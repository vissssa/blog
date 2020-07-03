---
title: python展示调用栈
tags:
  - python
categories:
  - python
  - deep
date: 2020-07-03
description: 图形化展示函数调用链
---
如下一个简单的flask项目，在view函数中加入这个展示栈的函数，就可以自动打开一个图形化的对于栈的展示
<!-- more -->
```python
from flask import Flask

from analysis import show_stack

app = Flask(__name__)


@app.route('/')
def index():
    file = show_stack()
    print(file)
    return {'data': file}


if __name__ == '__main__':
    app.run(debug=True)

```

浏览器输入[http://127.0.0.1:5000](http://127.0.0.1:5000)就可以看到效果。
![stack.png](https://i.loli.net/2020/07/03/K1zqjI87bFOlTUi.png)

`analysis`文件的代码在我的[github](https://github.com/vissssa/awesome-pythonlib/blob/master/analysis.py#L13)仓库中
