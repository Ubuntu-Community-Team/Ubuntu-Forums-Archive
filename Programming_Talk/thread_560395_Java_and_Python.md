---
title: "Java and Python"
date: 2007-09-26
forum: Programming Talk
---

### Post by measekite on 2007-09-26
Java for sure and possibly Python:

I have been programming using VB,net going against SQL server.  Now I am gradually moving away from Windows.

To program in Java I need a complete IDE including the Java programming language and what ever goes with it.

What do I download.  I am looking at no cost.

Also what is net beans or Java beans?

I also would like to learn Python.  Is there an IDE for Python and what do I download for that?

---

### Post by pmasiar on 2007-09-26
Python is "batteries included" language, it includes also IDE (called IDLE), and couple other free IDEs are available, like Eric (yes, that [Eric Idle](http://en.wikipedia.org/wiki/Eric_Idle) from Monty Python), SPE (all can be installed by Synaptic) and many commercial with free subset, like WingIDE and Komodo. 

I prefer SPE. One of the reasons is that SPE is being developed primarily in ubuntu, Stani sometimes hangs around this forum and recommends to use version from CVS as most recent (but I use standard repository version).

And you can go by using just simple programmer's editor, like SciTE, which has syntax highlighting and other nice features, just set tabs to be converted to spaces - Python dislike mixing tabs and spaces, and such confusing source will generate warning in coming Py3K.

Also, I found Python many times more productive than Java, more fun to program in, and Python is becoming more widely accepted too.

What kind of applications do you plan to develop?

---

### Post by LaRoza on 2007-09-26
There is a sticky for Windows programmers coming to Linux. (+1 for Python though)

---

### Post by skeeterbug on 2007-09-26
Go with Python. You are coming from VB, so the syntax will be more natural for you. I am not sure if you have looked at anything in Java yet, but there is a LOT of configuration done using XML files. In Python, you can open your code in a lightweight editor if needed. Besides, Java is "Write once, debug everywhere". I wrote my website in Python on Windows, but the server is running Linux. There were no issues moving the code over.

---

### Post by Ramses de Norre on 2007-09-26
For java: I'd recommend you eclipse, I find it the best IDE I've worked with. You'll be best of installing it from [eclipse's home site](http://www.eclipse.org). You'll also need the java jdk which is in the repo.

Netbeans is another IDE which is used by many, I prefer eclipse but you might like netbeans better, only way to find out is to try them both ;)

JavaBeans are part of J2EE (java 2 enterprise edition), they are used in big, distributed apps and you'll meet them when needed, don't start using such things until you're experienced enough and you really need them.

---

### Post by CptPicard on 2007-09-26
> **Ramses de Norre said:**
> 
JavaBeans are part of J2EE (java 2 enterprise edition), they are used in big, distributed apps and you'll meet them when needed

Actually, [JavaBeans]("http://en.wikipedia.org/wiki/JavaBean") are nothing but Java objects that obey certain naming conventions with their method names, and in particular have getter and setter methods for their properties. Despite the hype, they're just a particular kind of POJO :)

---

### Post by Ramses de Norre on 2007-09-26
> **CptPicard said:**
> Actually, [JavaBeans]("http://en.wikipedia.org/wiki/JavaBean") are nothing but Java objects that obey certain naming conventions with their method names, and in particular have getter and setter methods for their properties. Despite the hype, they're just a particular kind of POJO :)

True, but you'll only use them (on purpose) in combination with frameworks which require JavaBean objects.

---

### Post by measekite on 2007-09-26
I have been developing client server concentrating mostly on front end in VB.net hitting SQL Server on the backend.

---

### Post by pmasiar on 2007-09-27
> **measekite said:**
> I have been developing client server concentrating mostly on front end in VB.net hitting SQL Server on the backend.

Python has two very nice web frameworks, Django and TurboGears. Looks like you will be better of with TurboGears, because you need only parts of it (and Django is rather monolithic), or just get SQLObject or SQLAlchemy ORM.

It would be interesting to reuse Turbogears (or it's meta-framework, Pylons) for client/server app framework, generating wxPython GUI instead of HTML for web, and it even may exist, but I do web apps so I don't follow C/S apps world anymore.

---

### Post by Kahai on 2007-09-27
I am currently learning Java it is the intro to prograaming at my university, so of course Java at first

but since my switch from windows (which has now been completed lol i hate VI$TA)   i havent been able to get the beanshell working, but alas, then i found python!

from what i have learned thus far in java, python is much easier to use, and get into, i use the pre-nstalled "terminal" python, im not picky lol my schools library has a Python ILDE which is nice but they is on windows lol

i havent gotten too far into the python tut provided through

```
help()
```

im not giving you the link lol find it yourself :)

as for an actual program in python, i just know the first one they give you
```
a,b=0,1
while b > 10:
      print b
      a,b=b,a+b
```
(note: the "spaces" are a tab)

---

### Post by Ramses de Norre on 2007-09-27
Beanshell can be installed as "bsh".

---

### Post by kknd on 2007-09-27
For Python, you can use eclipse + pydev (really good), or just gedit or geany if you want something lightweight. Add pygtk and glade if you want to do some productive GUI building.

For Java, I recommend NetBeans 6.0 (beta 1 right now). It's open-source, has a good editor (way better than nb 5.5) and a good GUI builder, for the Desktop guys =).

---

