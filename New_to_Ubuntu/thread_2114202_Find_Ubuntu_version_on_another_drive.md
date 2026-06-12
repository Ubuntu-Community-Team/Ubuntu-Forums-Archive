---
title: "Find Ubuntu version on another drive"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by wejones10 on 2013-02-09
How do I find out what version of ubuntu is on my hard drive while my laptop is booted up with a 12.10 CD?

Saga
I am restoring grub2 after royally dorking up my laptop that I dual boot W7/Ubuntu.  I thought I would resize both my partitions and install W8.

I thought I was at 12.10 but I am probably at another version.
I have completed the following commands:

sudo su
mount /dev/sdx# /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
cp /etc/resolv.conf /mnt/etc/resolv.conf
chroot /mnt

I get 'bin/bash: exec format error' here.

So upon further research I think my livecd version is different than the installed version.

mount info for linux hard drive partition:

/dev/sda6 on /media/ubuntu/8a2ab........ type ext4 (rw,nosuid,nodev,uhelper=udisks2)

How I got here.

I resized a W7, 64bit partition that messed up the W7 boot.  I restored the W7 boot and dorked up the grub2 bootloader.  So I am trying to get back to just the messed up w7 partition with grub2 working.

---

### Post by Prince Valiant on 2013-02-09
Good luck with your OS switcheroo!  Look in the following file; that should give you the Ubuntu OS version.

/etc/lsb-release

Cheers!
Val

---

### Post by wejones10 on 2013-02-09
That worked great, thanks.  I thought it would be easy.

I was way off.  I am at 11.10

A couple of followup questions, if I upgrade/install 12.10, I should be able to install grub2?  I can see and mount my W7 partition so I just think I will have to deal with the issues of W7 mft & booting.  Not as easily resolved as with linux.

Should I use a liveCD of ver 11.10 to run gparted to resize the existing linux partition before doing an upgrade to 12.10?

---

