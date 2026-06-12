---
title: "Feisty EasyEclipse"
date: 2007-04-30
forum: Programming Talk
---

### Post by thefool808 on 2007-04-30
anybody get easyeclipse to work in feisty?  i've had no luck.

with easyeclipse-lamp-1.2.1.3, when running it from the command line inside the easyeclipse folder i get the not very imformative response:

$ ./eclipse 
bash: ./eclipse: No such file or directory

(i switched sh to point to bash instead of dash btw)

I've also renamed the easyeclipse jre folder so that it uses the jre5 installed on my system.

Eclipse runs fine (well except for the fact that it never runs as smooth as easyeclipse and the plugins often crash).

---

### Post by thefool808 on 2007-05-01
aptana didnt work either... same problem.  I'm sad about not having a useful error message :cry:

---

### Post by thefool808 on 2007-05-01
alrighty...

so i've made myself happy now by using the ubuntu repository eclipse and just replacing my ~/.eclipse/.../plugins folder with the plugins folder from easyeclipse-lamp.  works even though easyeclipse-lamp is at 3.2.1 and the ubuntu package is at 3.2.2

8-)

---

