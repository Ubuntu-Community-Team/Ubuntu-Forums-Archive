---
title: "format hard drive for reinstall of windows"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by cbivins on 2008-05-25
How can i format my hard drive so i can reinstall windows. The formatting program on my Vista disk doesn't like my ubuntu, and i want to switch to a dual boot. any ideas?

---

### Post by sharks on 2008-05-25
do u want to format windows or the entire harddisk?

---

### Post by cbivins on 2008-05-25
Well, i think i have to format the hard disk to install windows. (all i have on here now is ubuntu)

---

### Post by sharks on 2008-05-25
if u want to format the partition on where u have installed windows(C:\) ,just put the windows boot cd on the drive and it will give u an option where u can format the windows partition and it will not affect other windows partition if u have one.

---

### Post by hyper_ch on 2008-05-25
but windows will overwrite the bootloader so in order to get dualboot again you'll need to reinstall grup (from Supergrub Disk)

---

### Post by cbivins on 2008-05-25
When i do that, the windows formatter says that it doesn't recognize the format. I know that sounds stupid, but it's true. Is there any way to format a drive so that windows can reformat it?

---

### Post by sharks on 2008-05-25
can u post a screenshot of ur partiton through gparted?

---

### Post by thisiam on 2008-05-25
well it sounds like you want to start from scratch and dual boot.
use your windows install cd to partition and install, leave space unallocated so you can install ubuntu onto from the live cd.
thats about it, the forums will show what else needs to be done.

---

### Post by cbivins on 2008-05-25
sorry, i have no idea how to do that. I have just been booting off of the reinstall disk that came with my computer and following the instructions for formating. If you give me a minute, i can tell you exactly what it says, but i will have to reboot first.

---

### Post by cbivins on 2008-05-25
See, that's the problem. i can't get the stupid windows disk to format my hard disk.

---

### Post by warp99 on 2008-05-25
> **cbivins said:**
> How can i format my hard drive so i can reinstall windows. The formatting program on my Vista disk doesn't like my ubuntu, and i want to switch to a dual boot. any ideas?

You can use gparted available on the Ubuntu install disk or you can download the gparted LiveCD or LiveUSB version here:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You need to partition your drive so that the first partition (hd 0,0) will be the install target otherwise you'll overwrite your Ubuntu install. Once that is done you can install Windows. After the install you now have a choice to use either the Vista Boot Manager or overwriting the MBR with GRUB which was installed with Ubuntu.

Instructions for using the Vista Boot Manager are here:

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

Instructions for recovering and overwriting the Windows MBR with GRUB are here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29%7C%28install%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29%7C%28install%29)

The second link also has some information on boot management from Vista or from a third party manager instead of using Grub. Hope this helps.

Edit:

Gparted can partition the drive for NTFS so you can install Vista without any problems.

---

### Post by cbivins on 2008-05-25
This is exactly what i needed. When i got to the part where i had to select a partition to format, it said that windows can't format this partition because it is not NTFS formatted. Your links should help me figure this out. Thanks a bunch.

---

### Post by binary00mind on 2008-05-25
[COLOR="DarkRed"][/COLOR][LEFT][/LEFT]Not enough info on your layout, partition-wise, where you booting from now ? What partition and do You use Grub or Lilo ? Windows never liked Linux.
They play dumb, that some unknown OS is there. Forget about using Windows console, to do the job.Why would You want to re-install Windows.
The new Windows find your history from MBR. In seconds. If You insist, then use a third party partitioning utility.
There are freewares but for experts. sharewares cost money. I use Partition Magic (#8 the last from PowerQuest )I always did it out of floppies. So Windows had no knowledge about it.
Always do it, without Prior Windows knowledge. Ambush them.
Try to make a peace with Windows and find some freeware, dual booting utility. 
Here is the place to go. [http://majorgeeks.com](http://majorgeeks.com)
You find tons of useful stuff there and they have a forum like here. With Linux Group. Good place to find common problems.

---

