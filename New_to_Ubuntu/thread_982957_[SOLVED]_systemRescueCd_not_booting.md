---
title: "[SOLVED] systemRescueCd not booting ?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by michiedo on 2008-11-15
for sure i'm doing something wrong, but i'm unable to find it
:-(
i've downloaded and burned a cd with "systemRescueCd", but i'm unable to boot from it !
i've burned it whit K3B, and also with "wodim" from console, but two differents pc refuse to boot from it.
the bios(es) boot order is ok, the cd contains the following directories:

drwxr-xr-x 2 root root      2048 2008-10-30 01:03 bootdisk
drwxr-xr-x 2 root root      2048 2008-08-01 08:47 grub4dos
drwxr-xr-x 3 root root      4096 2008-10-30 01:04 isolinux
drwxr-xr-x 2 root root      2048 2008-10-26 13:19 ntpasswd
drwxr-xr-x 2 root root      2048 2008-10-26 13:19 syslinux
-rw-rw-rw- 1 root root 206774272 2008-10-30 01:03 sysrcd.dat
-rw-r--r-- 1 root root        45 2008-10-30 01:04 sysrcd.md5
-rw-r--r-- 1 root root       876 2008-08-01 08:47 usbstick.htm
-rw-r--r-- 1 root root         6 2008-10-30 01:03 version

the cd is a rewritable one, but it should not make any difference

let me be more clear: the pc(s) display the message "booting from cd" the cd led blinks, then appeard the message "failure" (as if the cd is not bootable or not present) and the boot continues with hd (grub)

thank you for any help !

---

### Post by taurus on 2008-11-15
Did you burn it as an image file?  In k3b, you would go to Tools -> Burn CD Image... and browse to where your ISO file is.

---

### Post by michiedo on 2008-11-15
>Did you burn it as an image file? In k3b, you would go to Tools -> Burn CD Image..

yes, in K3b i've choosed "burn cd image" and, in another try, from console :
wodim dev=/dev/hdc -v systemrescuecd-x86-1.1.1.iso
:-(

---

### Post by mapes12 on 2008-11-15
> the cd is a rewritable one, but it should not make any differenceSometimes it does make a difference. Try a record once CD-R. I have had similar problems with rewritable media.

---

### Post by michiedo on 2008-11-15
thanks to all, it looks like version 1.1.1 of systemrescuecd has troubles.
i've found this post on their forum:
[http://www.sysresccd.org/forums/viewtopic.php?t=2326](http://www.sysresccd.org/forums/viewtopic.php?t=2326)

now i' downloading the new "beta", and hope in more luck.
i'll post in this thread the results.
:-)

---

### Post by michiedo on 2008-11-15
no joy with the "beta", so downloaded and burned (on rw-cd) the previous one (1.1.0) ... it boots like a charme
:-)

---

