---
name: visual-note-generator
description: Turn arbitrary Chinese or multilingual source content into a concise Chinese sketchnote-style knowledge-card image. Use when the user asks to make notes, articles, course content, Apple Notes, transcripts, screenshots, documents, or pasted text into a Chinese knowledge card, reading-note infographic, social-media saveable image, or when they request coordinate-based local text corrections to a generated card.
---

# Visual Note Generator

把任意内容提炼为主题统一、中文清晰、适合收藏传播的竖版手绘知识卡片。优先做 MVP：一张图讲清一条主线，不堆砌全部信息。

## 工作流

1. 获取内容。
   - 用户粘贴文字时直接使用。
   - 用户指定本地备忘录时，使用电脑操作技能只读打开并提取相关笔记。
   - 用户提供图片、网页或文件时先读取内容；网页引用需要核对时再搜索。
2. 提炼主线。
   - 用一句话回答“这张图只讲什么”。
   - 合并重复信息，删除案例枝节、跨主题知识和无法支撑主线的内容。
   - 默认保留：一个标题、一句副标题、一条核心公式或结论、3～5 个同类知识点、一个可复制模板或行动步骤、一句收束金句。
   - 信息过多时主动删减，不缩小字体硬塞。
3. 先写文字底稿。
   - 全部使用中文；必要英文术语保留并紧跟中文解释。
   - 每个知识点标题控制在 2～6 个汉字，正文尽量不超过两行。
   - 用户原文与准确性优先，不虚构课程结论、引用或数据。
   - 生成前逐字检查底稿，锁定最终文案。
4. 生成卡片。
   - 必须调用图片生成技能和内置图片生成工具，不用 HTML、SVG 或代码绘图替代。
   - 默认使用 `assets/default-style-reference.png` 作为风格参考；用户提供新参考图时，以用户参考图为主。
   - 使用 `references/style-and-prompt.md` 的版式、配色、提示词模板和质量要求。
   - 默认竖版 3:4、高清、单页完整输出。
5. 检查与迭代。
   - 检查主题是否单一、中文是否清晰、是否有错别字、遗漏、重复、越界或字号过小。
   - 首次结果有文字错误时，使用原生成图作为编辑目标，只做一次针对性局部修改。
   - 用户用坐标指出修改位置时，严格只改指定区域，并在提示词中锁定其他区域不变。
6. 保存交付。
   - 将最终成品复制到当前项目的 `outputs/`；若无项目输出目录，则保存到当前工作区。
   - 使用不覆盖旧版本的名称，例如 `主题-知识卡片-v2.png`。
   - 最终回复提供可点击文件链接，并简述本次提炼掉了哪些非同类内容。

## 默认内容结构

按内容选择最少且够用的结构，不要为了填满版面添加知识：

- 方法型：核心公式 → 3～5 个步骤 → 万能模板 → 总结。
- 课程型：课程主题 → 核心观点 → 关键方法 → 行动清单 → 金句。
- 概念型：是什么 → 为什么 → 如何做 → 常见误区 → 一句话记忆。
- 对比型：共同维度 → A/B 对照 → 选择建议 → 判断公式。

## 局部修改规则

- 将坐标视为定位提示，并结合可见标题确认目标区域。
- 精确引用“原文字”和“替换文字”。
- 明确要求保持尺寸、比例、背景、图标、边框、纹理和其他文字不变。
- 替换文字较长时仅在原卡片内自然换行，不扩张到相邻区域。
- 保存为新版本，不覆盖原图。
