---
title: "Dual Boot installation problem"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by jhughs on 2012-11-08
I’m completely new to Linux and Ubuntu, so please keep that in mind when responding.
   
  After a few trial runs with the Ubuntu 12.10 LiveDisk, I decided to take the leap and load it as a dual-boot onto the old Dell computer (the same one I’d been testing on) that has two hard disks.
   
  It seemed to load fine, but when I reboot it fails out and stops at “grub rescue”.
   
  Trying to fix from there I didn’t get very far as shown here:
  Error: no such device: 4514b2af-d3e6-46ad-b966-8b9fe1b74c9a.
  Grub rescue> set
  Prefix=(hd0)/boot/grub
  Root=hd0
  Grub rescue> ls
  (hd0) (hd0) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos5) (hd1,msdos1) (fd0) {yes, it has a floppy drive}
  Grub rescue> ls /
  Error: unknown filesystem
   
  And then anything I try with ls after that gives “unknown filesystem”, so I’m stuck.  (Any idea why I'm getting "unknown filesystem"?)
   
  When I rebooted with the LiveDisk, it appears Ubuntu got loaded onto the second hard disk (HD1) instead of HD0.  (Which is a pity because I cleared space on HD0.)
   
  So I figure I have two paths here and am looking for advice:
  [FONT=Calibri]1)      [/FONT]Try to reset the root and boot prefix to HD1 (but I’m not sure which partition); or
  [FONT=Calibri]2)      [/FONT]Reload Ubuntu and manually force it onto a partition on HD0 (so I need to learn how to do that).
   
   
  Thanks in advance for your advice (and moral support).

---

### Post by oldfred on 2012-11-08
Welcome to the forums.

Lets see where everything is at.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

If you have two drives it is best to use manual install or Something else. You then do have to choose (& create if not already created)  / (root)  & swap partitions  and possibly /home. I prefer to partition in advance with gparted, then use manual install as I know where it is going to go. 

Install to external drive 12.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)

---

### Post by jhughs on 2012-11-08
Thanks oldfred.

I really appreciate the link to the BootRepair site.  I'd seen references to BootRepair but hadn't found the ISO version.

Unfortunately, I ran the repair and got the same result. 

Over the weekend, I'll try your second suggestion of doing the manual install to force it onto HD0 instead of going to HD1 (don't really understand why that was the default, but this is forcing me to learn, so that's good).

If it helps, here's the boot info: [http://paste.debian.net/207633](http://paste.debian.net/207633)

---

### Post by oldfred on 2012-11-08
Boot repair attempted to reinstall grub to both drives and they boot refer to partition 72. Not sure if boot script error with grub2's newest version or more likely grub just is not installed correctly.

Yours in not a large drive, but we have seen issues only with some BIOS where grub cannot find its own files when / partition is large (yours is not) or is beyond 100GB which yours is. Then a small /boot partition inside the 100GB seems to work.

Have you reviewed BIOS settings. Some issues like fast boot, drives set to IDE not large or LBA can also cause issues. IDE may be emulating an old issue where drives could not boot beyond 137GB.

Since install looks ok otherwise you could also try Supergrub. It boots some systems with grub issues, so then you can reinstall grub from inside your install.
[URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"]http://www.supergrubdisk.org/
http://www.supergrubdisk.org/wiki/Main_Page
http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk

[/URL][]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by jhughs on 2012-11-11
oldfred - Thanks.  You put me on the right track to figuring this out.  Gparted showed me that sda has bad sectors and should be replaced.  So Ubuntu was being loaded on sdb and probably isn't working for the reasons you mentioned (being loaded past 100GB).  So I need to decide if I just replace the disk or look for a newer used computer and make it a full Linux box.  Thanks again.

---

