---
title: "Can't play MP3 files on 8.04?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by giordun on 2008-05-04
I tried playing mp3 files on my computer but it don't work.

So I did a little search and I found out you do that restricted extras thing...

jdan@jdan-desktop:~$ sudo apt-get install ubuntu-restricted-extras 
[sudo] password for jdan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
jdan@jdan-desktop:~$ 

and it don't work...

:(

---

### Post by zaussome on 2008-05-04
z

---

### Post by giordun on 2008-05-04
What's this repositories enabled stuff? Yes I'm connected to the Internet.

---

### Post by zaussome on 2008-05-04
z

---

### Post by imasickboy on 2008-05-04
Open Synaptic, click settings, repositories, and be sure everything is checked. Then, reload, and you can install the package from there, or go back to a terminal and repeat your initial attempt.

---

### Post by SunnyRabbiera on 2008-05-04
right, also in synaptic make sure to under settings to check the second tab in (third-party software) and make sure everything is checked off there too.
synaptic is located under system, under administration just in case you get lost.
I know this sounds like a pain to do but its there because of the Ubuntu philosophy of not including proprietary formats out of the box.
but its easy to overcome.

---

### Post by giordun on 2008-05-04
Whoops I forgot to reload. :P

---

### Post by SunnyRabbiera on 2008-05-04
aye, its a simple mistake.
hey you are new, so expect to make mistakes... its how you learn :D

---

