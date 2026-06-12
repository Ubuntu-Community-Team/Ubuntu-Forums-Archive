---
title: "alongside installation with windows 8"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by vibaviattigala on 2013-03-14
i have a 2GB computer it has windwos 8 32 bit i want to install ubuntu 32 bit permently alongside windows my F drive is 200 GB

i had a ubuntu dvd when i select alongside installing it ejects the disck but the live dvd runs well when trying .how do i install it?

another question i want to buy a better laptop is there any pre installed ubuntu laptops or will it suppots laptops all drivers?

---

### Post by oldfred on 2013-03-14
If computer was Windows 7 before, have you used all 4 primary partitions?

Post this from terminal in liveCD.

sudo fdisk -lu

Ubuntu will only install to Linux formatted partition, not NTFS (except wubi). You either need unallocated space and an available primary partition or Linux formatted partition(s).

Install is essentially the same for all recent versions.
       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

