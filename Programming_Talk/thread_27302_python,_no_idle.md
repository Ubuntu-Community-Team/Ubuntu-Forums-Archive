---
title: "python, no idle"
date: 2005-04-15
forum: Programming Talk
---

### Post by lmellen on 2005-04-15
:?Does anybody know what needs to be installed for the python idle? I have python, no idle!
                 Thanks -- Larry :)

---

### Post by jdonnell on 2005-04-15
I just looked and idle doesn't appear to be on my system.

Why not use gedit instead or kate if your on kubuntu. Both of these have more features than idle and you can use them for other programming/editing.

---

### Post by dataw0lf on 2005-04-15
sudo apt-get install idle-python2.4

gedit and kate are for the birds.  (g)vim is where it's at.

---

### Post by lmellen on 2005-04-15
Thanks DatawOlf, that worked -- Larry  :)

---

### Post by jdonnell on 2005-04-15
[QUOTE=dataw0lf]sudo apt-get install idle-python2.4
[/quote]
Strange, on warty I did an 
apt-cache search idle 
and didn't see that package.

> 
gedit and kate are for the birds.  (g)vim is where it's at.

I presonally use a mix of kate and gvim. I use kate for my heavy coding and gvim for light things. The projects in kate are very convenient, I love the little dots it uses to show tabs (i do a lot of python), and I hate not being able to ctrl-c and ctrl-v for copy and paste in gvim. I also have an eye disease and reading the small text in gvim can be hard sometimes. Is there an easy way to change the font size? I look but it wasn't quickly apparent. Basically, you can tell that vim wasn't designed for gui use and it can be frustrating.

---

### Post by maubp on 2005-11-07
[QUOTE=dataw0lf]sudo apt-get install idle-python2.4[/QUOTE]
Cheers :)

That just did the trick on my Breezy Badger installation (which was upgraded from Hoary).  I had just given up after searching the installed files and turned to google...

It didn't occur to me that IDLE wouldn't be part of the standard python install.  Its showing up on the programming languages section of the "start menu" too, as expected.

There was a brief hickup with python-rpy-doc, but uninstalling that allowed idle-python2.4 to install without error.

---

