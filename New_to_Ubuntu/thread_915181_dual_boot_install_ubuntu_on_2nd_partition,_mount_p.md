---
title: "dual boot: install ubuntu on 2nd partition, mount point, I'm stuck"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by crowhill on 2008-09-09
Hi there !

I have a little problem with the setup of my dual boot Windows XP/Ubuntu. I seem to have forgotten how to do it since, once, I was able to ...

The situation that I'm facing is the following:
Before installing WinXP I formatted my entire 80 G harddrive. Then, I chose a 50 G partition for the WinXP installation, which worked well. Now, I want to install Ubuntu 8.04 (Hardy Heron) on the remaining 30 G.

The problem is as follows:
When I start the installation of Ubuntu, the manual installation would choose the 50 G partition for Ubuntu, giving WinXP less space and leaving the 30 G partition untouched. When I choose the manual installation procedure, it seems that I have to divide the 30 G partition in a small swap partition and a bigger ext3 partition. I did that using the Gparted from the live CD. However, when I restart the manual installation, the partition editor doesn't let me assign a mount point to the swap partition. I can make the the ext3 to be the home partition, but the drop down window for mount points is grayed out if it comes to the swap partition. In conclusion, the installer keeps telling me that I have no root partition. 

My idea:
I read somewhere, that this has to do with the numbering of the partition, the hierarchy so to speak. However, I didn't understand the details so I don't know whether that is of any help.

Some advice would be very welcome.

Ah, could it be that I can use the entire HD for WinXP and let the Ubuntu installer resize this partition for Ubuntu? Does this work or is it putting the WinXP installation in danger?

Thanks a lot in advance,
cheers,
crowhill.

---

### Post by Rocket2DMn on 2008-09-09
Since you pre-partitioned, you assign the mountpoint / to the ext3 partition that you created.  Then you have a swap formatted partition - this has no mount point (swap doesn't actually mount anywhere on the filesystem!).
I think your setup is fine, don't resize the Windows partition.
Ex: 
sda1 - ntfs (this is windows) - mount at /media/windows or don't specify any mount point (but don't format it!)
sda2 - ext3 (this is the root partition) - mount at / (requires format)
sda3 - swap - no mount point (format optional if swap space is already there)

---

### Post by BenAshton24 on 2008-09-09
why not choose option "use largest available disk space" or something like that, sorry if it doesn't exist, I've installed stack loads of distros and it gets confusing sometimes :P

Hope this helps (though i doubt it will) Ben. :D

---

### Post by crowhill on 2008-09-11
> **Rocket2DMn said:**
> Since you pre-partitioned, you assign the mountpoint / to the ext3 partition that you created.  Then you have a swap formatted partition - this has no mount point (swap doesn't actually mount anywhere on the filesystem!).
I think your setup is fine, don't resize the Windows partition.
Ex: 
sda1 - ntfs (this is windows) - mount at /media/windows or don't specify any mount point (but don't format it!)
sda2 - ext3 (this is the root partition) - mount at / (requires format)
sda3 - swap - no mount point (format optional if swap space is already there)

Hi there!

Thanks a lot for this reply. Mounting the ext3 partition at / rather than /home did the trick. Everything worked perfectly.

Have a wonderful day,
cheers,
crowhill.

---

