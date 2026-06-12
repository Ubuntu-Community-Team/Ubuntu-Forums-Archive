---
title: "Grub won't load on multiboot system"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by Jontydog on 2013-05-20
Hi all new to Linux and having a dabble. My problem is this I have a multi boot machine Windows 8,7 and XP all on different drives and have installed Ubuntu 13.04 which caused my machine not to boot it just went to the grub rescue command. I ran the boot repair start up disc which didn't fix the fault but gave me this pastebin entry [http://paste.ubuntu.com/5681100/](http://paste.ubuntu.com/5681100/) I have managed to get my machine running again using the windows 8 fixmbr but would still like to run Ubuntu to learn how to use it. 

Any help greatly appreciated :D

---

### Post by oldfred on 2013-05-20
While it shows a Linux partition on sdd, it seems like it cannot mount it. Was that your install? As you also seem to have an install in sdi which looks like a removeable drive. Can you boot sdi?
You may need to run fsck on sdd1.

Confirm that drive is still sdd when running from liveCD first.
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdd1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdd1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdd1

    

You have let Boot-Repair install grub to every MBR, I would keep a Windows boot loader in the MBR of every Windows drive. But as configured you only have one Windows boot drive.

Windows can only boot from one active partition which is the BIOS boot drive and the partition with the boot flag. So all your Windows are booting from sda1. You cannot currently boot sdb or sdc separately. I would create Windows repair CDs and repair sdb & sdc. You have to set BIOS to boot each drive before repair and not let it update other installs.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Jontydog on 2013-05-21
Cheers will have a go at this tomorrow morning will let you know how I get on :-D

---

### Post by William D. on 2013-05-21
I also have Windows 7 and Windows 8 and Ubuntu installed on one computer.   Three SEPERATE Hard Drives.   I do not use Grub, never installed it.  When I built the Compuer I put in the First Hard Drive (ssd) and installed Windows 8. After I got Windows 8 up and running ok. I turned off the compuer and disconnected the SSD and connected the second HD and installed Windows 7.  Did the same thing and on the third HD I installed Ubuntu. Turned off the compuer and reconnected the three Hard Drives.  In the BIOS you can select which hard drive is primary.  I set the SSD with Windows 8 as Primary so when I turn on the comptuer and dont touch anything Windows 8 starts.   However, if right after turing on the PC I Press the F12 Key a menu comes up with a list of the drives and I just select which one to boot off of.   That way the opearting systems do not interact with each other like what happens with GRUB.

---

### Post by Jontydog on 2013-05-23
What I actually did was install from the Ubuntu 13 Live CD and let it do its own thing. I was given the option to install ubuntu on its own or alongside windows 8 so I chose to install alongside and assumed everything would be ok. Using the Live CD I have 2 drives with all the linux files installed from failed installations which don't show up in windows. Will continue to have a look this morning and sort things out. Am pretty good with Windows stuff but a complete novice with Linux so am learning all the time :D

---

