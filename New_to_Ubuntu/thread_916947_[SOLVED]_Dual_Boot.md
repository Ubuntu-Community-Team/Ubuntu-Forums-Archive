---
title: "[SOLVED] Dual Boot"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-09-11
Hy all!
I have a quick question.I have a dual boot system Windows XP and Ubuntu 8.04.I have a 120 GB hard drive with 3 partitions:a windows partition (NTFS) a data partition (NTFS) and the Ubuntu partition (Ext 2).I have to reinstall Windows (what a surprise, no :)).My questions is:will it screw up the GRUB?I don't want to turn my PC into a paper weight.
Thanks!

---

### Post by sisco311 on 2008-09-11
> **Troll_the_Great said:**
> My questions is:will it screw up the GRUB?
Yes, but you can reinstall it from the live cd.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by t0p on 2008-09-11
> **Troll_the_Great said:**
> Hy all!
I have a quick question.I have a dual boot system Windows XP and Ubuntu 8.04.I have a 120 GB hard drive with 3 partitions:a windows partition (NTFS) a data partition (NTFS) and the Ubuntu partition (Ext 2).I have to reinstall Windows (what a surprise, no :)).My questions is:will it screw up the GRUB?I don't want to turn my PC into a paper weight.
Thanks!

Very often, installing windoze after ubuntu results in windoze screwing up grub.  It is fixable, but I don't know how...

Anyway, in my experience it's better to install  windoze first, then ubuntu.

---

### Post by Troll_the_Great on 2008-09-11
> **sisco311 said:**
> Yes, but you can reinstall it from the live cd.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

This should be easy enough.Thanks allot!

---

### Post by Troll_the_Great on 2008-09-12
One more question before I take the plunge:those are the exact commands I should run?
```
sudo grub

      root (hd0,0)

      setup (hd0)

      exit
```
Like I said, I have 3 partitions, the first one is windows and the third one is Ubuntu.
Thanks allot.

---

### Post by Tatty on 2008-09-12
This page might give you a little more info:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by caljohnsmith on 2008-09-12
> **Troll_the_Great said:**
> One more question before I take the plunge:those are the exact commands I should run?
```
sudo grub

      root (hd0,0)

      setup (hd0)

      exit
```
Like I said, I have 3 partitions, the first one is windows and the third one is Ubuntu.
Thanks allot.
Those commands will depend on which partition your Ubuntu is on, so it may not be (hd0,0). One of the best ways to reinstall Grub, and make sure you get the correct Ubuntu partition, is by doing the following from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
The "find" command is what helps you determine the correct partition to use in the subsequent commands to reinstall Grub. Let us know how it goes or if you have problems. :)

---

### Post by Troll_the_Great on 2008-09-12
Thank you all very much, I manage to reinstall windows and I recovered my precious...\\:D/
Ubuntu forums ROCKS!!!:guitar:

---

