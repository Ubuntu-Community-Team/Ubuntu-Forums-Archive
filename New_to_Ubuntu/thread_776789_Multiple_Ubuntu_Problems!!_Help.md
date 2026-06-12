---
title: "Multiple Ubuntu Problems!! Help"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Shadius on 2008-04-30
Hi, I'm new to Ubuntu. Long story short, I need to remove Ubuntu and reclaim that partitioned space for Windows. How do I do that? I don't know if it's called GRUB, but the screen that lets you choose Ubuntu or Windows doesn't show up anymore. I had it dual-booting. Also, when I do "sudo gparted" it shows "unallocated", but when I do "fdisk -l" it shows the partitions. I don't know what's going on. I just want to go back to Windows. Somebody please help me, please, I'm begging you.:( I don't want to ruin my computer.

---

### Post by Tatty on 2008-04-30
Firstly, if you want to re-install grub then do this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you want to remove ubuntu then:

1. Boot into a live cd
2. System->Administration->Partition Editor
3. Delete all of your linux partitions.
4. Boot into your windows XP cd
5. Select restoration console
6. Select XP installation
7. type fixmbr
8. reboot into windows and defrag your hard drive 3 or 4 times
9. reboot into live CD and expand your NTFS partition to fill the drive

done!

[http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959)

**Edit:** Are you sue your just havent hidden your Grub menu?  it might appear if you pres Esc when its loading.

---

### Post by Shadius on 2008-05-01
> **Tatty said:**
> Firstly, if you want to re-install grub then do this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you want to remove ubuntu then:

1. Boot into a live cd
2. System->Administration->Partition Editor
3. Delete all of your linux partitions.
4. Boot into your windows XP cd
5. Select restoration console
6. Select XP installation
7. type fixmbr
8. reboot into windows and defrag your hard drive 3 or 4 times
9. reboot into live CD and expand your NTFS partition to fill the drive

done!

[http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959)

**Edit:** Are you sue your just havent hidden your Grub menu?  it might appear if you pres Esc when its loading.
I'm not sure what happened to "GRUB". I'll try to see if it comes up if I press "Esc". Okay, I booted into Ubuntu's LiveCD and went to the Partition Editor but all it shows is "/dev/sda" and the size is 37.27 GB" My disk is a 40 GB disk, so does that mean that Ubuntu is taking over the whole drive? How is that when I can still use Windows? It just seems weird to me. It doesn't show any other partition. Also, I don't have a Windows XP CD, I just have the recovery CD, however when I try to use that and restore the computer to factory settings, it just reboots. It's not working as it normally would have worked.

---

### Post by Tatty on 2008-05-01
can you post the output of ```
sudo fdisk -l
``` (lowercase L not a 1) That will show us your partitions.

Also your /boot/grub/menu.lst file might be helpful.

---

### Post by Shadius on 2008-05-01
> **Tatty said:**
> can you post the output of ```
sudo fdisk -l
``` (lowercase L not a 1) That will show us your partitions.

Also your /boot/grub/menu.lst file might be helpful.
Okay, give me a second. I really appreciate you trying to help me. I'm using my laptop to get help from his forum, Ubuntu is installed on my desktop.

---

### Post by Shadius on 2008-05-01
> **Shadius said:**
> Okay, give me a second. I really appreciate you trying to help me. I'm using my laptop to get help from his forum, Ubuntu is installed on my desktop.
Okay, remember I said that my "GRUB" isn't showing? I tried pressing "Esc" but it said something about a keyboard error. Am I supposed to press it at a specific time? How can I get into Ubuntu if the GRUB isn't showing? Should I just use the CD?

---

### Post by Tatty on 2008-05-01
Yes you can use the CD to give the output for sudo fdisk -l.  Make sure you get your /boot/grub/menu.lst from your hard drive though, not from the CD.

Im a little confused, are any OS's booting on your computer?  I assumed from your post that it was jsut booting straight into Ubuntu... or are you saying that nothing happens?  If so then you could give some description as to what does happen...

---

### Post by Shadius on 2008-05-01
> **Tatty said:**
> Yes you can use the CD to give the output for sudo fdisk -l.  Make sure you get your /boot/grub/menu.lst from your hard drive though, not from the CD.

Im a little confused, are any OS's booting on your computer?  I assumed from your post that it was jsut booting straight into Ubuntu... or are you saying that nothing happens?  If so then you could give some description as to what does happen...
It's just booting into Windows. Okay, if I use the CD to get fdisk -l, how do I get /boot/grub/menu.lst from my hard drive then? This might help better to explain what I'm going through. [http://ubuntuforums.org/showthread.php?t=508927&page=7](http://ubuntuforums.org/showthread.php?t=508927&page=7)

I've been following that guide in hopes of fixing this.

---

### Post by Shadius on 2008-05-01
This is what I get when I do fdisk -l.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2717    21818128+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4211        4865     5261287+   f  W95 Ext'd (LBA)
/dev/sda3            2717        3549     6691072+  83  Linux
/dev/sda5            4356        4865     4089928+   b  W95 FAT32
/dev/sda6            4283        4355      586309+  82  Linux swap / Solaris
/dev/sda7            4211        4282      578277   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by lwvmobile on 2008-05-01
If its just booting strait into Windows then what you might try doing is just use the Windows CD and go into the recovery console to fix the master boot record for Windows using the command fixmbr. This is just a precaution to make sure your not using Grub to go strait to Windows.

In windows, right click on My Computer or Computer in Vista, click manage and then choose the disk drive management, at least I think that's what its called. It will show you all the partitions on all the disks and will show unknown partition for all linux partitions. You can just delete those 'unknown' partitions and reclaim that space for windows, but unless you have Vista, you may have to use another utility to resize the original C: partition to the full amount. I would, like was previously mentioned, defrag C: at least once before expanding the image just as a precaution.

---

### Post by Shadius on 2008-05-01
> **lwvmobile said:**
> If its just booting strait into Windows then what you might try doing is just use the Windows CD and go into the recovery console to fix the master boot record for Windows using the command fixmbr. This is just a precaution to make sure your not using Grub to go strait to Windows.

In windows, right click on My Computer or Computer in Vista, click manage and then choose the disk drive management, at least I think that's what its called. It will show you all the partitions on all the disks and will show unknown partition for all linux partitions. You can just delete those 'unknown' partitions and reclaim that space for windows, but unless you have Vista, you may have to use another utility to resize the original C: partition to the full amount. I would, like was previously mentioned, defrag C: at least once before expanding the image just as a precaution.
What Windows CD, are you talking about Windows XP CD or the Recovery CD? All I have is the recovery CD.

---

### Post by lwvmobile on 2008-05-01
What make and model is your computer? Some recovery disc are the Windows XP installation cd and some are special imaging software that copies an image or compressed files and just expands them. The second kind that I mentioned probably will not work. In that case, if you could get a hold of an XP cd from somebody just to use the recovery console feature you might be ok.

I'm trying to think of an easier way to go about doing this, but I can't right now. Nothing else really comes to mind than what has already been recommended.

---

### Post by Shadius on 2008-05-01
> **lwvmobile said:**
> What make and model is your computer? Some recovery disc are the Windows XP installation cd and some are special imaging software that copies an image or compressed files and just expands them. The second kind that I mentioned probably will not work. In that case, if you could get a hold of an XP cd from somebody just to use the recovery console feature you might be ok.

I'm trying to think of an easier way to go about doing this, but I can't right now. Nothing else really comes to mind than what has already been recommended.
The make is Compaq Presario 5410US Series 5000. Oh, man, I should've never tried to dual-boot Ubuntu. Now I'm doomed! :-(
The CD I have just says Recovery CD, and when I try to use that it just reboots without restoring the computer to the factory settings.

---

### Post by lwvmobile on 2008-05-01
Here is something that I found I am going to try out to see if it will work in this case.

[http://www.thecomputerparamedic.com/files/rc.iso](http://www.thecomputerparamedic.com/files/rc.iso)

It is a link to a recovery console ISO file that may come in handy if you don't have an actual XP CD.

But I am also thinking that if during you boot up that you don't see "Press ESC in 3 seconds" or a menu to choose the boot up then you may just be using the Windows XP bootloader by default anyway so It may be safe to go ahead and use the disk drive management console in windows to delete the linux partitions but that still doesn't expand the original C: unless you just want to make a new Windows partition and have an F: or something.

---

### Post by Shadius on 2008-05-01
> **lwvmobile said:**
> Here is something that I found I am going to try out to see if it will work in this case.

[http://www.thecomputerparamedic.com/files/rc.iso](http://www.thecomputerparamedic.com/files/rc.iso)

It is a link to a recovery console ISO file that may come in handy if you don't have an actual XP CD.

But I am also thinking that if during you boot up that you don't see "Press ESC in 3 seconds" or a menu to choose the boot up then you may just be using the Windows XP bootloader by default anyway so It may be safe to go ahead and use the disk drive management console in windows to delete the linux partitions but that still doesn't expand the original C: unless you just want to make a new Windows partition and have an F: or something.
Okay, wait, lemme go into Windows and see if I can get the Linix partitions.
Oh, here is a screenshot of my desktop when I open Gparted.

---

### Post by lwvmobile on 2008-05-01
Wow, Halt!
Question: How many hard drives do you have in that computer?

---

### Post by Shadius on 2008-05-01
> **lwvmobile said:**
> Wow, Halt!
Question: How many hard drives do you have in that computer?
One hard drive.

---

### Post by Shadius on 2008-05-01
This is what Disk Management looks like. It's a screenshot I took in Windows.

There are 3 Healthy Unknown Partitions, which I'm guessing the from Linux. So do I now just delete those 3 partitions and run my Recovery CD to restore my computer back to Factory Settings?

---

### Post by Shadius on 2008-05-01
Hey, are you still there?

---

