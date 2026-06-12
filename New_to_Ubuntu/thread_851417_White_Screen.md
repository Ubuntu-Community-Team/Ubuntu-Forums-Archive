---
title: "White Screen"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by hotcarl on 2008-07-06
I was trying to get WOW to work on my laptop through wine and I kept getting some kind of issue with my video card that was causing my computer to crash.  I'll admit I probably should have done a little more research into what I was trying to do and I jumped in head first into some wiki page that I  blindly followed.  The problem is now after I login I get a completely white screen.  I tried removing the beryl compiz application but it said that "beryl could not be found".  here is a link to the wiki page i stupidly followed:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29)


If anyone could help me out It would be appreciated.  I have tried searching for help already, but to no avail.

---

### Post by ChameleonDave on 2008-07-07
Before making any changes to /etc/X11/xorg.conf, you ought to make a backup of it.  I expect that an error in that file is what is screwing you up.

Have a look in /etc/X11/ and see if there are any automatic backups in there.

---

### Post by alienexplorers on 2008-07-07
look for files such as xorg.conf~ or xorg.~....

---

