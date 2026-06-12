---
title: "[SOLVED] Backing up the whole of my partition to an external hard drive"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Berean on 2008-05-18
Hi,

Having made a disk image of 7.10 and saving it to my external hard, I've had difficulty reinstalling it.  I used a combination of this thread - [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) - and another illustrating how to use Partimage.  Eventually - failing! - I did a fresh install of 8.04.  What I would like to know is;

1. Can I copy the whole of my partition of 8.04 onto a partitioned hard drive?
2. If so, can I then take the external hard drive and boot from it, from say, a usb bootable work PC?
3. Can you suggest how I go about it if it's possible?

Thanks - in advance - for your assistance.  Kind regards,

---

### Post by kubaknopp on 2008-05-18
and the answer is : rsync

to tell the truth i was never used it to create boot disc. Anyway: rsync is great tool for backups. First time it run   - copying entire volume, but next time only changes. Thats mean you can backup few gb in few minutes.

Script in attachment is for daily backup of the server. You can play with it.

---

### Post by SunnyRabbiera on 2008-05-18
yes, what you ask is very possible, and yeh probably rsync will do it for you

---

### Post by Berean on 2008-05-19
Thanks guys, but I was of the understanding that rsync (or Grsync as I use it) only copied files across, and did not produce a disk image.  If I'm wrong, do I simply partition my external hard drive and then using the live CD Grsync the files from my internal hard drive to my external?  To my limited thinking that doesn't quite make sense if I want to boot from my external hard drive.  Can you clarify please?  Regards,

---

### Post by WorldTripping on 2008-05-19
'rsync' will happily backup all of your partition files, to a USB device if you like.

As far as I'm aware though this will not make said USB bootable.

That is a separate procees, a guide to which can be found here;

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar")


Hope that helps.

---

### Post by housam on 2008-05-19
Creating disc images using dd :[[COLOR="Red"]_https://help.ubuntu.com/community/Backupsolutionsforlinux_[/COLOR]]("https://help.ubuntu.com/community/Backupsolutionsforlinux")

this will backup your entire disk to another one .

---

