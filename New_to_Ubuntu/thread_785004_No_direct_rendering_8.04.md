---
title: "No direct rendering 8.04"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Loves_Unicorns on 2008-05-07
Hi, first post.
I just installed Ubuntu 8.04. Everything good so far. I did install the ATI drivers from Envy. I can enable desktop effects.  However
```

michelle@michelle-desktop:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
michelle@michelle-desktop:~$ 

```
I had figured that if I could enable desktop effects that I was good on direct rendering, but I guess that is not the case. Any help would be much appreicated.

---

### Post by Loves_Unicorns on 2008-05-07
Is it possilbe to do this w/o re-installing the drivers ? I had the same problem as in another post where my monitor was out of range. I had to call someone who did the fix X thing because the reconfigue didnt work. When they did the fix X would it have taken the drivers off ?

---

### Post by revilodraw on 2008-05-30
i have the same problem - can anyone help us?

---

### Post by linux4life88 on 2008-10-11
I'm having the same problem. I was wondering if anyone has found any fixes yet. I have an ATI Xpress 1150 graphics card. I get horrible frame rates in games (<5).

---

### Post by markbuntu on 2008-10-11
There are a lot of problems with envy and the drivers from ati. Envy seems to misinstall them more often than not and installs the 8.6 driver which has a lot of bugs and no support for many ati cards/chips.
The best way to install the latest ati proprietary fglrx driver 8.9 is to follow this guide here, use method 2, folow the guide very carefully, expecially if you are using 64 bit Hardy. Do not install these drivers if you are using Intrepid 8.10:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

