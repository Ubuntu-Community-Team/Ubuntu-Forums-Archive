---
title: "Ubuntu Server out of disk space"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by armegeden on 2013-09-29
Hello all,

I have Ubuntu Server (12.04.3) running as a virtual machine inside an ESXi host; all home use.

In ESXi, I set the VM to have one virtual disk at 10GB.  I installed the server and use it primarily as a dynamips server for my GNS3 lab.  

The server is now saying it is out of space.  I believe the problem is that the server is only seeing 2GB usable; but why?

```
loki@hoenir:~$ df -l
Filesystem          1K-blocks    Used Available Use% Mounted on
/dev/sda1             1998672 1965016         0 100% /
udev                  4077872       4   4077868   1% /dev
tmpfs                 1635612     464   1635148   1% /run
none                     5120       0      5120   0% /run/lock
none                  4089028       4   4089024   1% /run/shm
overflow                 1024       0      1024   0% /tmp
/home/loki/.Private   1998672 1965016         0 100% /home/loki



```

Yet when I look at fdisk, it sees 10GB.  (please keep in mind I am not a NIX guru)

```
loki@hoenir:~$ sudo fdisk -l


Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b494


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     4196351     2097152   83  Linux
/dev/sda2         4198398    20969471     8385537    5  Extended
/dev/sda5         4198400    20969471     8385536   82  Linux swap / Solaris


Disk /dev/mapper/cryptswap1: 8586 MB, 8586788864 bytes
255 heads, 63 sectors/track, 1043 cylinders, total 16771072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48677040


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
loki@hoenir:~$

```

I'm probably overlooking something, but.... help?

Thanks

---

### Post by DuckHook on 2013-09-29
Although you did define 10GB as a virtual HDD, you then subdivided that 10GB into only a 2GB partition for Linux (sda1) and 8GB for a swap partition (sda2 and sda5). If you can do without the swap, you can recover 8GB and use it for your OS and data.

---

### Post by armegeden on 2013-09-29
DuckHook, many thanks for the response.

I suppose I'll write this off as just clicking next during the Server install, but I do not recall the option for the swap file partition.  Oh well.

I do not know of anything I do that would require a swap partition.  Is it okay to go without a swap partition?

If it's okay, then I'll research on how to delete a swap partition then assign the unallocated space to the sda1.

Thanks again.

---

### Post by DuckHook on 2013-09-29
As I recall, swap is automatically created if you choose the default install.

Whether a swap is needed or not is a contentious matter among geeks and gurus. Based on the swap that was automatically created, I am guessing that you assigned 8GB of system memory to your VM server (please confirm). Since I don't know anything about dynamips, I have no idea if this is sufficient or overkill. For typical desktop use, 8GB of memory is more than enough, in which case a swap is largely superfluous. The problem is that if your system runs out of main memory, it will simply crash or drop random apps. This is why some gurus insist on a swap even if their computer has scads of system memory. Additionally, you must have at least as much swap as RAM if you want to hibernate. However, this should not be a consideration on a server and especially not on one running within a VM.

[Here]("https://help.ubuntu.com/community/SwapFaq") is a good resource that explains swap and how to create/change/delete it.

---

### Post by armegeden on 2013-09-29
Ah hah.  I believe I understand.  You are correct, I assigned 8GB of memory mainly due to dynamips.  I use GNS3 on my PC to emulate virtual Cisco routers for labs and study.  With this server, I offloaded the virtualization processing to the server running dynamips, and my PC is just the GUI front end.  Very convenient.

Whether or not I'll go over 8GB of memory I can't answer.  Right now, I do not approach this limit, but I gave it the extra amount so that I would be in a safe zone.  You are also right, I would never hybernate this server.

I'll have to read through your link on what to do.  It's a fresh enough server that I may just blow it out and start over, though that would kill my learning experience.  :-)

Thanks again for all your help.  Much appreciated!

---

### Post by DuckHook on 2013-09-29
You are more than welcome. And you are absolutely right that trying to correct your setup through manipulation will educate you much faster than nuking your install and starting fresh, as long as you are prepared for some frustration, pain and head-scratching along the way. I admire your attitude. Happy Ubuntuing!

---

