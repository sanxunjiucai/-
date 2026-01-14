# 运营任务卡片样式指南

## 1. 任务信息卡片 (Task Info Card)

### 样式描述
任务卡片采用 **磨砂玻璃 (Glassmorphism)** 风格，结合 **微渐变** 区分任务类型，整体视觉轻盈且具有层级感。

*   **容器 (Container)**:
    *   **背景**: 高通透度的白色背景 (`rgba(255, 255, 255, 0.7)`) 叠加 `20px` 的背景模糊 (`backdrop-filter`)。
    *   **边框**: 细微的白色半透明边框，增强玻璃质感。
    *   **阴影**: 柔和的深色阴影 (`rgba(30, 41, 59, 0.05)`) 增加悬浮感。
    *   **圆角**: `24px` 大圆角，视觉更亲和。
    *   **间距**: 内边距 `20px`，内容布局紧凑。

*   **视觉标识 (Visual Identity)**:
    *   **顶部微渐变**: 卡片顶部设有 `80px` 高度的微渐变遮罩，颜色根据任务类型（创收/随访/宣教）变化，透明度为 `0.6`，不遮挡内容。
    *   **图标**: 统一使用 `1.5px` 线条粗细的 SVG 线性图标。

*   **排版 (Typography)**:
    *   **标题**: `18px` 加粗 (`700`)，深色 (`#0f172a`)，紧凑行高。
    *   **信息行**: `12px` 灰色 (`#64748b`)，图文混排。
    *   **关键数据**: 底部展示 `22px` 特粗 (`800`) 数字，统一深色 (`#1e293b`)，无彩色干扰。

*   **功能区 (Functional Areas)**:
    *   **洞察框 (Insight Box)**: 半透明白色背景容器，用于展示关键提示信息。
    *   **进度条**: 统一使用深靛蓝 (`#4f46e5`) 填充。

### 核心代码
```css
/* 卡片容器 */
.task-row-inner {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  min-height: 280px;
  padding: 20px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.8);
  box-shadow: 0 8px 32px rgba(30, 41, 59, 0.05);
  overflow: hidden;
}

/* 顶部微渐变 (以创收类为例) */
.task-type-revenue .task-row-inner::after {
  content: "";
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 80px;
  background: linear-gradient(to bottom, rgba(255, 237, 213, 0.6) 0%, rgba(255, 255, 255, 0) 100%);
  pointer-events: none;
  z-index: 0;
}

/* 标题样式 */
.task-title {
  font-size: 18px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 6px;
  line-height: 1.4;
  letter-spacing: -0.01em;
}

/* 洞察框 */
.insight-box {
  background: rgba(255, 255, 255, 0.5);
  border-radius: 12px;
  padding: 10px 12px;
  margin-bottom: 12px;
  border: 1px solid rgba(255, 255, 255, 0.6);
  font-size: 12px;
  color: #475569;
  z-index: 2;
}
```

---

## 2. 创建任务卡片按钮 (Create Task Card Button)

### 默认样式代码 (Default Style)
这是一个伪装成卡片的按钮，用于触发新建任务操作。采用虚线边框和浅色背景，与实体任务卡片形成视觉区分。

```css
.task-card-new {
  /* 布局与尺寸 */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 280px;
  padding: 24px;
  border-radius: 24px;
  
  /* 视觉样式 */
  background: rgba(248, 250, 252, 0.5);
  border: 2px dashed rgba(148, 163, 184, 0.4);
  cursor: pointer;
  text-align: center;
}

/* 内部图标容器 */
.new-task-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  margin-bottom: 12px;
  border-radius: 50%;
  background: #4f46e5;
  color: white;
  box-shadow: 0 4px 12px rgba(79, 70, 229, 0.3);
}

/* 文本样式 */
.new-task-text {
  margin-bottom: 4px;
  font-size: 16px;
  font-weight: 600;
  color: #1e293b;
}

.new-task-sub {
  font-size: 12px;
  color: #64748b;
}
```
