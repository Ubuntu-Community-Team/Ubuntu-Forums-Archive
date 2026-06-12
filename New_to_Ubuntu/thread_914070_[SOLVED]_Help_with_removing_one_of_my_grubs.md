---
title: "[SOLVED] Help with removing one of my grubs"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-09-08
I had a dual boot with Ubuntu and Mandriva.

My (mandriva)grub menu made me select either Mandriva or Ubuntu. If I selected Ubuntu it would then go into the next grub menu (ubuntu kernel select).

I removed Mandriva using Gparted. Now the first Grub menu (the mandriva one) now makes an error.

I just want to completely remove the Mandriva grub so that only the one that lists the Ubuntu kernels comes up.

Any ideas?

Thanks in advance!

---

### Post by wolfen69 on 2008-09-08
the easy way out is to download [Kiwi linux]("http://kiwilinux.org/kiwi/en/") and load the live cd and go to system>administration>restore grub. kiwi is basically ubuntu with all the codecs. even looks the same.

---

### Post by pluckypigeon on 2008-09-08
is there a quicker way? 

I don't know if I can burn that to disc while I'm already using the cd-r drive with Ubuntu live cd

---

### Post by pluckypigeon on 2008-09-08
What I did was add the kiwi repo. (i ignored gpg key error)  Then installed restoregrub. then typed sudo restoregrub then i rebooted and all is well

---

### Post by phidia on 2008-09-08
Just boot from the install disk and choose re-install grub.
Or you can also reset your grub by entering grub (from a terminal enter "sudo grub") press tab to see the commands available to you from the grub commandline. For more detailed info see the [Ubuntu grub wiki]("https://help.ubuntu.com/community/GrubHowto").

BTW you never have more than one grub installed to the MBR the last install you did overwrote your MBR. Which is the standard method unless you select a custom grub install.

---

