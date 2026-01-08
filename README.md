# **个人Git 标准操作手册（SSH 版）**

### 零、标准操作模板

####     新项目（本地 → GitHub）

```bash
git init
git add .
git commit -m "init"
git remote add origin git@github.com:you/repo.git
git push -u origin master
```

---

####     老项目（日常更新）

```bash
git add .
git commit -m "xxx"
git push
```

### **一、Git / GitHub 的核心认知**

1️⃣ **版本控制的最小单位是 commit，不是 push**

2️⃣ **git push 只是把 commit 同步到 GitHub**

3️⃣ **origin 是“每个仓库内部的远端别名”，不是全局的**

4️⃣ **. 表示“当前目录”**（操作系统级概念）

5️⃣ **SSH 配好后，以后 push / pull 都不需要密码**

### **二、Git 的三大区域**

**工作区 (Working Directory)**
   **|**
   **| git add**
   **v**
**暂存区 (Staging Area)**
   **|**
   **| git commit**
   **v**
**本地仓库 (Local Repository)**
   **|**
   **| git push**
   **v**
**远端仓库 (GitHub)**

### **三、最基础但最重要的命令**

##### **1️⃣ 我现在在哪？**

##### `pwd`

- 含义：Print Working Directory
- 显示当前所在的完整路径

##### **2️⃣ 当前目录是不是 Git 仓库？**

`ls -a`
如果看到：
`.git`
👉 当前目录是 Git 仓库

如果看不到 .git：

👉 所有 git add / git commit 都会失败

##### **3️⃣ 查看当前 Git 状态（必查）**

`git status`

- 红色文件：还没有 add
- 绿色文件：已 add，等待 commit
- 推荐习惯：**每次 add / commit 前都先看一眼**

### 四、`.` 和 `..` 的含义（命令行通用基础）

##### 1️⃣ 基本含义

| 符号 | 含义       |
| ---- | ---------- |
| `.`  | 当前目录   |
| `..` | 上一级目录 |

**说明：**

- 这是 **Unix / Linux / macOS** 的系统级约定  
- **不是 Git 特有规则**  
- Git、Shell、编辑器都会使用这套语义  

---

##### 2️⃣ 常见实际用法

```bash
git add .        # 当前目录及其子目录的所有改动
ls .             # 查看当前目录
ls ..            # 查看上一级目录
cd ..            # 返回上一级目录
./a.out          # 运行当前目录下的可执行文件
```

### **五、最常用 Git 提交流程（SSH 已配置）**

##### **✅ 日常开发 / 作业提交（90% 使用场景）**

```bash
git add .
git commit -m "feat: xxx"
git push
```

##### **✅ 第一次 push（必须使用-u)** 

```bash
git push -u origin master
# 或
git push -u origin main
```

##### `-u` 的真实含义

- `-u` = `--set-upstream`
- 含义是：
  把当前本地分支，绑定到指定的远端分支

##### Git 会记录：

`本地 master  ↔  远端 origin/master`

以后即可直接使用：

```bash
git push
git pull
```

### **六、版本控制核心命令（查看历史与版本）**

1️⃣ 查看提交历史

```bash
git log
```

精简版（推荐）：

```bash
git log --oneline
```

示例：

```bash
a4d2cc8 A2_submitted
9f21b31 fix: timer bug
3c81a7e init
```

说明：

- 每一行 = 一个版本
- 左边是 commit hash（版本 ID）
- 右边是 commit message

---

2️⃣ 查看某一次提交的内容

```bash
git show
git show <commit_id>
```

---

3️⃣ 查看单个文件的历史

```bash
git log 文件名
git blame 文件名
```
