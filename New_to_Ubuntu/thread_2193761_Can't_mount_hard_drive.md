---
title: "Can't mount hard drive"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by wheelerrver on 2013-12-14
I am trying to work with Ubuntu on a USB drive.  When I try to use it on my computer it seems to work fine except it will not let me mount my hard drive.  When I click on it I get this message :Error mounting: mount exited with exit code 21: mount: according to mtab, /dev/sda2 is already mounted on /media/TI106033W0C

Can anyone help me?  When I load Ubuntu from a DVD I am able to mount the drive.

---

### Post by asus-user on 2013-12-14
> **wheelerrver said:**
> I am trying to work with Ubuntu on a USB drive.  When I try to use it on my computer it seems to work fine except it will not let me mount my hard drive.  When I click on it I get this message :Error mounting: mount exited with exit code 21: mount: according to mtab, /dev/sda2 is already mounted on /media/TI106033W0C

Can anyone help me?  When I load Ubuntu from a DVD I am able to mount the drive.

Maybe you are facing the same problem as in this thread: [http://ubuntuforums.org/showthread.php?t=1476540](http://ubuntuforums.org/showthread.php?t=1476540) ?

---

### Post by wheelerrver on 2013-12-14
No cd or dvd in my drive which was the other person's problem.  Mine is similar to the other user since I used the usb for some time before it decided to give me this message.  I, too, thought it might relate to a cold shutdown although I don't remember doing it.  I am running 12.04, incidentally.  When I looked at media, I did see one instance of the cd drive,  but nothing is in there.  I will try to get exact wording from etc/mtab and etc/ftab - I only checked media.

---

### Post by asus-user on 2013-12-15
> **wheelerrver said:**
> No cd or dvd in my drive which was the other person's problem.  Mine is similar to the other user since I used the usb for some time before it decided to give me this message.  I, too, thought it might relate to a cold shutdown although I don't remember doing it.  I am running 12.04, incidentally.  When I looked at media, I did see one instance of the cd drive,  but nothing is in there.  I will try to get exact wording from etc/mtab and etc/ftab - I only checked media.

Do your thing, and check this link, it might help you :) : 
[http://www.linuxquestions.org/questions/linux-mint-84/usb-issues-exit-code-21-kills-mounting-hd-how-to-usb-diskcheck-943156/](http://www.linuxquestions.org/questions/linux-mint-84/usb-issues-exit-code-21-kills-mounting-hd-how-to-usb-diskcheck-943156/)

---

### Post by Bucky Ball on 2013-12-15
Switch machine off. Unplug the drive. Boot up. Once at a desktop, plug the drive in and turn on. Does it automount? Is there a message, error or otherwise?

---

### Post by jimmyh1972 on 2013-12-17
you can open any file and then go to
compter > media and you should see your HDD just click on it
if you dont see it you'll have to config /etc/fstab
to do that you'll have read some about fstab and to use the terminal 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

