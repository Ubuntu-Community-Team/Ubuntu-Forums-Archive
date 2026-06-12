---
title: "Can't install alongside WinXP"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by sundit1 on 2012-11-24
Recently I uninstalled Ubuntu 11.04 which had been installed inside Windows. I threw it out because I had never been able to connect to the internet.

I bought a disc for 12.10 (which includes Wubi) and it connects easily when run from the disc BUT I am not given the option to install alongside Windows. Since the older version did so, does anyone know why this will not?
My disc is not partitioned.

---

### Post by oldfred on 2012-11-24
You hard drive has to be partitioned if you have both Windows & Ubuntu on it.

Post this from terminal in liveCD/USB.

       sudo parted /dev/sda unit s print

---

### Post by bcbc on 2012-11-24
Installing Wubi from CD has been disabled since 12.04, but you can still do it with the argument --force-wubi: [http://askubuntu.com/q/125015/14916](http://askubuntu.com/q/125015/14916)

---

### Post by mlentink on 2012-11-24
> **oldfred said:**
> You hard drive has to be partitioned if you have both Windows & Ubuntu on it.

Not if it was a Wubi installed, which the OP said it was.

OP: do you want to redo a Wubi install (use the windows-installer) or do you want to create a dual-boot situation (Windows and Ubuntu next to each other on separate partitions)?

---

### Post by sundit1 on 2012-11-24
I want to avoid partitioning because Disk Manager does not give me the option to create a new partition. I will not attempt it from the command console because I do not know if it will destroy my Windows files.
The Ubuntu 11.04 was installed inside Windows and I had a choice of OS when booting.

---

### Post by monkeybrain2012 on 2012-11-24
> **sundit1 said:**
> I want to avoid partitioning because Disk Manager does not give me the option to create a new partition. I will not attempt it from the command console because I do not know if it will destroy my Windows files.
The Ubuntu 11.04 was installed inside Windows and I had a choice of OS when booting.

Of course it does, you need to boot off a live usb and run gparted. But some people said you should shrink the Windows partition with a Windows tool in Windows(I don't remember having done that, but I read it somewhere so I cite it just for your reference). 

Then when you install Ubuntu, choose "something else" instead of "install alongside .." a graphic representation of your hard drive layout will appear, then create 2 (or 3 see below) subpartitions in the free space created above (by shrinking Windows), a big one as "/" for the system and a small one for swap (about 1.5 x ram) . As another option you can create 3 partitions: / ; /home (to store your data) and swap. / and /home should be in ext4 file system. If you have a separate /home partition you can allocate maybe 10 -12G to / and it is quite sufficient

I have gotten rid of the XP partition for a few years, but as far as I remember it wasn't that difficult. :)

---

