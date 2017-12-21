Python 独立运行环境
-------------
> 在开发Python应用程序的时候，系统当前的Python往往只有一个版本：3.X / 2.X。所有第三方的包都会被pip安装到Python的site-packages目录下。
如果我们要同时开发多个应用程序，那这些应用程序都会共用一个Python，就是安装在系统的Python。如果应用A需要jinja 2.7，而应用B需要jinja 2.6怎么办？
这种情况下，每个应用可能需要各自拥有一套“独立”的Python运行环境。virtualenv就是用来为一个应用创建一套“隔离”的Python运行环境。
[廖雪峰Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001432712108300322c61f256c74803b43bfd65c6f8d0d0000)


#### 1. virtualenv
```bash
# 安装
pip install virtualenv


# 初始化
cd your-project/

virtualenv .venv

source .venv/bin/avtive


# 此时的安装就依赖就在你的虚拟环境里面
pip install flask

# 运行之前你也需要进入该环境
source .venv/bin/active

python app.py


# 通过安装路径可以指定Python版本
virtualenv -p /usr/bin/python3 .venv


# 退出该环境
deactivate

```


#### 2. pipenv
```bash
# 安装
pip install pipenv


# 初始化
cd your-project/

# pipenv install --two 安装Python 2.X 虚拟环境
# pipenv install --three 同样需要你本机安装了Python 3

pipenv install


# 安装依赖
pipenv install flask


# 运行你的代码
pipenv run flask

# 或者进入虚拟环境
pipenv shell

pipenv run python manage.py


# 设置shell别名
alias prp="pipenv run python"

prp manage.py


```

使用 pipenv 会自动在当前目录下创建Pipfile & Pipfile.lock
里面有项目依赖等信息, clone or copy到新机器上时, 只要对方安装了 pipenv， 即可通过 `pipenv install` 初始化虚拟环境并安装好依赖
