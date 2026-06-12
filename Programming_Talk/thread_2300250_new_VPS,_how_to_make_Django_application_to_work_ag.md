---
title: "new VPS, how to make Django application to work again?"
date: 2015-10-24
forum: Programming Talk
---

### Post by asteriks on 2015-10-24
Hi, 

one man developed python/django app for me and now when I changed VPS, I must install everything from zero, debian 8. 

I have backup, tar files and mysql file, but it is not enough just to untar files and to import DB with phpmyadmin. I need to install django, python, virtualenv, tmux, and above all, he placed it in /root/env and /root/mercury folders (mercury contain static files), I am afraid if I put it in /var/www/html I will damage paths in django application. I don't know how to find path in so many files.

1) can I install it in other place or it must be /root/env & /root/mercury? 
here is screenshot when I unzip/untar env archive, you can see paths, should I use it (just to untar it, maybe it will be overwritten when I use requirements.txt?) or I must reinstall all of it (from ENV)? [http://oi60.tinypic.com/312fpuf.jpg](http://oi60.tinypic.com/312fpuf.jpg)

2) how to connect apache/debian with python/django? I think he used python 3.4, mod wsgi or something else? I have no idea how to write path looking like this: 
python-path=${SRV}/www:${SRV}/src:${SRV}/venv/dev/lib/python2.7/site-packages \
I suppose site-packages is place of django

3) I would like to separate this application from the system, should I install python3/django/mysql inside of virtualenv and not inside of the whole debian system?

4) I found some requirements.txt file. I think: pip install -R requirements.txt (inside of requirements, it is written: Django==1.8.3, mysqlclient==1.3.6, pycrypto==2.6.1), it looks it is not debian mysql-client than pip mysql?

my small test I tried to do:
I installed python3.4 and python3-pip but when I logged in virtualenv, I got error in executing requirements.txt:

```
Could not fetch URL pypi.python.org/simple/Django/1.8.3: 404 Client Error: Not Found Will skip URL pypi.python.org/simple/Django/1.8.3 when looking for download links for Django==1.8.3 (from -r requirements.txt (line 1))

OSError: mysql_config not found
```

screenshot from pip.log: [http://oi57.tinypic.com/15xag7r.jpg](http://oi57.tinypic.com/15xag7r.jpg)

---

### Post by asteriks on 2015-10-24
problem solved, I installed this time gcc inside of virtualenv, and miracle happened, it works.
there was error for pycrypto and other things like mysql:

> Failed building wheel for pycrypto
unable to execute 'x86_64-linux-gnu-gcc': No such file or directory
error: command 'x86_64-linux-gnu-gcc' failed with exit status 1

but after I installed gcc, it works, just it catches itself for python2 and I thini developer used python3, I will check tomorrow if all of it works.

still my questions are valid, how to deploy application/server considering I need to connect it with apache.

---

