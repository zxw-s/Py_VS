# Visual Studio 开发 Python

> **Python工作负载（官方Python开发）**，完整调试、虚拟环境、pip、项目管理；
> 
> 不要混淆：VSCode是轻量编辑器，Visual Studio是完整IDE。

## 前置安装

打开 VS安装器 → 修改 → **工作负载** → 勾选【**Python开发**】，安装。

- 同时本机需要安装Python解释器（3.10以上推荐）
- VS可以自动检测本机Python，也可以新建虚拟环境。

## 创建Python项目

1. 创建新项目 → 搜索 `Python` → **Python应用程序**
2. 生成默认 `PythonApplication1.py`

```python
print("VS Python中文测试：你好！")
```

## 中文乱码（Windows高频坑）

### 现象：编辑器中文正常，运行print输出乱码

两种方案：

### 方案1：项目环境变量（推荐）

右键Python项目 → **属性 → 调试 → 环境变量** 添加：

```plaintext
PYTHONIOENCODING=utf-8
```

保存，重新运行。

### 方案2：代码顶部兜底

```python
# -*- coding:utf-8 -*-
import sys
sys.stdout.reconfigure(encoding="utf-8")

print("VS Python中文测试：你好！")
s = input("请输入：")
print(s)
```

> 文件编码：右下角看编码，源码保存为 **UTF‑8**。

## VS虚拟环境管理

1. 右侧【解决方案资源管理器】→ 右键【Python环境】→ **添加虚拟环境**
2. 创建 `venv`，VS自动激活。
3. pip安装库：右键虚拟环境 → **管理Python包**，图形界面搜索安装；
   也可以使用VS内置终端：

```bash
pip install requests
pip freeze > requirements.txt
```

## 运行与调试

- `Ctrl+F5`：不调试运行
- `F5`：断点调试，支持变量监视、条件断点。
- 控制台模式：项目属性 → 调试，选择使用外部控制台窗口。

## 项目文件结构

```plaintext
VsPythonDemo/
├─ VsPythonDemo.sln       # VS解决方案
├─ VsPythonDemo.pyproj    # python项目文件
├─ main.py
└─ venv/                  # 虚拟环境（不要提交git）
```

## 常用操作

1. 切换解释器：右侧Python环境下拉，切换全局/venv虚拟环境
2. requirements.txt：右键 → **安装requirements.txt**，一键批量装依赖
3. 代码格式化：安装`autopep8`，工具 → 选项→配置格式化。

## 常见坑

1. **项目路径、文件夹不要中文**，虚拟环境容易创建失败。
2. 乱码核心：环境变量 `PYTHONIOENCODING=utf‑8`。
3. 解释器选错：导入模块报红，重新切换Python环境。
4. `.pyproj`项目文件，不要手动乱改。

# VS和VSCode Python对比

|      | Visual Studio                  | VSCode                     |
| ---- | ------------------------------ | -------------------------- |
| 安装   | 需要安装Python工作负载                 | 只装Python扩展                 |
| 虚拟环境 | 图形化管理                          | 命令行手动创建venv                |
| 配置文件 | `.pyproj`解决方案                  | `.vscode/launch.json .env` |
| 乱码解决 | 项目属性添加`PYTHONIOENCODING=utf‑8` | 项目`.env`文件                 |
| 适合场景 | 大项目、教学、windows完整IDE            | 轻量刷题，快速脚本                  |

> 小提示：如果你只是写小脚本刷题，VSCode更轻便；做课程大作业，Visual Studio图形界面更友好。

---

接下来可以走两个方向：

1. 做一套多语言的练习题巩固
2. 整理一份开发环境踩坑清单（环境变量、PATH、各种报错）
