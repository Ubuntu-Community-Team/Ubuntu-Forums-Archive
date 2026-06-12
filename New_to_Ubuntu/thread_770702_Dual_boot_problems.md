---
title: "Dual boot problems"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by gredawarha on 2008-04-27
Hello all

A while back I tried to install Ubuntu 7.10 onto my main desktop computer.  This computer allready had Vista (I know boooo!) and I wanted to end up with a dual boot scenario.

I tried several times but it would seem to install okay and then when I rebooted the computer it would allways boot straight to vista  no GRUB, nothing.

I gave up.

Well downloaded the latest Ubuntu Hardy Heron and though id give it another go, but the same old thing reboot after Hardy installed and it booted straight into vista.  I have a couple of years experience with ubuntu but have no idea with this issue.  I have also successfully installed an XP/Ubuntu dual boot on my old laptop.

It's just this one computer and Vista that is causing me problems.

Any help would be most appreciated.

---

### Post by fredwilby on 2008-09-20
At the last install screen (the summary page) did you leave the bootloader settings as default ( install GRUB)?

you could try ( from a livecd ):

```
sudo grub /dev/yourdisk

root /dev/ubuntupartition

setup /dev/yourdisk

quit
```

then reboot.

---

