---
title: "GRUB not showing up"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by meisetsu33 on 2008-08-18
So I have a hdd with Windows XP installed, and partitioned the rest of the hdd and installed Ubuntu 8.04 from a Live CD according to this guide:
[http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/)

Installation went well and everything, but when I start the computer, the boot menu (GRUB?) does not show up! It basically gives me no choice but to sit there and watch XP load.

My question is, how do I get GRUB to show up? I'm not too familiar with linux, so some detailed help would be appreciated.

Thanks!

---

### Post by alienexplorers on 2008-08-18
Try reading this post.  It may help you.
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

You could also boot your install Ubuntu CD.
Launch it in the preview without loading to disk section.
Wait for it to load.
Select from Applications>Acceseries>terminal
type in sudo grub
Enter: find /boot/grub/stage1
Enter: Root (XX,YY)  XX = disk  YY=partition
Enter: Setup (hdXX)  XX - disk
exit grub
reboot

---

### Post by cdtech on 2008-08-18
You will need to boot from the "Live CD".

Open a terminal and type:
```
sudo grub
 > find /boot/grub/stage1
 > root (**hd0,?**)
 > setup (hd**0**)
 > quit
```
The find will return a location of the stage1 file. This will be from the "/boot/grub" directory of the Ubuntu partition (probably (hd0,**?**). The "root" command should be whatever was returned from the find command, this sets up the GRUB bootloader to use the "stage1" from this partition. The setup tells GRUB to install the bootloader into the MBR of the primary (hd0) drive.

---

### Post by meisetsu33 on 2008-08-19
Thanks for your replies!

After typing in find /boot/grub/stage1 I got this message:

Error 15: File not found

Does this mean that Ubuntu wasn't installed correctly?? Its weird because I'm pretty sure I installed it correctly (according to that website)

---

### Post by cdtech on 2008-08-19
If your using the live cd, type "sudo fdisk -l" in a terminal (copy and paste). It can't see your drive. You may need to mount it first.

---

### Post by meisetsu33 on 2008-08-19
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4679608+   b  W95 FAT32
/dev/sda2   *         620       25840   190670760    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0d665ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d404d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sdc2           25497       25558      498015   82  Linux swap / Solaris
/dev/sdc3           25559       25564       48195   83  Linux
/dev/sdc4           25565       35290    78124095   83  Linux

Its the bottom hdd. Isn't this showing that it has been mounted?

---

### Post by meisetsu33 on 2008-08-19
Ok, so I fixed it and I got the GRUB to work!

But now it says Error 22: Cannot find partition or something like that (error number was 22).

How can I solve this?

---

### Post by alienexplorers on 2008-08-19
Read Thus:
> Quoted from the GNU/GRUB manual

    22 : No such partition
        This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

For example there might be a mistake in the menu.lst file in the partition number, if there is no such partition as specified in the 'root (hdx,y)' line.
example,
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
Look at your partitions with your partitioning software or run 'sudo fdisk -lu' in a terminal and make sure you have the partition number correct here in your menu.lst boot entry.

This is also the error that people often see after they delete their Linux partition but they still have that partition's GRUB's stage1 written in the MBR.

They can easily cure that by overwritting the existing GRUB IPL code with code for another bootloader in another operating system.
In other words either re-install GRUB or re-install Windows bootloader or some other bootloader or boot manager. In Super Grub Disk, go 'English Super Grub Disk'-->'Windows'-->'Fix Boot of Windows', or see my 'Un-install Page'.
Don't bother doing anything if a new (Linux) operating system will soon be installed, the new operating system will install a new bootloader and cure this error automatically.

If there is another operating installed in the computer, re-writing the bootloader'e MBR code for that operating system's bootloader and overwriting the now useless GRUB code will cure the problem. This can be easily done with Super Grub Disk.
1) Re-install a GRUB to MBR from another Linux
2) Re-install a Windows Bootloader to MBR.
     (These two above items are both options in Super Grub Disk that can be selected and SGD will do it for you).

I got GRUB error 22 myself one time after doing quite a lot of work to the partitions in my wife's computer. I tried to fix the boot of grub with an older version of Super Grub Disk, not realizing her partition numbers had been unexpectedly changed somehow by disk partitioning software.
I installed grub from the wrong partition by accident.
Later I found out the real cause of all the trouble was a dirty DVD/CD-ROM drive that caused read problems from my partitioning CD.

 Anyway I got  Grub Loading Stage1.5
       Grub Loading Stage1.5
       Grub Loading Stage1.5
       Grub Loading Stage1.5...and so on, scrolling endlessly down the monitor.

I couldn't even boot with Super Grub Disk's 'English Menu'-->'Gnu-Linux'-->Boot Gnu/Linux Directly'.
After much mumbling and head scratching and trying various ideas I decided to run a file system check with my GParted -- LiveCD. When that was done I clicked on the triangular buttons for a report and found that GParted LiveCD had repaired quite a few problems in that filesystem.

So tried again, this time from the Super Grub Disk menu I pressed 'c' for a Super Grub Command Line Interface, and booted manually using a direct kernel style boot
The operating system booted and I was able to re-install Grub to MBR, and configure menu.lst with new partition numbers.

GParted LiveCD saved the day for me. I didn't have to sleep in the doghouse after all! :)
The lessons here are,
1. keep my CD-ROM drives clean, and
2. to try a filesystem check if I am having unusual troubles booting.

It's easy to run a file system check on any file system with a GParted -- LiveCD, just boot with the CD and click on the filesystem (partition) to be checked and click 'check'.
Click 'Apply' (on the toolbar), and then 'Apply' again (in the confirmation box).
Then wait a few minutes.
When it's finished it's a good idea to click on the arrow shaped 'Details' button in GParted to expand the output box. Make sure you click on all the subsequent arrow buttons too, so you will expand it all fully so you can read the report and see what was done to fix your file system.
See my File Systems and Mounting Page for more about file system checking in Ubuntu.

---

### Post by meisetsu33 on 2008-08-19
So I have three partitions right now:
/ , /boot, swap

Is the root (hdx,y) suppose to be set to the / partition and not the /boot?
Right now I set it to the /boot partition...

Also, a drive of sdc would be hd2, correct?

---

### Post by alienexplorers on 2008-08-19
Try setting it up under /.
And you are correct that hdc would be hd2.

Instead of a boot directory you should have made a home directory of about 10-15 Gig.

---

### Post by meisetsu33 on 2008-08-19
So it seems that when I try to set root (hd1,3) which is the / directory, setup doesn't work, and when its (hd1,2) setup goes through but result is a failure.

I'm just going to reinstall ubuntu, but how should I go about doing it? What do you mean by a home directory instead of /boot? Don't I need a /boot for a successful installation?

---

### Post by alienexplorers on 2008-08-19
A boot directory is not required.  A home directory is where all your program options are installed.  If you ever have to reload Ubuntu you would format / and DO NOT FORMAT /HOME.  This leaves all your important data on your system.

Donnie

---

