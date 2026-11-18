# 剑心（jianxin）

把卡住你的生意问题丢进来，它不急着回答，先拆掉你的问题：一刀点破你真正卡在哪、你在躲什么，再陪你找到下一步。

> 用户：为什么我跑通了却放不大？做上门宠物洗护一年多了，月入一万八，每天跑六七单，排得满满的。最早是帮邻居家洗狗做起来的。
>
> 剑心：你问的是怎么放大，可你每天六七单已经排满了。一万八不是市场给你的上限，是你一个人能跑出来的上限。
>
> ……
>
> 你真正该问的是：哪几件事，不该是我来做？

背后是张柯Ker 的判断：困住你的不是问题，是问法。

## 安装

把这句话发给你的 agent（豆包电脑版的「工作」、Claude Code、Codex、Grok、Trae 等能在电脑上执行命令的都可以）：

```text
帮我安装 Github 上 zhangke668/jianxin
```

豆包电脑版里可以说：「豆包你好，帮我安装 Github 上 zhangke668/jianxin」。装好后新开一个对话就能用。

## 怎么用

- `/jianxin 为什么我跑通了却放不大？`：直接把卡住你的生意问题和情况说出来。
- 也可以直接说「剑心」「我卡住了」「帮我拆一下这个问题」。
- 它每次先给一个判断，判断缺一块关键事实时才问你一个问题。你接住了判断，它再给你下一步。
- 同一类事反复卡你，说「练剑」：它把拆出来的真问题建一个档案，每轮补一份材料、出一道你没见过的题，连着两题判对就算练成。下次说「继续上次」接着练。档案存在你电脑「文档」目录下的 `剑心档案` 文件夹里。
- 只输入 `/jianxin`，它会告诉你能做什么。

## 给 AI agent 的安装说明

用户让你安装这个仓库时，按下面的顺序试，前一步成功就不用做后面的。下文的 `~` 指用户主目录，Windows 上是 `C:\Users\<用户名>`。

### 1. 用 skills 安装器（推荐，需要 Node.js）

```bash
npx -y skills add zhangke668/jianxin -g -y
```

它会把 skill 装到 `~/.agents/skills/jianxin/`，并自动链接到本机已有的 Claude Code、Grok、Trae 等 agent 目录。输出里如果有 `PromptScript does not support global skill installation`，可以忽略，不影响其他 agent。

### 2. 没有 Node.js，或安装器失败：直接克隆

把仓库克隆到你自己读取 skill 的目录，文件夹名必须是 `jianxin`，`SKILL.md` 直接放在里面，不要多套一层：

| Agent | 目录 |
|-------|------|
| Claude Code | `~/.claude/skills/jianxin/` |
| Grok | `~/.grok/skills/jianxin/` |
| Trae / Trae CN | `~/.trae/skills/jianxin/` 或 `~/.trae-cn/skills/jianxin/` |
| Codex、豆包，以及其他读通用目录的 agent | `~/.agents/skills/jianxin/` |

```bash
git clone --depth 1 https://github.com/zhangke668/jianxin.git ~/.claude/skills/jianxin
```

连不上 GitHub 时，告诉用户网络不通，请用户自己下载 <https://github.com/zhangke668/jianxin/archive/refs/heads/main.zip> 发给你，再解压到上表的目录，并把解压出来的 `jianxin-main` 改名为 `jianxin`。

### 3. 你不能在电脑上执行命令

比如手机 App 或网页聊天。读取 <https://raw.githubusercontent.com/zhangke668/jianxin/main/SKILL.md>，以及它提到的 `references/` 里的文件，在当前对话里按它的方法回答用户，并告诉用户：这样只在本次对话有效，想长期用，需要装到能执行命令的 agent 里；「练剑」的档案这时存不下来。

### 装完以后

1. 确认 `jianxin/SKILL.md` 存在，开头写着 `name: jianxin`，旁边有 `references/` 文件夹。
2. 告诉用户：新开一个对话（或重启 agent）后，输入 `/jianxin` 加一个卡住你的生意问题试试。

## 更新和卸载

- 更新：`npx -y skills update jianxin -g -y`；手动克隆的，在 `jianxin` 文件夹里执行 `git pull`。
- 卸载：`npx -y skills remove jianxin -g -y`；手动装的，直接删掉 `jianxin` 文件夹。
