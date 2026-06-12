---
title: "Lost my ubuntu..   after changing resolution.. pls. help"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by RIDE on 2008-05-10
I was trying to change the resolution of ubuntu, then I restarted...  now I can't get it to fully boot..    It runs like 5 items and lists them as "[ok]"...  the last item says something about running scripts...  and lists that as "[ok]"...   then nothing...  no matter what I type (just to check)  it does nothing...  just the black screen with the text saying that the 5 items are "ok"...


What can I do????   please help.    

Thanks in advance.

---

### Post by bumanie on 2008-05-10
Try booting into recovery mode and see if the linux vesa graphics driver is loaded. If so, you should be able to your graphics card back to the  original settings. If this doesn't work, you will have to go to console and try to fix it with command lines.

---

### Post by RIDE on 2008-05-10
Thanks...  but what do I do in recovery mode in order to get the settings back???  I'm a newb :(

---

### Post by RIDE on 2008-05-10
How do I tell if the Versa Graphics Drivers are installed??

---

### Post by RIDE on 2008-05-10
I booted into recovery mode...    (not sure how to scroll up??)... but... I do see that it lists the following:

* Mounting local filesystems...
[mntent]: line 8 in /etc/fstab is bad




Is everything lost???

---

### Post by disturbedite on 2008-05-10
no, i don't think everything is lost.  there is obviously a problem in your fstab file.
boot to recovery mode, then type:
```
cat -b /etc/fstab
```
post the output.  (of course, line 8 will be of particular relevance).

---

