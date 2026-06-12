---
title: "Unable to install Scrapy on Python 3.6.5"
date: 2018-10-15
forum: New to Ubuntu
---

### Post by pratap31 on 2018-10-15
[LIST]
[*]pip install lxml
[*]pip install parsel
[*]pip install w3lib
[*][B]pip install twisted(src/twisted/test/raiser.c:4:20: fatal error: Python.h: No such file or directory) and ([B]Failed building wheel for twisted
[/B]  Running setup.py clean for twisted
[B]Failed to build twisted
[/B])[/B]
[*]pip install cryptography
[*]pip install cryptography
[*]pip install pyOpenSSL
[/LIST]
and finally

[LIST]
[*]pip install scrapy,
[/LIST]

if i tried to use below scripts it installed 
**$ sudo apt-get install python-virtualenv**
**$ virtualenv my-fun-env**
**$ source my-fun-env/bin/activate**
**(my-fun-env)$ pip install twisted**

but installed in the path of [B]my-fun-env ( it is a virtual environment),

[/B]how can i install scrapy directly?,

Thanks in advance.

---

### Post by monkeybrain20122 on 2018-10-15
```
sudo pip3 install -U scrapy
```

---

