---
title: "Fsck"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by czgirb on 2013-03-31
Where is the place which I can learn about **FSCK** (**File System Consistency Check**) include how to run it?
Cos for my district, **power-outage** is often happen.

**Power-Outage = Power Failure**

---

### Post by sudodus on 2013-03-31
You can start by searching the internet with the search string ***fsck tutorial*** or something similar. I found several interesting pages that way, and you can browse through them and read carefully what is most interesting for you.

There are also the built-in manual pages. Start with ```
man fsck
``` At the end of the man page you will find references to similar programs, e.g. e2fsck and fsck.vfat. But remember that it is better to use Windows to repair Windows file systems (FAT and NTFS).

To check and repair ***ext*** file systems I boot from another drive, unmount the partition to be repaired and run
```
sudo e2fsck -f /dev/sdxy
```
where x is the drive letter and y is the partition number, typically /dev/sda5.

But it is much better to prevent file system corruption with battery backup (UPS).

> What is a Battery Backup?:

A battery backup, or  uninterruptible power supply (UPS), is primarily used to provide a  backup power source to the parts in the computer case, the monitor, and any other device plugged in to the battery backup.

***The simplest solution is to use a laptop*** with enough battery power to perform a soft shutdown (finish writing operations and close files). A few minutes is should be enough for that. And for desktops and servers you need an external equipment. There are lots of such equipment on the market, and you can choose what fits your purpose. Is it enough to perform a soft shutdown, or do you need power enough to run during the whole power outage (or at least most outages, say power for two hours)?

---

### Post by czgirb on 2013-04-02
Thank you ... I do a search and found: ***FSCK** should always be run in **single user mode** otherwise the data can be corrupted.*
**Single User Mode**? What is this? How can I run into **single user mode**?

Some friends of mine, said that FSCK should be runned by using **LiveCD**?
Is there any difference between **LiveCD** and **single user mode**?
Which one is right?

**PS:**
SORRY ... my ubuntu's knowledge is very-very poor ... please be patient.
**Thank you**

---

### Post by Nutster on 2013-04-02
Single User Mode:  When you first start the computer, you may see the GRUB menu that lets you choose your operating system.  From there, choose **(recovery mode)**.  This will put you into single-user mode.  In single-user mode, you are only using one text interface on the computer and many services and applications are not running.  It is intended for maintenance work.

In order to run **fsck**, the file system you want to test must not be mounted.  Even in single-user mode, the root file system must be mounted, so if that is the file system you want to test, you will have to  boot from a LiveCD/LiveDVD.  Generally, this is the disk that was used to install your operating system.  Put the disk in and boot the computer.  Choose **Try Ubuntu** (you don't need to reinstall the operating system, I hope) and then press Ctrl+Alt+F1 to get a command line.  Enter:
```
sudo ls /dev/sd*
sudo fsck /dev/*drive*
```
where *drive* is the drive you want to check.  The first line gives you a list of your hard drive partitions for modern SATA drives.  If you are using another type of drive, the file names will be different.  

Another thing you could try is to put the file [font=Courier New]forcefsck[/font] in the root directory of the partition then reboot the computer.  Just before the file system is mounted, the operating system will run **fsck** on the file system.  After the file system is mounted, that file will be removed.  This does not work with every file system.  I have had mixed results with this one.  An easy way to put the needed file on the file system, is to touch it.
```
sudo touch /forcefsck
```
Use **sudo** because the root directory can not normally be written to.  This will put an empty files called [font=Courier New]forcefsck[/font] in the root directory of the main partition.  If you have other writable file systems mounted, do the same thing, but the file must go at the root of each file system.

---

### Post by MoebusNet on 2013-04-02
I found this:

> Please download and burn the Ubuntu 12.04 Desktop ISO to a CD-R. Then set your BIOS to boot from it, and boot the Live-CD.

Once in there, open a terminal with Ctrl-Alt-T, and type sudo fdisk -l to see what the hard disk was mounted as.

Then run sudo fsck /dev/sda1, etc. for all partitions on that hard disk.

That should hopefully fix the problem.

at:

[http://askubuntu.com/questions/161153/ubuntu-12-04-takes-too-long-to-boot](http://askubuntu.com/questions/161153/ubuntu-12-04-takes-too-long-to-boot)

This is for running fsck from a Live-CD.

---

### Post by oldfred on 2013-04-02
I normally suggest a liveCD/DVD/Flash drive so partitions are not mounted.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

