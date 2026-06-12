---
title: "Issues preparing Lubuntu for dual boot."
date: 2014-03-07
forum: New to Ubuntu
---

### Post by jeremyhammer007 on 2014-03-07
I am working on my wife's Toshiba 64 bit net book.  The hard drive failed and I could not create a windows recovery disk.  As a result I ended up installing Lubuntu 13.04 on the new hard drive so we can learn how to use Linux and be familiar with it.  (I have used it in the past but am not used to it).  I now have a windows install disk to finish my tinkering.

After installing Lubuntu, I resized/changed partitions so that I could add a Windows 7 install later.  There are currently 4 partitions:

Lubuntu (about 100gb)
Empty NTFS (about 105gb for Windows)
Storage (most of the remainder of the disk, so that data files can more easily be accessed and found in both operating systems)
Linux Swap partition (small, like 1gb, whatever the system set up as default)

I now have a Windows install ready and was trying to follow walk-throughs on what to do next.  I'm having the following issues:

(bear with me, I'm not finding the actual processes I used, so I'm trying to go from memory)

using 'dd if=/dev/sda of=/mbr.bin bs=446 count=1' returns 'dd: opening '/dev/sda': Permission denied
(I have the only account set for administrator)

using 'sudo gedit /boot/grub/menu.lst' returns sudo: gedit: command not found
(sudo asks for the account password before returning this)

I'm trying to make sense of the grub2 reinstall instructions here: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2) but I don't see what needs to be done before the windows install to back up grub or whatever I need to do.

I keep running into dead ends.  I always have the option of just installing windows and reinstalling Lubuntu as there is nothing critical on the drive, but I'm trying to learn to do things the right way from a troubleshooting perspective (repairman and programmer by trade)

What do I need to do?  How different is Lubuntu from Ubuntu?  Seems like every search engine I type 'lubuntu' into changes it to 'ubuntu' with no option of not doing this.  The tutorials and instructions I find are for Ubuntu.

---

### Post by oldfred on 2014-03-08
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Only the gui and standard apps are different, so at the kernel level or before booting, software cannot tell which flavor of Ubuntu you are running. If particular you have to manually edit it.

---

### Post by Bill Tetzeli on 2014-03-08
There's also Rescatux, which has worked flawlessly for me in repairing boot issues.
[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

---

