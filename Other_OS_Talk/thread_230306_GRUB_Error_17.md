---
title: "GRUB: Error 17"
date: 2006-08-05
forum: Other OS Talk
---

### Post by RAV TUX on 2006-08-05
SO I have been having a bit of a struggle here:

I tried installing several distros: Knoppix 5.0 for example & I got a GRUB Error 21

so I installed openSUSE 10:

I got a GRUB error 17

I found this in the Gentoo forum about error 17
> 
Ok, I have it working.. 
 
Seems I didn't take notice that when I installed Windows on my SATA drives that I needed to put a small partition on the ide drives in order for Windows to install.. I thought it was because Windows didn't like it's boot files on a RAID drive.. 
 
Well it seems (in my case anyhow) that this Western Digital RAID/SATA controller does not boot on my system.. so installing grub made no differance because it would not boot the system. I know, it sounds confusing as hell.. but I had to make a small /boot partition on an ide drive and *Presto it worked. 
 
So.. if you have a PCI SATA/RAID controller and no matter what you do.. you recieve "Error 17" ... try to put a /boot partition on an ide drive. 
 
Also I tried in my bios to tell the system to boot off of SCSI, but that wasn't happening either. So either way, on this mobo (Asus A7N8X-E Deluxe) I had to use ide. Why you might ask didn't I use the onboard SATA controller? Well for me.. with that SATA controller, I was plagued with tons of lockups and Irq 11 being disabled on bootup.. but the WD card it works great.. I have the Asus bios 1009 installed, and all efforts to install a newer bios where unfruitful to say the least.. 
 
Also I must thank the fellas in the #grub channel on irc for pointing me in the right direction.. they were very polite and helpful, and I wouldn't be back home in Linux on my main rig now it it were not for them. 
 
Thank you everyone 
 
Sincerely, 
 
TriKster Abacus  
I even tried using Lilo instead of GRUB,....no luck so I think I may make a small partition for GRUB and see if this works....

also I got this message when repairing SUSE:

> RAID configuration presented by the BIOS as a software RAID
/dev/sda
/dev/sdb

RAID configuration & data will be lost

refer to 

[http://portal.suse.com](http://portal.suse.com)

to learn how to migrate to a linux software RAID 
I don't know if this is related or not?

I now have two OS's on two hard drives and am unable to boot to either one

SUSE & Knoppix

---

### Post by siman on 2006-08-06
I also have a dual-boot winXP and dapper. After a lot of trouble, I now use this tool:

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

Just burn it to CD, and boot from it - it has a graphical setup / install.

---

### Post by richbarna on 2006-08-06
In this situation, I would boot the ZenWalk live cd (root access to all partitions.
Then got to the last OS that you installed and edit the GRUB menu list.

Using this guide :-
[http://www.ubuntuforums.org/showthread.php?p=1319395#post1319395](http://www.ubuntuforums.org/showthread.php?p=1319395#post1319395)

---

### Post by RAV TUX on 2006-08-06
Thanks for the help guys. In the end it had nothing to do with GRUB or Lilo but how my BIOS was set with RAID....

I actually solved this problem, refer to this thread:

[http://www.ubuntuforums.org/showthread.php?t=230361](http://www.ubuntuforums.org/showthread.php?t=230361)

It appears that the software that controls the harddrives on the BUS? system is incompatible with Linux.  There are two options to fix this I choose the easier option.

---

