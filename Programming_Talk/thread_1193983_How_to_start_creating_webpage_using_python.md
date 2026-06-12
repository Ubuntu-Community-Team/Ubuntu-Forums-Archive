---
title: "How to start creating webpage using python?"
date: 2009-06-22
forum: Programming Talk
---

### Post by superpink99 on 2009-06-22
OBJECTIVE: create a simple website using python.
PROBLEM: i don't know where and what to start with. can anyone suggest the best and simplest way to start?
OPERATING SYSTEM: Ubuntu Jackalope

thanks.............

---

### Post by era86 on 2009-06-22
Look into Django.  It is a development framework based in Python.  I've used it, works well.  You can find plenty of tutorials online.  If you run into anything you can't find, let me know and I'll help.

---

### Post by -grubby on 2009-06-22
> **era86 said:**
> look into django.  It is a development framework based in python.  I've used it, works well.  You can find plenty of tutorials online.  If you run into anything you can't find, let me know and i'll help.

+1

---

### Post by markux^Hs on 2009-06-22
[http://wiki.python.org/moin/WebProgramming](http://wiki.python.org/moin/WebProgramming)

---

### Post by scottuss on 2009-06-22
If you want something simple, try cherrypy

---

### Post by loell on 2009-06-22
I also lean on cherrypy while also suggesting that you look into [plone]("http://plone.org/").

---

### Post by curvedinfinity on 2009-06-22
Meh, frameworks take a long time to learn. Here's your get-started-in-30-seconds tutorial:

Install everything:

```

sudo apt-get install libapache2-mod-python
sudo a2enmod python

```

Edit this file:

```

gksudo gedit /etc/apache2/sites-available/default

```

Insert this after <Directory /var/www/>:
```

AddHandler mod_python .py
PythonHandler mod_python.publisher
PythonDebug On

```

Reload apache:
```

sudo /etc/init.d/apache2 restart

```

Insure apache is running by going here: [http://localhost](http://localhost)

Make your first web-app:
```

gksudo gedit /var/www/hello.py

```

Enter this:
```

def index(request):
	return "Hello World!"

```

Visit [http://localhost/hello.py](http://localhost/hello.py) to see your running app.

More:
[http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch](http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch)

---

### Post by loell on 2009-06-22
bah.. apache is bloated and overkill :tongue:

here's a  get-started in 10 seconds.

1. install **cherrypy**

```
sudo apt-get install cherrypy3
```

2. save this as **helloworld.py**

```


import cherrypy

class HelloWorld(object):
    def index(self):
        return "Hello World!"
    index.exposed = True

cherrypy.quickstart(HelloWorld())



```
3. then run helloworld.py!  :D

4. oops forgot, then go to **[http://localhost:8080](http://localhost:8080)**

---

### Post by jetole on 2012-09-12
> **era86 said:**
> Look into Django.  It is a development framework based in Python.  I've used it, works well.  You can find plenty of tutorials online.  If you run into anything you can't find, let me know and I'll help.

+1 for Django though if you want something simpler and more straight to the point then maybe Flask would be up your ally but, for a quality site which takes a little more effort, then I think Django is the way to go and it's still easy. It will prevent errors you didn't know existed and implement efficiency in wonderful ways you weren't expecting.

P.S. It comes with a development server to run on demand whenever you want to test your site. It's not the server you want to use for the whole world when you publish but it makes dev and debugging a lot simpler.

---

### Post by Toz on 2012-09-12
Old thread.
Closed.

---

