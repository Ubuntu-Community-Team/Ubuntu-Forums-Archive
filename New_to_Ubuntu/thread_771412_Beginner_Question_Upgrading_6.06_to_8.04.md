---
title: "Beginner Question: Upgrading 6.06 to 8.04"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by zaussome on 2008-04-27
z

---

### Post by zalberico on 2008-04-27
[http://ubuntuforums.org/showthread.php?t=766573](http://ubuntuforums.org/showthread.php?t=766573)

Same problem here, the guy suggests two different pages.

What it means when it is asking you to enable the dapper updates channel is basically that there are certain locations where new packages are pulled from and your version of ubuntu doesn't have the newest locations (doesn't know what website they are at) to get the new packages on file.  You need to add these internet locations for the upgrade to be able to proceed.  The two sites on the link should help you with that.  I have not looked very closely at them though, so if you need more help deciphering it just ask. :)

---

### Post by hums07 on 2008-04-27
It's about adding "dapper-updates ...." line in the file **/etc/apt/sources.list**. However, it will matter if you update using internet.

As you said your computer was not connected to the internet, so your best way is to upgrade using Alternate CD. You can download it [here]("http://www.ubuntu.com/getubuntu/download").

> Upgrading using the alternate CD/DVD
Use this method if the system being upgraded is not connected to the Internet.
1. Download and burn the alternate installation CD.
2. Insert it into your CD-ROM drive.
3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
4. Follow the on-screen instructions.

---

### Post by zalberico on 2008-04-27
Not sure exactly how new you are to gnu/linux, but to add the text to /etc/apt/sources.list as hums07 said you'd need to open the terminal and use a text editor to do that.

sudo nano /etc/apt/sources.list

---

### Post by zaussome on 2008-04-27
z

---

### Post by hums07 on 2008-04-27
There are 7 steps in the instruction. Where are you now?

---

### Post by zalberico on 2008-04-27
Press Alt-F2 and type gksu "update-manager -d" 

If it is already there you may already have the necessary updates.  I'd continue with step three (above)

---

### Post by zaussome on 2008-04-27
z

---

### Post by zaussome on 2008-04-27
z

---

### Post by hums07 on 2008-04-27
You just need to click the "Check" button. Later another button "Upgrade" will appear, then you need to click it.

---

### Post by zalberico on 2008-04-27
> **zaussome said:**
> Bah! That's it. I was running Update Manager with no arguments. Thanks very much for your help, everybody! Very greatful. :)

Glad it all worked out! :)

---

### Post by zalberico on 2008-04-27
Glad it all worked out! :)

---

