---
title: "CD Rom in VMWare Server"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-06-04
Hi I have installed the VMware server on Hardy 8.04 and am running the Ubuntu Server as a guest OS.

As you know the Ubuntu server is text only (no nice GUI).

I want to transfer data from a CD to my virtual machine. In the VM ware server everything is set correctly as far as I can tell:
CD-ROM 1 (IDE 1:0)
Device status: connected
Connection: Use physical drive
Location: host
Device: auto detect.

When I insert a CD however it opens in my host OS (Ubuntu Hardy) but I cannot find it in the VM (I have looked in /media/cdrom and /media/cdrom0 but they are both empty)

I am relatively new at working with Linux, so could someone please tell me where I should look to find the files on the CD Rom within the virtual machine. (Or if there is something wrong with my configuration)

Many thanks

---

### Post by Jim_in_Germany on 2008-06-04
Answering my own questions again.
Solution was simple.
Look in fstab to see what name the device was given and then mount it manually, in this case with:
mount /dev/scd0 /media/cdrom
then:
cd /media/cdrom
ls -l 
etc ....

---

