---
title: "Upgraded my PCs, they have different kernel versions"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by cwmoser on 2014-07-11
I upgraded both my PCs - a desktop and laptop.
Both are running Ubuntu 14.04.
Both are updated -- sudo apt-get upgrade


My Desktop PC shows:
$ uname -a
Linux klaatu-2 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


My Laptop PC shows:
$ uname -a
Linux carl-T500 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:43:42 UTC 2014 i686 i686 i686 GNU/Linux

Any insights into this????

Thanks

Carl
__________________

---

### Post by oldfred on 2014-07-11
One is 64 bit and the other is 32 bit. 
I do not think you should expect two versions to be identical.

I purposely installed 64 bit on my older laptop even though it only has 1.5GB of RAM. As long as I do not load to many apps at once or two large apps it runs well with fallback/flashback and full Ubuntu. But it does not have enough video hardware to support Unity. Most would suggest older hardware like that run a lighter weight flavor of Ubuntu.
Then my laptop & desktop are running the same version.

---

### Post by ptn107 on 2014-07-11
Try again with:
```
sudo apt-get update; sudo apt-get dist-upgrade
```

A regular
```
sudo apt-get upgrade
```
from the command line will not install new kernel versions because this mode is not allowed to install *new* packages.  It will only upgrade *existing* ones.

If you use the gui software updater application from the dash new kernels *will* be installed because it uses dist-upgrade for the process.

---

### Post by Impavidus on 2014-07-11
Although 32 bit and 64 bit are not necessarily at the same version, your 64 bit system is running behind. On my laptop:```
$uname -a
Linux Elektra 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

And +1 to ptn107.

---

### Post by grahammechanical on 2014-07-11
Phased Updates, anyone?

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

We might call them kernels but they are in fact revisions of the same Linux 3.13 kernel made by the Ubuntu developers. What really is the difference between -24 and -30? It might be a fix for a bug that does not affect our hardware.

Regards.

---

### Post by bapoumba on 2014-07-11
> **grahammechanical said:**
> Phased Updates, anyone?

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

We might call them kernels but they are in fact revisions of the same Linux 3.13 kernel made by the Ubuntu developers. What really is the difference between -24 and -30? It might be a fix for a bug that does not affect our hardware.

Regards.
I'm not sure it be related to phased updates, as the OP has been using apt-get which does not check for them (neither do aptitude or synaptic), only Software Updater :)
I have observed that sometimes kernels are held back, I have no explanation for this. A dist-upgrade as suggested pulls them through. If I am to dist-upgrade for a kernel, I only **sudo apt-get dist-upgrade <kernel_metapackage>**.
To the OP: do you have held packages when you **sudo apt-get update** ?

---

### Post by cwmoser on 2014-07-11
I fixed the problem.  
I have 2 hard drives - a 128GB SSD and a 500GB SATA drive.
For some reason the UUID was the same for both /dev/sda1 and /dev/sdb1
I must have cloned by root drive some time ago.

When I ran **df -h** it revealed that my root was /dev/sdb1 and /home was /dev/sda3
apparently grub was getting confused with the duplicated UUID.  I had previously issued
**update-grub** to update the boot menu.

What I was observing was that under /boot on /dev/sdb1 I had two kernels - a -24 and a -30
kernel, and /boot on /dev/sda1 had only the -24 kernel.  Grub would only create a -24 kernel
in the menu.  

I straighten this out so that my /dev/sda SSD has both / and /home on it.
Fixing all this should make the system run faster by using the SSD for /.

So the moral to this story is if you can't get the kernel to get updated,
issue **sudo blkid** and see if you have a duplicate UUID.

Carl

---

### Post by bapoumba on 2014-07-12
Ah good, glad to see you figured it out. Please mark your thread as solved (under Thread tools), thanks :)

---

