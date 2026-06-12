---
title: "[help]Install QT4 in Ubuntu"
date: 2007-06-27
forum: Programming Talk
---

### Post by wth_china on 2007-06-27
I want to learn QT4 in Ubuntu,I have installed it in WindowsXP,but it has some problem in linux.Can't make the program.
I want to use synaptic to install the QT4,QT assistant,QT designer,can you tell me how to do.

---

### Post by yabbadabbadont on 2007-06-27
Search for libqt4 and install whichever of the packages that show up you want.  Probably libqt4-dev will get you most of what you want.  You could also install kdevelop and that should pull in pretty much everything you would need.

---

### Post by wth_china on 2007-06-27
you mean install Kdevelop will install all package QT4 need?

---

### Post by samjh on 2007-06-27
No, KDevelop will install QT3.

Install QT4 as Yabbadabbadont has posted.  But you can install KDevelop as a C++ IDE, if you want.

---

### Post by wth_china on 2007-06-27
OK,I will use Kdevelop.

---

### Post by wyrmfire on 2007-12-30
Another good one for an IDE (with a more streamlined approach) is QDevelop.

Is my editor of choice and its designed specifically for Qt4.

Regards,


Wyrmfire

P.S: I know this is an old thread but at the same time is still providing some further information. 

:popcorn:

---

### Post by TheRoot on 2008-03-12
I did this:

```
apt-get install libqt4-core libqt4-dev libqt4-gui 
qt4-dev-tools
```

---

### Post by LaRoza on 2008-03-12
Necromancy is not really condoned by the forum :)

---

