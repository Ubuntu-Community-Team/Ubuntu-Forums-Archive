---
title: "dual boot issues, vmware?"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by musicguyguy on 2012-01-03
I have Ubuntu Studio and Windows 7 (both x64) installed on my machine, but I have many problems switching to the other OS when I start up my computer.

My partitions looks like this:
[1: Ubuntu, 50GB]
[2: Windows system, 0.2GB]
[3: Windows, 200GB]
[4: NTFS, >1TB]

I want to delete Ubuntu and expand my Windows partition(#3), but the windows system partition (2) is "in the way".

Is there any way to fix this?


I've read a little about running VMware on servers, and then installing "guest OSes" on top of it. (And guest OSes can run simultaneously?) Could I pehaps make backup images of my partitions, install something like VMware, and then copy the partitions onto the VMware?

---

### Post by Chiel92 on 2012-01-04
> **musicguyguy said:**
> I have Ubuntu Studio and Windows 7 (both x64) installed on my machine, but I have many problems switching to the other OS when I start up my computer.

My partitions looks like this:
[1: Ubuntu, 50GB]
[2: Windows system, 0.2GB]
[3: Windows, 200GB]
[4: NTFS, >1TB]

I want to delete Ubuntu and expand my Windows partition(#3), but the windows system partition (2) is "in the way".

Is there any way to fix this?


I've read a little about running VMware on servers, and then installing "guest OSes" on top of it. (And guest OSes can run simultaneously?) Could I pehaps make backup images of my partitions, install something like VMware, and then copy the partitions onto the VMware?


Hey, 
have a look here:
[https://help.ubuntu.com/10.04/hardware/C/disks.html](https://help.ubuntu.com/10.04/hardware/C/disks.html)

It assumes you have ubuntu available and gparted installed.
As you want to uninstall ubuntu and AFTER that resize/move, you could use live ubuntu (from cd or usb) to perform this.

Also, do not just delete the ubuntu partition. Have a look on the internet how to safely uninstall ubuntu. Otherwise you will probably get issues with your bootloader.

regards!

---

