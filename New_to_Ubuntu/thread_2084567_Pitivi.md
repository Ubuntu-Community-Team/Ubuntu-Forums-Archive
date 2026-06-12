---
title: "Pitivi"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by enperera on 2012-11-15
Hi, I want to install Pitivi in my PC, so I downloaded from 

[http://ftp.gnome.org/pub/GNOME/sources/pitivi/0.15/](http://ftp.gnome.org/pub/GNOME/sources/pitivi/0.15/)

When I read the file Install, it says I should type from a terminal './configure', then 'make' and last 'make install', so, when I run './configure' then I get many lines checking on several things and at the end say:

checking for intltool >= 0.35.0... ./configure: line 5334: intltool-update: command not found
 found configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.

so I went to Synaptics, I reinstall intltool with the version 0.35.0 but it doesn't work, when I run ./configure again I get the same message

Please helpme!

---

### Post by Bucky Ball on 2012-11-15
Easier to install Pitivi from the repos through Synaptics or Software Centre unless you have a specific reason to 'roll your own'. That way it will drag in what it needs on install. ;)

---

### Post by sffvba[e0rt on 2012-11-15
Why don't you install it from the Ubuntu repo's?

Quickest way to do it would be to type the following in Terminal:

```
sudo apt-get install pitivi
```

Enter your password and away you go...


404

*edit - Ninja'd >.>*

---

### Post by enperera on 2012-11-16
Thank you very much, I follow your advise and it works fine...cheers!

---

### Post by enperera on 2012-11-16
Thank you, you all guys, I follow the sudo instruction and everything is fine now, without complications...hog!

---

### Post by sffvba[e0rt on 2012-11-16
> **enperera said:**
> Thank you, you all guys, I follow the sudo instruction and everything is fine now, without complications...hog!

Awesome. In future check out synaptic or the software center and you should find the software you want to use :)

I have marked your thread as solved (something you can do in future by editing the opening post).


404

---

### Post by Bucky Ball on 2012-11-16
... or just hit 'Thread Tools' at top right and 'Mark Thread as Solved'. 

Glad it's sorted. ;)

---

