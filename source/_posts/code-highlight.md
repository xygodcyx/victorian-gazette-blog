---
title: 代码高亮与汇编之美
date: 2026-05-05
updated: 2026-05-05
categories: 技术考古
tags: [代码高亮, 汇编, TypeScript, 使用指南]
description: 维多利亚号外代码高亮系统的完整展示，涵盖多种编程语言、行号、复制按钮与羊皮纸底色。
---

{% paranote "summary" "本文展示代码高亮系统的各项功能——行号、语法着色、复制按钮以及移动端适配。示例代码涵盖汇编、TypeScript、Python 与 JSON。" %}

{% dropcap "本" %}刊的代码块以羊皮纸为底色、铜色细线为边框，四角饰以金色标记。行号列静默地列于左侧，代码则在右侧以等宽字体呈现。桌面端双列并排，移动端行号绝对定位，代码列可横向滚动。每个代码块右上角均有一个半透明的复制按钮，点击即可将代码复制至剪贴板。

{% endparanote %}

<!-- more -->

## 汇编语言

汇编是离机器最近的語言。以下是一段 x86 汇编，演示如何将数据移入寄存器与内存：

```asm
mov ax, 32h
mov bx, 1000h
mov ds, bx
mov [0], ax
add ax, 1
mov [1], ax
add ax, 1
mov [2], ax

mov ax, [0]
mov bx, [2]
mov cx, [1]
mov bx, [1]
mov cx, [2]
```

{% paranote "citation" "此段汇编代码参考了王爽《汇编语言》第3版的示例，略有改动。" "left" %}
{% endparanote %}

## TypeScript 类型定义

TypeScript 的联合类型与字面量类型非常适合描述具有多种变体的数据结构。以下示例定义了几何形状的类型：

```typescript
type Circle = {
  kind: 'circle'
  radius: number
}

type Square = {
  kind: 'square'
  sideLength: number
}

type Shape = Circle | Square

function area(shape: Shape): number {
  switch (shape.kind) {
    case 'circle':
      return Math.PI * shape.radius ** 2
    case 'square':
      return shape.sideLength ** 2
  }
}
```

## Python 文本处理

Python 简洁的语法使其成为处理文本的首选工具。以下代码统计了一段维多利亚时代文本中的词频：

```python
import re
from collections import Counter

text = """
The fog crept along the cobblestone streets,
wrapping the gas lamps in a yellow haze.
"""

words = re.findall(r'\b\w+\b', text.lower())
word_count = Counter(words)

for word, count in word_count.most_common(5):
    print(f"{word}: {count}")
```

## JSON 配置文件

本刊主题的配置文件以 JSON 格式存储，以下为侧边栏配置的简化示例：

```json
{
  "sidebar": {
    "bio": "千禧年幸存者 · 数字考古学家",
    "badge_text": "烛光排版认证",
    "links": {
      "老猫的静默花园": "https://example.com",
      "CD旋转岁月": "https://example.com"
    }
  },
  "fonts": [
    "Playfair Display",
    "Cormorant Garamond",
    "UnifrakturMaguntia"
  ]
}
```

{% paranote "editorial" "编者按：以上四种语言分别代表了底层硬件、类型系统、文本处理与数据配置四个领域。本刊的代码高亮配色经过精心调校——关键字为勃艮第红，字符串为深棕，注释为灰褐斜体，全以暖色调呈现。" %}
{% endparanote %}

## 移动端效果

在手机屏幕上，代码块的行号列会自动缩窄，代码字号适当减小，确保在小屏设备上依然可以舒适阅读。行号在极窄屏幕上会被隐藏，以最大化代码显示区域。
