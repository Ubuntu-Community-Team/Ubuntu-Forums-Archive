---
title: "[Ask] Why Skype doesnt available at USC?"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by RotiHangus HC on 2013-07-11
Hye all,
I'm new to ubuntu (currently using Ubuntu 13.04 "Raring Ringtail" 

I dont even know why **skype** doesnt available at ubuntu software center. 
Is there any other ways to get it?

---

### Post by newbie-user on 2013-07-11
Skype is not in the default repository for Ubuntu. You have to enable the partner repository in order to get it.
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

To do this in the GUI, go to the Ubuntu Software Center, then Click on Edit > Software Sources. Click on the "Other Software" tab, click on "Add...", then type 
```
deb http://archive.ubuntu.com/ubuntu raring partner
```
Then click "Add Source". Once it updates the sources, you should be able to find Skype in the software center.

---

### Post by RotiHangus HC on 2013-07-13
> **newbie-user said:**
> Skype is not in the default repository for Ubuntu. You have to enable the partner repository in order to get it.
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

To do this in the GUI, go to the Ubuntu Software Center, then Click on Edit > Software Sources. Click on the "Other Software" tab, click on "Add...", then type 
```
deb http://archive.ubuntu.com/ubuntu raring partner
```
Then click "Add Source". Once it updates the sources, you should be able to find Skype in the software center.

Thanks mate! 
Its worked for me. :D

---

