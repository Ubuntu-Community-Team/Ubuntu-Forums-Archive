---
title: "Is it easier to dual boot Vista?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-08-13
Is it easier to dual boot Vista instead of XP?  Because I've had a heck of a time trying to dual boot XP.

Thanks 
Matt

---

### Post by RequinB4 on 2008-08-13
Yes, because Vista has a built-in partitioner.

What exactly are you having trouble with with XP?

---

### Post by hellodoggie on 2008-08-13
> **RequinB4 said:**
> Yes, because Vista has a built-in partitioner.

What exactly are you having trouble with with XP?

Here is my original Post
[http://ubuntuforums.org/showthread.php?p=5564630#post5564630](http://ubuntuforums.org/showthread.php?p=5564630#post5564630)

I installed grub with:

- root (hd1,4)
- setup (hd1)
- quit

That worked well, and I see grub there.

But then when I choose 'ubuntu' I get:
Error 21: Selected disk does not exist press any key to continue.

I have already tried:
sudo grub
grub> find /boot/grub/stage1
[should return a partition in the form of (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

and then edit menu list:
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

But that does not work

---

### Post by tommynz1975 on 2008-08-13
> **RequinB4 said:**
> Yes, because Vista has a built-in partitioner.

What exactly are you having trouble with with XP?

This is where I went wrong...   use the vista partitoner.  I understand that the ntfs structure changed some how?  between xp and vista....

---

### Post by tuxxy on 2008-08-13
Dual boot with Vista then install your XP in virtualbox once you up and running in Ubuntu

---

### Post by cybrsaylr on 2008-08-13
I have dual boots with XP/Hardy and Vista/Hardy.
Both went in with no problems but it can be confusing. I just carefully studied and followed the CD directions and it was OK. Both PCs run great.

---

### Post by sandysandy on 2008-08-13
what is output of [COLOR="Red"]sudo fdisk -lu[/COLOR]

option also exists to boot ubuntu with windows bootloader

see here

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

[http://ubuntuforums.org/showthread.php?t=208951](http://ubuntuforums.org/showthread.php?t=208951)

regards

---

