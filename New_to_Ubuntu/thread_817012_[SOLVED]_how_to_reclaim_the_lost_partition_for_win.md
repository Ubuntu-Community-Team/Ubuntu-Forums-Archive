---
title: "[SOLVED] how to reclaim the lost partition for windows after a ubuntu install failure"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by copperco2 on 2008-06-03
i have ubuntu installed on my laptop and also wanted to have it on my desktop.
but it seems there is a problem with the hard disk..'its old' or the ' machine needs a cooler environment' or such reasons i could not install 7.10 or 8.04. then i tried to partiton the free space to install ubuntu 7.10, deleted the one of the drives to create root and swap partitions for the installations.. 
This attempt was also a failure and i am now with a 40GB hard disk and only one part of it seen in the systems...

how can i reclaim the lost space, at least let me use it for windows... if not ubuntu. May be i will have to go for a new hard disk to install a ubuntu version. 

My desktop configuration is P4, 2GHz, 512 Ram, 40 GB hard disk (now only 10GB for use).

This machine dates back to 2006..

---

### Post by Sef on 2008-06-03
Get [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

From the site:

> TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy. 

---

### Post by copperco2 on 2008-06-03
can also try to undo the changes i have made in the making of partition by again initiating the installation and then when it askes for the space to eb installed then simply undo..

is it feasible..?

---

### Post by pjnsmb on 2008-06-03
> **copperco2 said:**
> can also try to undo the changes i have made in the making of partition by again initiating the installation and then when it askes for the space to eb installed then simply undo..

is it feasible..?

Had a go with Testdisk a couple of weeks ago and finished up re-installing !

Might be easier to use GParted partition editor available from Synaptic using the LiveCD

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by copperco2 on 2008-06-03
Thank you all, very much for your help.
i tried booting from XP installer and then formatted the partition that was there from Ubuntu failure.. and everything seems to go all right.


Thanks a ton for the help.

regards,

---

