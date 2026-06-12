---
title: "Grub failed to install on 12.10 64 bit"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by elixeroflife on 2013-02-12
Hello, typical n00b here

im fed up with Microsoft and i'd really like to get this to work...

Im installing Ubuntu 12.10 on a Dell Inspiron 1520. if it helps i can include the service tag so you can fully see what im working with.

i first tried 32 bit on a USB stick, no avail

tried 64 bit on usb stick, no avail

now im on  64 bit from a DVD drive, even burned with the slow write speed.

here is what fdisk get me

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086709

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   232366079   116182016   83  Linux
/dev/sda2       232368126   234440703     1036289    5  Extended
/dev/sda5       232368128   234440703     1036288   82  Linux swap / Solaris


just looked at the clock and im gunna wrap this up, gotta head to work. 

please looking forward to replies and help

Thank you

---

### Post by oldfred on 2013-02-13
Welcome to the forums.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by elixeroflife on 2013-02-13
> **oldfred said:**
> Welcome to the forums.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)



Thank you good sir.

I finally got Boot Repair to install, here is what it found


Please write on a paper the following URL:
[http://paste.ubuntu.com/1647086/](http://paste.ubuntu.com/1647086/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

No change has been performed on your computer.


im going to run the repair sequence and see if it boots

---

### Post by elixeroflife on 2013-02-14
thank you oldfred, i got the boot repaired.

---

### Post by oldfred on 2013-02-14
Glad Boot-Repair Worked.  :)

---

