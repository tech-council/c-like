MaxWit零基础入门系列

# 系统管理

- [1. 了解三大操作系统（桌面级）](#1-%e4%ba%86%e8%a7%a3%e4%b8%89%e5%a4%a7%e6%93%8d%e4%bd%9c%e7%b3%bb%e7%bb%9f%e6%a1%8c%e9%9d%a2%e7%ba%a7)
- [2. 系统配置](#2-%e7%b3%bb%e7%bb%9f%e9%85%8d%e7%bd%ae)
- [3. Shell](#3-shell)
- [4. 包管理 (CLI版App Store)](#4-%e5%8c%85%e7%ae%a1%e7%90%86-cli%e7%89%88app-store)
- [5. 虚拟机](#5-%e8%99%9a%e6%8b%9f%e6%9c%ba)
- [6. Linux](#6-linux)
- [7. 开发环境](#7-%e5%bc%80%e5%8f%91%e7%8e%af%e5%a2%83)

## 1. 了解三大操作系统（桌面级）

No. | Item | macOS | Linux | Windows | Comments
----|------|-------|-------|---------|---------
1 | 病毒少 | 是 | 是 | 否 | 
2 | 稳定不易降速 | 是 | 是 | 否 | 
3 | 开发工具支持 | 优 | 优 | 有待完善 | 另见专门文档
4 | Unix兼容 | 是 | 是 | 否 | WSL一定程度上弥补了这一不足
5 | 开源项目 | 较多 | 最多 | 较少 | 
6 | 办公软件 | 多 | 较少 | 最多，很完善 | 
7 | 游戏数量 | 中 | 少 | 多 | macOS的游戏数量正在快速增加

## 2. 系统配置
一、请在Windows或macOS系统（根据你的实际情况而定）上执行如下操作，根据系统提示信息了解计算机的硬件配置
<div style="float: left;width: 45%;">
<h5 align = "center">macOS</h5>

```
Apple菜单 ➤ About This Mac ➤ Overview ➤ System Report
```
</div>

<div style="float: left;width: 53%;margin-left:2%">
<h5 align = "center">Windows</h5>

```
右键点击Windows菜单 ➤ 选择“Device Manager”
```
</div>

然后将了解到的硬件配置信息填入表1-1中“当前配置”一栏：

组件  |  推荐配置 |  当前配置 
--- | ----- | ------
计算机型号  | （无要求） | （PC组装机写主板型号） 
CPU  |  Intel i5+ | （比如i9-9900k） 
RAM  |  8G+ | （比如32G DDR4）
HDD  |  固态240G+ |  
GPU  | （无要求） |  
NIC  | （无要求） | （填写有线网卡型号）
Wi-Fi  | （无要求） |  


二、在Windows或macOS系统上执行如下操作，然后截图（其中Mac电脑的序列号可隐藏）：

<div style="float: left;width: 48%;">
    <h5 align = "center">macOS</h5>
    Apple菜单  ➤  About  This  Mac
    <img src="img/pasted-image-small-18.png" alt="mac version">
    <center>图1-1</center>
</div>

<div style="float: left;width: 48%;margin-left:4%">
    <h5 align = "center">Windows</h5>
    右键点击Windows菜单  ➤  Run  ➤  输入“msinfo32”，回车
    <img src="img/pasted-image-small-15.png" alt="win version">
    <center>图1-2</center>
</div>

MaxWit预科阶段的系统架构图1-3所示，其中OS推荐使用macOS 10.13以上版本或Win10 Pro最新版。接下来的预科课程会陆续给讲解该系统的安装及使用。

![avatar](img/work-env.png)

图1-3 MaxWit工作环境

## 3. Shell
——从另一视角理解Windows/macOS
传统的人机交互界面主要有两种：GUI（图形界面）和CLI（命令行）。大家都对GUI比较熟悉，但专业人员还需要掌握CLI。Windows 10的默认CLI为PowerShell，macOS的默认CLI为Bash，分别按如下方式打开——

<div style="float: left;width: 48%;">
    <h5 align = "center">macOS</h5>

```
Command(⌘) + Space，输入terminal，回车
```
</div>

<div style="float: left;width: 48%;margin-left:4%">
    <h5 align = "center">Windows</h5>

```
 右键点击Windows菜单，选择“Windows PowerShell” 
```
</div>

方便起见，建议把终端固定在任务栏上，以后直接点击任务栏上的终端图标即可（特别是对于Windows PowerShell，右键点击可以选择多种模式，后面会用到）：
<div style="float: left;width: 45%;">
<h5 align = "center">macOS</h5>

```
右键点击Dock上的Terminal图标，选择“Options” ➤ Keep in Dock
```
</div>

<div style="float: left;width: 53%;margin-left:2%">
<h5 align = "center">Windows</h5>

```
右键点击任务栏上的PowerShell图标，选择“Pin to taskbar”
```
</div>

然后，在Shell终端中练习下面表2-1中的命令。建议多练习几遍，直到熟练为止。结束后回复邮件，将最后一步生成的hist.txt文件的内容复制到邮件正文中。

**重要提示：**
1. 输入命令（包括参数）时请注意空格。
2. Tab键！Tab键！Tab键！重要的事情说三遍:-) 输入命令或参数时尽可能尝试Tab键补全，工作更加快速、准确。
3. 操作期间同时打开图形窗口，直观感受命令的运行情况。具体做法：Windows上运行“explorer .”，macOS上运行“open .”，输入命令的同时请注意GUI窗口中的变化。


N | 命令 | 简要说明 | 使用示例
--|----|------|-----
1 | echo | 输出，类似于C语言中的printf | 输出常量：`echo "Hello, World!"`<br/>输出变量：`echo "my home is $HOME"`<br/>重定向到文件：`echo "print('my home is $HOME')" > hello.sh`
2 | man | 查看命令用法 (必要时可按q退出) | `man mkdir` (可知mkdir命令的最简用法是后面接一个字符串)
3 | mkdir | 创建目录 | `mkdir demo`
4 | ls | 列出目录内容 | 列出当前目录的内容：`ls`<br/>列出当前目录下所有Shell脚本：`ls *.sh`
5 | pwd | 查看当前路径 | `pwd`
6 | cd | 切换路径 | 切换到根目录：`cd /`<br/>切换到用户的home目录：`cd $HOME`
7 | cat | 输出文件内容 | `cat hello.sh`
8 | mv | 移动或改名 | `mv hello.sh hello.py`<br/>`mv demo demo1`
9 | cp | 复制文件或目录 | 复制文件：`cp hello.py max.py`<br/>复制目录：`cp -r demo1 demo2`
10 | rm | 删除文件或目录 | 删除文件：`rm max.py`<br/>删除目录：`rm -r demo2`
11 | history | 显示历史命令 | `history`

表2-1

## 4. 包管理 (CLI版App Store)

choco和brew分别是Windows和macOS平台上非常有用的第三方软件包管理工具，相当与CLI（命令行）版的App Store。和普通App一样，Shell也有两种运行模式：普通用户模式和特权用户模式。特权用户拥有操作系统的一切权限，Windows上对应Administrator，macOS和其他Unix-like系统（比如Linux、Android等）对应root。
<!-- 为了方便起见，我们约定之后的Shell命令示例中，“$”表示普通用户模式，“#”表示特权用户模式。 -->
<div style="float: left;width: 45%;">
<h5 align = "center">macOS</h5>

打开Terminal，然后执行如下命令安装brew，安装过程中会提示输入sudo密码（即系统登录密码）。brew不需要在特权用户模式下安装。
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Howmbrew/install/master/install)"
```
</div>

<div style="float: left;width: 53%;margin-left:2%">
<h5 align = "center">Windows</h5>

用Admin模式打开PowerShell（右键点击任务栏上的PowerShell，选择“Run As Ademinstrator”），然后执行如下命令安装choco:
```shell
$ Set-ExecutionPolicy Bypass -Scope Unrestricted -Force
$ iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
```
</div>

安装完成后输入`choco --version` (on Windows) 或 `brew --version` (on macOS) 确认，看到版本号说明已经安装成功。现在可以尝试使用choco install或brew install命令来安装软件了。下面是需要安装的部分软件：

N | App | Windows系统 | macOS系统
--|-----|-----------|--------
1 | Python3 | $ choco install -y python3 | $ brew install python3
2 | Visual Studio Code | $ choco install -y vscode | $ brew cask install visual-studio-code
3 | VirtualBox | $ choco install -y virtualbox | $ brew cask install virtualbox
4 | Vagrant | $ choco install -y vagrant | $ brew cask install vagrant
5 | Vagrant Manager | $ choco install -y vagrant-manager | $ brew cask install vagrant-manager
6 | VMWare | $ choco install -y vmwareworkstation | $ brew cask install vmware-fusion
7 | SSH Client | $ choco install -y mobaxterm | $ brew cask install iterm2

表3-1

下面的命令将输出已安装的App列表（包括版本号），安装完成表3-1中的App后输入命令确认已经装情况
<div style="float: left;width: 45%;">
<h5 align = "center">macOS</h5>

```
$ brew list -version
```
</div>

<div style="float: left;width: 53%;margin-left:2%">
<h5 align = "center">Windows</h5>

```
$ choco list -l
```
</div>

**Tips：**
1. Windows上需要在Admin模式下运行choco命令。
2. 安装软件的过程中如果遇到网速不稳等问题，可改用迅雷下载，然后普通方式安装。
3. 如果不确定App的名字，可以使用choco/brew search命令搜索和确认（支持模糊匹配）。

## 5. 虚拟机

**1. 创建Vagrant目录**
```shell
$ mkdir -p ~/vagrant/archlinux
$ cd ~/vagrant/archlinux
```

**2. 下载Vagrant box**（可选，网络环境好的同学请跳过这一步，直接做第3步！）
常规方式创建Vagrant VM（即第3步）需要从网上下载image，网速慢的话下载所需时间可能比较久，有的国外站点甚至可能无法直接访，所以我们事先把box image上传到了QQ群文件。下载完成后运行如下命令：
```shell
$ vagrant box add archlinux/archlinux ~/Downloads/archlinux.box（假定下载位置是Downloads目录）
```

**3. 创建Linux VM**
执行如下命令初始化一台虚拟机
```shell
$ vagrant init archlinux/archlinux
```

虚拟机上的OS被称为Guest OS（比如这里的Linux），物理机上的OS被称为Host OS（比如这里的Windows/macOS）。

**4. 启动VM、登录Linux**
```shell
$ vagrant up
$ vagrant ssh（通过SSH方式登录Linux）
```

**5. 体验Linux**
在Linux系统上做些简单操作，比如查看Linux内核信息：
```shell
$ uname -s -r（该命令在Linux上执行）
```

**6. 退出Linux、关闭VM**
```shell
$ exit（该命令在Linux上执行）
$ vagrant halt（该命令在Windows/macOS上执行）
```

**7. SSH远程登录**
第4步中我们使用vagrant ssh登录虚拟机，我们还可以使用普通ssh方式登录Linux，方式如下：
```shell
$ cd ~/vagrant/archlinux
$ vagrant up
$ vagrant ssh-config --host archlinux-workstation > ~/.ssh/config
```
其中，“archlinux-workstation”是我们给Linux虚拟机起的名字。上面的命令用于生成客户端配置文件，现在我们可以在任意路径通过执行”ssh archlinux-workstation”登录Linux了。不过在Windows系统上因为重定向的encoding问题导致ssh命令执行失败，我们需要转化config文件的编码。以notepad++为例演示如何完成这一操作：
```
# choco install -y notepadplusplus
$ notepad++ ~/.ssh/config (务必使用Tab补全)
```
用notepad++打开config文件后，点击“Encoding”菜单 ➤ “Convert to ANSI”，然后保存退出。Linux

## 6. Linux

**1. 启动Linux VM，并登陆系统**
```shell
$ cd ~/vagrant/archlinux
$ vagrant up
$ vagrant ssh（登录Linux）
```

**2. Linux Shell**
之前我们在Windows/macOS系统上执行过表2-1中的命令，现在请在Linux系统上重新执行一遍。

**3. Linux包管理**

N | Operation | Ubuntu<br/>(apt) | CentOS<br/>(yum) | ArchLinux<br/>pacman | General<br/>snap
--|-----------|--------|--------|-----------|-------
1 | 安装 | install | install | -S | install
2 | 删除 | remove  | remove  | 
3 | 查询 | search  | search  | 
4 | 升级 | upgrade | update  | 

表 5-1

## 7. 开发环境
**第一步，安装python for vscode插件，整合vscode + python**
```shell
$ code --install-extension ms-python.python
```

**第二步，启动vscode，编写一个“Hello, World!”测试代码**
```shell
$ mkdir demo
$ cd demo
$ code .
```

**第三步，运行你的代码**。点击“New File”图标（见下图）➤ 创建一个文件，比如`hello.py` ➤ 输入测试代码，比如`print("Hello, World!")` ➤ Ctrl+F5（或者点击“Debug”菜单 ➤ “Start Without Debugging”）执行

![avatar](img/pasted-image-small-21.png)

图6-1
