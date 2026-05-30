# 贡献指南

感谢你对 Vanceling 项目的关注！本指南将帮助你了解如何参与项目的开发和改进。

---

## 📋 目录

1. [开发环境设置](#开发环境设置)
2. [工作流程](#工作流程)
3. [代码规范](#代码规范)
4. [提交规范](#提交规范)
5. [文档规范](#文档规范)
6. [常见问题](#常见问题)

---

## 🛠️ 开发环境设置

### 前置条件

- Git 2.30+
- 代码编辑器（推荐 VS Code）
- 浏览器（Chrome/Safari/Firefox 最新版）

### 项目特定工具

#### Agent Skills 开发
- Python 3.9+
- FFmpeg（用于音频处理）
- MLX-Whisper（用于音频转写）

```bash
# 安装 FFmpeg
# macOS
brew install ffmpeg

# 安装 Python 依赖
pip install mlx-whisper PyPDF2 lark-oapi
```

#### 音乐播客 & 小游戏
- 无需特殊依赖
- 仅需现代浏览器和文本编辑器

### 本地开发

```bash
# 克隆仓库
git clone https://github.com/vanbuster/vanceling-projects.git
cd vanceling-projects

# 创建特性分支
git checkout -b feature/your-feature-name
```

---

## 🔄 工作流程

### 1. 提出想法或报告问题

#### 报告 Bug
- 使用 GitHub Issues 创建问题
- 标题简洁明了，如：「[Skills] 转写精度问题」
- 详细描述：现象、复现步骤、期望行为、实际行为

#### 建议新功能
- 使用 GitHub Discussions 讨论新想法
- 先检查是否有类似建议
- 说明使用场景和预期效果

#### 提问或讨论
- 使用 GitHub Discussions
- 在 "Ideas" 或 "Q&A" 分类下发起讨论

### 2. 创建分支

按照类型创建分支名称：

```bash
# 新功能
git checkout -b feature/interview-coach-optimization

# Bug 修复
git checkout -b fix/transcribe-encoding-issue

# 文档更新
git checkout -b docs/update-readme

# 性能优化
git checkout -b perf/optimize-audio-processing
```

### 3. 本地开发

```bash
# 做出更改
# ...

# 测试你的更改
# - 对于 Skills：运行测试脚本
# - 对于 Web 项目：在浏览器中打开 HTML 文件

# 查看改动
git status
git diff
```

### 4. 提交更改

遵循 [提交规范](#提交规范)：

```bash
# 暂存文件
git add .

# 提交更改
git commit -m "feat: 添加新的转写优化策略"

# 推送到远程
git push origin feature/interview-coach-optimization
```

### 5. 创建 Pull Request

1. 在 GitHub 上打开 PR
2. 按照 PR 模板填写信息
3. 链接相关的 Issues
4. 等待代码审查
5. 根据反馈进行调整
6. 合并到 main 分支

---

## 📐 代码规范

### Python

```python
# 风格：PEP 8
# 工具：autopep8, pylint

# 示例：良好的 Python 代码
def transcribe_audio(audio_path: str, language: str = "zh") -> dict:
    """
    将音频文件转写为文本。
    
    Args:
        audio_path: 音频文件路径
        language: 语言代码，默认为中文
        
    Returns:
        包含转写文本和时间戳的字典
    """
    # 实现
    pass
```

### JavaScript/HTML/CSS

```javascript
// 遵循 ES6+ 标准
// 使用有意义的变量名
// 添加注释说明复杂逻辑

// 示例：良好的 JavaScript 代码
class MusicPlayer {
    constructor(containerId) {
        this.container = document.getElementById(containerId);
        this.audioContext = new (window.AudioContext || window.webkitAudioContext)();
        this.init();
    }
    
    init() {
        // 初始化播放器
    }
    
    play() {
        // 播放逻辑
    }
}
```

```css
/* 使用 BEM 命名规范 */
/* 支持主题变量 */

:root {
    --primary-color: #333;
    --background-color: #fff;
}

.music-player {
    /* ... */
}

.music-player__button {
    /* 元素 */
}

.music-player__button--playing {
    /* 修饰符 */
}
```

### 通用规范

- **缩进**：2 个空格（HTML/CSS/JS）或 4 个空格（Python）
- **行长**：最多 100 字符
- **命名**：使用英文，避免拼音和缩写
- **注释**：代码要清晰，注释说明「为什么」而不是「是什么」
- **删除代码**：不要注释出代码，直接删除或使用 Git 历史

---

## 📝 提交规范

采用 Conventional Commits 标准：

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type（必需）

- `feat`: 新增功能
- `fix`: Bug 修复
- `docs`: 文档更新
- `style`: 格式调整（不改变代码逻辑）
- `refactor`: 代码重构
- `perf`: 性能优化
- `test`: 测试相关
- `chore`: 构建、依赖、工具等

### Scope（可选但推荐）

标识改动涉及的模块：

```
feat(interview-coach): 添加音频预处理功能
fix(music-blog): 修复 Safari 兼容性问题
docs(readme): 更新快速开始指南
```

### Subject（必需）

- 使用祈使句：「add」而不是「added」
- 首字母小写
- 末尾不加句号
- 限制在 50 字符以内

### Body（可选）

- 说明是什么、为什么、怎么做
- 每行 72 字符以内
- 分离多个逻辑块

### Footer（可选）

```
Closes #123
Related to #456
Breaking change: 描述破坏性变更
```

### 示例

```
feat(skills): 集成 MLX-Whisper 实现离线转写

添加离线语音转写能力，支持中文和英文。
- 集成 MLX-Whisper 库
- 支持 MP3/WAV 等常见格式
- 生成时间戳转写结果

Closes #89
```

---

## 📚 文档规范

### Markdown 格式

```markdown
# 一级标题（文件标题）

## 二级标题（主要章节）

### 三级标题（子章节）

#### 四级标题（小节）

正文段落。使用清晰的语言，避免冗余。

**粗体** 用于强调重要概念。
*斜体* 用于引用或示例。
`代码` 用于代码片段。

### 代码块

\`\`\`python
def example():
    pass
\`\`\`

### 列表

- 项目 1
- 项目 2
  - 子项目 2.1
  - 子项目 2.2

### 表格

| 列 1 | 列 2 |
|------|------|
| 内容 | 内容 |

### 链接和图片

[链接文本](https://example.com)
![图片描述](path/to/image.png)
```

### 文档模板

#### README.md

```markdown
# 项目名称

> 简短的一句话描述

## 功能

- 功能 1
- 功能 2

## 快速开始

步骤 1
步骤 2

## 文档

- [完整指南](./docs/guide.md)
- [API 参考](./docs/api.md)

## 贡献

欢迎提交 PR！

## 许可证

MIT
```

#### SKILL.md

```markdown
---
name: skill-name
description: 简短描述
when_to_use: |
  使用场景列表
---

# 技能名称

## 角色定义

## 工作流程

## 输入输出

## 约束

## 迭代记录
```

### 文档检查清单

- [ ] 标题层级合理
- [ ] 代码示例正确且可运行
- [ ] 链接有效
- [ ] 未使用过时的信息
- [ ] 拼写和语法检查
- [ ] 包含使用示例

---

## ❓ 常见问题

### 如何建立本地开发环境？

参考 [开发环境设置](#开发环境设置) 部分。

### 我如何知道我的更改是否正确？

- **Agent Skills**：运行测试脚本，检查输出
- **Web 项目**：在浏览器中打开文件，测试功能
- **文档**：检查格式和拼写

### PR 被拒绝了怎么办？

- 阅读审查意见并理解反馈
- 做出相应的修改
- 在评论中说明你的更改
- 重新推送

### 如何报告安全问题？

不要在 GitHub Issues 中报告安全问题。

请直接通过邮件联系维护者。

### 我可以修改其他贡献者的代码吗？

- 小的拼写或格式错误：可以直接修改
- 逻辑或功能改动：先在 PR 中讨论

### 项目的路线图是什么？

查看 [GitHub Projects](https://github.com/vanbuster/vanceling-projects/projects) 了解计划的功能和改进。

---

## 🎯 审查流程

### 代码审查标准

1. **功能完整性**：是否实现了预期的功能？
2. **代码质量**：是否遵循项目的代码规范？
3. **测试覆盖**：是否有充分的测试？
4. **文档**：是否更新了相关文档？
5. **性能**：是否考虑了性能影响？
6. **安全性**：是否存在安全隐患？

### 审查反馈

- 建设性的批评和建议
- 说明改进的理由
- 提供改进的示例代码

### 合并条件

- ✅ 至少 1 名维护者审查并批准
- ✅ 所有自动检查通过
- ✅ 分支最新并不存在冲突
- ✅ 所有讨论都已解决

---

## 🙏 致谢

感谢所有为 Vanceling 做出贡献的人！

你的名字将被添加到 [CONTRIBUTORS.md](./CONTRIBUTORS.md) 文件中。

---

**最后更新**: 2026-05-30

有问题？在 GitHub Issues 中提问或通过邮件联系维护者。
