---
title: "problem with booting Ubuntu 12.04 LTS"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by onlineprasanna on 2012-04-29
hello all,

I have been using ubuntu since 2years as dual boot with windows 7,it is really fascinating to use ubuntu:), so today i went on to upgrade my 11.10 perfectly working version with 12.04LTS in my Lenovo G450 laptop. I downloaded the whole image, burned on a cd, booted up with it, it was booted finely, it was awesome to note the speed,look and feel, so went on to upgrade 11.10 to 12.04LTS by using same installation cd. The installation was went on fine near end, by that time it was struck which forced me to shut it down forcibly.:(
since the up gradation was not fully successful, i followed the method said in the forum,
once again booted with cd,
opened terminal,
typed following commands,
[B]sudo mkdir /media/fix
sudo mount /dev/sda2 /media/fix[/B]
(replaced /dev/sda2 with name of drive, e.g. sda1 etc.)]
**sudo chroot /media/fix su**
updated the system via
[B]apt-get update
apt-get upgrade
apt-get dist-upgra[/B]de
I hope by this time my system updated fully to the released version.
now typed “exit” to exit the chroot, then rebooted the computer.

while restarting the grub menu came up fine, but from there on a blank screen appears,:( the system won't boot, but with windows 7 works fine.
is this the problem with grub or with kernel.
how to solve it?
i am attaching the logs.
waiting for the help

---

