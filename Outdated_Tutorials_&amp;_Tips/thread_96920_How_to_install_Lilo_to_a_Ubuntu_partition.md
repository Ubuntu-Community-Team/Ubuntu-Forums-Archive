---
title: "How to install Lilo to a Ubuntu partition"
date: 2005-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Herman on 2005-11-29
INSTALL LILO BOOT LOADER TO UBUNTU PARTITION
(So you can boot with GAG boot manager).
GAG boot manager link:  [http://gag.sourceforge.net/]("http://gag.sourceforge.net/")
The GAG bootmanager does not need to disturb your MBR and can be used from a floppy disk or CD-ROM without affecting your original MBR that boots Windows. You can install GAG to your MBR later sometime if you want.
GAG boot manager is 'operating system independant', so you can install and uninstall operating systems without losing your boot.

1. Boot the computer with the 'Breezy' install CD.
2. Complete the questions for the first stage of the installation as if you were installing, until '[!!] Partition Disks' is reached.
3. Select 'Manual Partitioning'.
4. Select your Ubuntu partition.
5. (a) change mount point from /media/hda4 (or whatever) to /.
(b) change 'bootable' off to 'bootable' (a progress bar will display).
(c) choose 'done setting up the partition'.
(d) choose 'finish partitioning and write changes to disk.
6. Sign says: 'If you continue, changes will be written to disk, etc,''Continue?'choose 'Yes'.
7. A red warning screen appears, saying 'Not installing to unclean target' choose 'continue'.
8. A second red warning screen says 'Install the base system failed' choose 'continue' again. (we don't care!).
9. This sees you back in the 'Ubuntu Installer Main Menu', and once there you can scroll down to 'Install Lilo boot loader to a hard disk'.
10. 'Install Lilo to target' '/dev/hda: new Ubuntu partition' (not your MBR if you are doing this for GAG). A progress bar should display as Lilo gets installed.
11.A red warning screen appears, saying 'Not installing to unclean target' choose 'continue'.
12. A second red warning screen says 'Install the base system failed' choose 'continue' again.
13. Then you will be back in the 'Ubuntu Installer Main Menu' again, but be careful not to press 'enter' on anything you don't want,but scroll down immediatley to 'Abort Installation'.
14.Exit the installer.
15.Remove the install CD from your CD drive quickly as soon as you can before it boots from it again!


These instructions are taken from vnbuddy2002's famous howto on restoring GRUB to MBR, and I have only modified them a little bit. (I hope vnbuddy2002 won't mind, without his howto to start with, I wouldn't have been able to do this).

I have tested this twice on a computer with Windows98SE and two installations of 'Breezy'. (Triple-boot). I already had GRUB working alright before doing this. The results were that my computer still boots all three operating systems as it did before using GRUB, plus I have configured a GAG floppy disk, and all three operating systems also boot from the GAG floppy disk, using Lilo for the two 'Breezy' installs I am runnning. So to make it plainer; installing Lilo to my Ubuntu partitions has not affected Grub, and using GAG from a floppy doesn't change the MBR either. (So this is a safe thing to do, and can be done anytime.) (Herman)

Edited 3rd Dec 05, I had trouble doing this on an installation with a seperate partition for home. I wouldn't recommend people with home on a seperate partition try this, I'll test it some more and see if it's a problem that always happens or not. It made the home partitition inaccessable for some reason.

---

