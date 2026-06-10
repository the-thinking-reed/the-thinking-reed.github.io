# the-thinking-reed.github.io

5311 lab homepage

# 实验室学术主页维护说明

本说明面向实验室成员，用于维护实验室学术主页中的两个核心文件：`about.md` 和 `navigation.yml`。其中，`about.md` 负责首页正文内容，`navigation.yml` 负责顶部导航栏。一般来说，**添加新闻、论文、成员、资源、个人主页链接、GitHub 链接、ORCID 链接等，主要修改 `about.md`即可；**只有新增、删除或调整顶部导航菜单时，才需要修改 `navigation.yml`。

## 修改前注意事项

- 不要随意删除 `about.md` 文件开头的 `--- ... ---` 区域。它是页面的 Front Matter，用于配置首页路径、标题、作者栏等。
- 顶部导航能否正确跳转，取决于 `navigation.yml` 中的 `url` 是否与 `about.md` 中的锚点 `id` 一致。
- 图片、图标建议统一放在 `images/` 目录，例如 `images/github-logo.svg`、`images/ORCID-iD_icon_vector.svg`、`images/TCCN-szy.png`。
- PDF 建议统一放在 `pdf/` 目录，并使用 `/pdf/文件名.pdf` 的形式引用。
- 文件名尽量使用英文、数字、短横线或下划线，避免空格和中文，例如 `TCOM-2026-ljq.png`。
- `navigation.yml` 是 YAML 文件，缩进只能用空格，不能用 Tab。

## 首页结构

`about.md` 当前主要由以下部分组成：

| 页面部分 | 对应内容 | 维护建议 |
| ---- | ---- | ---- |
| Front Matter | `permalink`、`title`、`author_profile` 等页面配置 | 通常不要修改 |
| About Us | 实验室简介、导师简介、研究方向 | 修改实验室整体介绍时编辑 |
| News | 最新新闻、获奖、项目进展、成员加入 | 新消息放在最上面 |
| Publications | 论文列表和论文卡片 | 新论文按时间倒序添加 |
| Resources | 代码仓库、学习资料、项目资源 | 可复用论文卡片样式 |
| Members | 实验室成员及个人链接 | 添加成员、GitHub、ORCID、主页等 |
| Join Us | 招生与联系方式 | 修改招生说明和联系邮箱 |

## 锚点与导航

首页中的每个导航目标一般由两部分组成：

一是在 `about.md` 中添加锚点：

```html
<span class='anchor' id='-publications'></span>

# 📝 Publications
```

二是在 `navigation.yml` 中添加对应导航：

```yml
main:
  - title: "Publications"
    url: "/#-publications"
```

这里的关键是：`url` 中 `#` 后面的内容必须和 `id` 完全一致。例如：

| 页面部分 | `about.md` 中的锚点 | `navigation.yml` 中的链接 |
| ---- | ---- | ---- |
| About Us | `id='about-us'` | `url: "/#about-us"` |
| News | 建议使用 `id='-news'` | `url: "/#-news"` |
| Publications | `id='-publications'` | `url: "/#-publications"` |
| Resources | `id='-resources'` | `url: "/#-resources"` |
| Members | `id='-members'` | `url: "/#-members"` |
| Join Us | `id='-join-us'` | `url: "/#-join-us"` |

> 注意：当前文件中 News 部分的锚点写成了 `id='-xl'`，而 `navigation.yml` 中 News 的链接是 `url: "/#-news"`。这会导致顶部导航点击 News 时无法准确跳转。建议把 `about.md` 中 News 前面的锚点改为：

```html
<span class='anchor' id='-news'></span>

# 🔥 News
```

## 添加新导航栏目

如果想新增一个栏目，例如 `Projects`，需要同时改两个文件。

在 `about.md` 中添加：

```html
<span class='anchor' id='-projects'></span>

# 🚀 Projects

这里写项目介绍、项目列表或项目链接。
```

在 `navigation.yml` 中添加：

```yml
  - title: "Projects"
    url: "/#-projects"
```

完整示例：

```yml
main:
  - title: "About Us"
    url: "/#about-us"

  - title: "News"
    url: "/#-news"

  - title: "Projects"
    url: "/#-projects"

  - title: "Publications"
    url: "/#-publications"
```

## 修改实验室介绍

实验室介绍主要位于 `about.md` 的 About Us 部分。可以直接修改普通 Markdown 文本。

普通链接推荐使用 Markdown 写法：

```md
[[Google Scholar]](https://scholar.google.com/citations?user=xxxx)
```

研究方向可以使用列表：

```md
- **AI Agent** — 打造能自主决策的智能体，也尝试用生成式 AI 做点有趣的事
- **时序预测与数据压缩** — 用更少的比特描述世界，让预测更准、传输更快
- **网络信息论** — 探索多终端通信网络的极限
- **信息年龄（Age of Information）** — 优化实时系统中的更新策略与调度机制
```

## 添加 News

News 建议按时间倒序排列，最新的放在最上面。

模板：

```md
# 🔥 News
- *2026.06*, 🎉 论文 “论文标题” 被 *会议/期刊名称* 接收。
- *2026.02*, 🎉🎉 Welcome **成员姓名** join us as a PhD student.
- *2025.10*, 获得 某某比赛 `三等奖`。
```

写法建议：

- 时间统一使用 `*YYYY.MM*`，例如 `*2026.06*`。
- 重要结果可以用反引号突出，例如 `` `Best Paper Award` ``。
- 英文成员加入消息建议统一大小写，例如 `PhD student`，不要混用 `phd`、`Phd.`、`PhD.`。

## 添加成员

成员列表位于 `Members` 部分。

如果需要添加个人链接，可以用两种方式：普通 Markdown 链接或图标链接。

### 添加普通个人链接

普通链接最容易维护，适合不需要图标的情况：

```md
- Jiaqi Li (PhD) [[GitHub]](https://github.com/Li-Q-keep) [[ORCID]](https://orcid.org/0000-0002-2771-9344) [[Homepage]](https://example.com)
```

推荐链接类型：

| 链接类型 | 推荐显示文字 | 示例 |
| ---- | ---- | ---- |
| GitHub | `[[GitHub]](...)` | `https://github.com/用户名` |
| ORCID | `[[ORCID]](...)` | `https://orcid.org/0000-0000-0000-0000` |
| Google Scholar | `[[Google Scholar]](...)` | `https://scholar.google.com/citations?user=xxxx` |
| 个人主页 | `[[Homepage]](...)` | `https://个人主页地址` |
| 邮箱 | `[[Email]](mailto:邮箱地址)` | `mailto:name@example.com` |

### 添加带图标的个人链接

如果希望像当前成员信息中那样显示 ORCID 图标和 GitHub 图标，可以使用 HTML 的 `<a>` 和 `<img>`。

示例：

```html
<a href="点击后跳转的目标链接（GitHub、ORCID 或主页链接）" aria-label="访问说明"><img src="images/图片文件名.svg" width="18pt" alt="图片无法显示时的替代文字"/> 链接文字 </a>

<a href="https://github.com/Li-Q-keep" aria-label="View GitHub profile - Li-Q-keep"><img class="svg" src="images/github-logo.svg" width="18pt" alt="GitHub"/> Li-Q-keep </a>
```

### 添加自定义图标链接

如果想添加个人主页、Google Scholar、ResearchGate、LinkedIn、知乎、Bilibili 等自定义图标链接，步骤如下。

先把图标文件放入 `images/` 目录，例如：`images/google-scholar.svg`

然后在成员信息中添加：

```html
<a href="https://example.com" aria-label="View personal homepage"><img src="images/homepage.svg" width="18pt" alt="Homepage"/> Homepage </a>
```

## 添加论文

论文主要添加在 `Publications` 部分。当前页面中有两种写法：论文卡片和普通列表。

### 论文卡片

论文卡片适合展示代表性论文。它包含一个小图、一个会议或期刊标签，以及论文信息。

```html
<div class='paper-box'><div class='paper-box-image'><div><div class="badge">VENUE YEAR</div><img src='images/PAPER_IMAGE.png' alt="paper thumbnail" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

- `A. Author`, B. Author, C. Author, "Paper Title," in *Journal or Conference Name*, vol. xx, no. xx, pp. xx-xx, YEAR, doi: xx.xxxx/xxxxx.
[[IEEE Xplore]](https://ieeexplore.ieee.org/xxxx) [[PDF]](/pdf/paper.pdf) [[Code]](https://github.com/username/repo)

</div>
</div>
```

需要修改的地方：

| 位置 | 应填写内容 | 示例 |
| ---- | ---- | ---- |
| `VENUE YEAR` | 期刊或会议简称加年份 | `TCCN 2026`、`ICASSP 2026` |
| `images/PAPER_IMAGE.png` | 论文缩略图路径 | `images/TCOM-2026-ljq.png` |
| `Paper Title` | 论文标题 | `The Age of Incorrect Information ...` |
| `Journal or Conference Name` | 期刊或会议名称 | `*IEEE Transactions on Communications*` |
| `IEEE Xplore` | 官方页面链接 | `https://ieeexplore.ieee.org/document/xxxx` |
| `PDF`（optional） | 本地 PDF 或外部 PDF | `/pdf/paper-name.pdf` |
| `Code`（optional） | 代码仓库链接 | `https://github.com/用户名/仓库名` |

推荐规范：

- 新论文放在 `Publications` 最前面，保持时间倒序。
- 实验室成员姓名可以用反引号突出，例如 `` `J. Li` ``。
- 期刊和会议名称用斜体，例如 `*IEEE Transactions on Communications*`。
- 如果暂时没有 PDF 或代码链接，可以先不写对应链接。
- 缩略图建议宽高比例统一（**推荐横向图**），避免页面卡片高度差异过大。

### 普通论文列表

如果论文不需要图片，可以使用普通列表，维护成本更低。

示例：

```md
- `J. Li`, H. Xu, Y. Xu, X. Zhao, T. Guo and X. Ling, "The Age of Incorrect Information for Multi-User Link Scheduling Over Fading Channels," ICC 2025 - *IEEE International Conference on Communications*, Montreal, QC, Canada, 2025, pp. 2144-2149, doi: 10.1109/ICC52391.2025.11161794. [[IEEE Xplore]](https://ieeexplore.ieee.org/document/xxxx)
```

如果某条内容暂时不想显示，建议用 HTML 注释隐藏，而不是用删除线：

```html
<!--
- 暂时不展示的论文条目。
-->
```

## 添加 Resources

`Resources` 部分当前复用了论文卡片的样式，可以展示代码仓库、学习资料或开源项目。模板同`Publications`

> 建议：
>
> - 如果是代码仓库，优先给出 GitHub 链接。
> - 如果是课程、教程、数据集，可以增加 `[[Docs]](...)`、`[[Dataset]](...)`、`[[Project Page]](...)`。
> - 资源标题尽量简短，说明这个资源主要解决什么问题。

##  Join Us修改

`Join Us` 部分适合写招生方向、实验室风格、联系邮箱等。

## 常见链接写法

| 目标 | 推荐写法 |
| ---- | ---- |
| 普通网页 | `[[网页]](https://example.com)` |
| GitHub 仓库 | `[[GitHub]](https://github.com/username/repo)` |
| IEEE Xplore | `[[IEEE Xplore]](https://ieeexplore.ieee.org/document/xxxx)` |
| DOI | `[[DOI]](https://doi.org/10.xxxx/xxxxx)` |
| 本地 PDF | `[[PDF]](/pdf/paper.pdf)` |
| 邮箱 | `[[Email]](mailto:name@example.com)` |
| 个人主页 | `[[Homepage]](https://example.com)` |

## 文件架构简要说明

```text
acad-homepage.github.io/
├── _config.yml              # 全站基础配置：标题、作者、头像、邮箱、GitHub、ORCID、Google Scholar 等
├── _pages/
│   └── about.md             # 主页正文内容：简介、新闻、论文、成员、资源等
├── _data/
│   └── navigation.yml        # 顶部导航栏配置
├── images/                  # 头像、论文配图、图标、favicon 等图片资源
├── assets/                  # CSS、JS 等前端资源
├── _includes/               # 页面组件模板，一般不改
├── _layouts/                # 页面布局模板，一般不改
├── _sass/                   # 样式源码，一般不改
├── google_scholar_crawler/  # Google Scholar 引用统计脚本，一般不改
├── .github/workflows/       # GitHub Actions 自动化配置
├── docs/                    # 项目文档
├── Gemfile                  # Ruby/Jekyll 依赖
└── run_server.sh            # 本地预览脚本
```

