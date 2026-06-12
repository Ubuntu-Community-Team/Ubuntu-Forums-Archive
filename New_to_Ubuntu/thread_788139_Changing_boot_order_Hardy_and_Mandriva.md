---
title: "Changing boot order Hardy and Mandriva"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by worlestone on 2008-05-09
I have been running Ubuntu 8.04 for about a week now and all seems OK.  Unfortunately I also installed Mandriva a few days ago to check something out.

My system now gives the option of booting into Hardy, but uses the Mandriva boot thingy and lists Hardy as no. 3 option.

How can I either change the boot order or preferably remove/uninstall Mandriva so that I just boot into Hardy?

Thanks in anticipation

NB - assume a no knowledge user :-)

---

### Post by Six_Digits on 2008-05-09
Try startupmanager.

```
sudo apt-get install startupmanager
```Oh, to get rid of Mandriva I would simply delete that partition using Gparted. Then reboot and see if it worked. Better have a Super GRUB recovery disk in case this way of removal is improper.

```
sudo apt-get install gparted
```

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by worlestone on 2008-05-10
Thanks for the help.  I could not work out what to do with Startupmanager.  Opted to delete the partition Mandriva was on with Gparted and then used Super Grub Disk to fix the Master Boot Record.

All seems OK now

---

### Post by Six_Digits on 2008-05-10
Excellent :)

---

