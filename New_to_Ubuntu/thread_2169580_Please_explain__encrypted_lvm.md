---
title: "Please explain  encrypted lvm"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by PGHBSA on 2013-08-22
Please explain Guided -use entire disk and set up encrypted lvm.
Does this encrypt everything on the hard drive?  If i was to put in another live CD i could not read the contents of the drive?

---

### Post by Cheesemill on 2013-08-22
Correct.

Everything on the hard drive is encrypted except a small /boot partition which holds the files needed to boot the machine to the state where it asks for your password.

---

### Post by texaswriter on 2013-08-22
The disk will be encrypted by a passphrase. You would be able to mount this hard drive if you enter the passphrase. 

So if you install Ubuntu using encrypted LVM, then you put the live cd in and try to mount the hard drive, it will ask you to enter the passphrase. If you enter the correct passphrase, the disk will be mounted.

---

