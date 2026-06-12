---
title: "black screen"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by mithritades on 2008-06-01
i tried to install ubuntu on a thumbdrive,but after i was finished an tried to get back to windows i just get a black screen that says error 21 or when i try to run ubuntu from the thumbdrive it's just a black screen that says error 5....it's 8.04 from a live CD by the way,any help appreciated:confused:

---

### Post by rich86 on 2008-06-01
If you installed onto the thumb drive then i suspect that you have overwritten the MBR (Master Boot Record) of the main hard drive. If it is just windows on the main drive put in the windows cd and go the the rescue command promt and type 'FIXMBR' (no quotes) that should restore the windows MBR so windows will boot. 
As for the thumb drive you can either re-install and this time just before you finalise go to advanced and make sure that it is only chaning the MBR of the thumb disk. This will probably be /dev/sdb if you only have one internal drive. You can check by opening a terminal and typing fdisk -l and find the name of the thumb disk.
When you want to boot to the thumb drive you need to have it plugged in and select boot from USB. If the thumb drive is not plugged in you should just boot windows normally.
Hope that helps a bit,
Rich

EDIT: these posts could help:
[http://ubuntuforums.org/showthread.php?t=80811&page=49&highlight=success+external](http://ubuntuforums.org/showthread.php?t=80811&page=49&highlight=success+external)
[http://ubuntuforums.org/showthread.php?t=744800](http://ubuntuforums.org/showthread.php?t=744800)
[http://ubuntuforums.org/showthread.php?t=610422](http://ubuntuforums.org/showthread.php?t=610422)

---

### Post by bobnutfield on 2008-06-01
Grub error 21 means that you are trying to boot to a disk that grub can't find.  Do you have a linux installation on your hard drive along with windows, or were you just trying to install only to the pendrive?

---

### Post by mithritades on 2008-06-01
@bobnutfield,just the thumbdrive

---

### Post by ajgreeny on 2008-06-01
The error 21 is because grub, which has replaced the windows MBR is looking for the grub configuration file (/boot/grub/menu.lst) which is on the thumb drive.  When that is not in place, your system can go no further.

Grub error 5 is a bit more of a problem and may mean that the files you are accessing on the thumb drive are corrupted.  Have a look [here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18") for more detailed info.

---

### Post by bobnutfield on 2008-06-01
> **mithritades said:**
> @bobnutfield,just the thumbdrive

As rich86 has pointed out, it appears that you have inadvertently partially installed grub to your mbr, but it is not a massively critical problem.  If you have your windows install cd, just boot to it, choose resuce installtion, and type:

fdisk /fixmbr

assuming that you are using XP.  

Bob

---

### Post by mithritades on 2008-06-01
thnx ya'll,ya'll the bestest(elohel).ok,i'm back on windows. Now can i try to re-install my live CD on my thumbdrive again since it seems like it was corrupted on the first try?...and how would i go about it so it won't happen again?...a step by step tutorial if u will or is there already a post on here that i can follow..thnx again!

---

### Post by bobnutfield on 2008-06-01
You will find all you need right here:

[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

Bob

---

### Post by mithritades on 2008-06-01
how do i erase the thumbdrive i tried to install ubuntu on in the first place or can i just overwrite it?

---

### Post by bobnutfield on 2008-06-01
Just overwrite it.  No need to format it, although you could load up live cd and use gparted to format the pen drive if you want to format it to an ext3 file system.

Either is fine.

Bob

---

