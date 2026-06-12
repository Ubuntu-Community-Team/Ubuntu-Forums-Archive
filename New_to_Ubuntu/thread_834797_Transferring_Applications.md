---
title: "Transferring Applications"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by lizandeen on 2008-06-19
I have two hard drives in my computer, one ubuntu 8.04/windows and the other just ubuntu 8.04 and was wondering if there is an easy way to copy (transfer) all my Settings (fonts, sizing etc),Documents and, perhaps most importantly, all my Applications (with all their settings!) en masse from one ubuntu to the other ? Thanks in advance, lizandeen.

---

### Post by phidia on 2008-06-19
Take a look at [this]("http://ubuntuforums.org/showthread.php?t=613462&highlight=transfer+copy+settings")
and see if that works for you. You could also use dd to do this too see man dd.

---

### Post by mevets on 2008-06-19
to transfer your setting just copy your home folder. for applications thats harder. i would use something like APTonCD.

---

### Post by lizandeen on 2008-06-19
Thanks to both of you but niether solution seemed to work for me (though the QuickStart application should prove useful in the future!). Any more suggestions from anybody or this could turn out to be a very long and tedious transfer process!!

---

### Post by RequinB4 on 2008-06-19
> **lizandeen said:**
> Thanks to both of you but niether solution seemed to work for me (though the QuickStart application should prove useful in the future!). Any more suggestions from anybody or this could turn out to be a very long and tedious transfer process!!

You do realize that your application settings (including all your windows programs running in wine) are located in your /home, right? (Try opening nautilus to your /home and press control+h)  All you need to do is re-install the application and then put in your /home...

The only thing I can think this would be a problem for is applications that are a) not in the repositories AND b) you installed manually WITH root permissions that are c) NOT running in wine.

---

