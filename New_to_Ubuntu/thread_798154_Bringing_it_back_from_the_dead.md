---
title: "Bringing it back from the dead"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by TattooedRunes on 2008-05-17
Ok, so I've been running a dual boot, Vista and Ubuntu... today I decided I was fed up with Vista and I was going to downgrade to winXP/SP2.  To make a long story short, I messed up along the line and lost everything (luckily I back up all my pertinent stuff beforehand).  

Luckily I still had the disk for Gutsy because it's the only thing that seems to work right now.  

I've got the disks for XP and for Leopard and ideally I'd like to set up a triple boot, but unfortunately they're not working.  The windows disk tells me it can't find a hard drive on this computer, and the Mac disk won't even load on startup.

If it helps, computer stats:
HP Pavilion dv9000
Intel Centrino Dual (1.8's I think)
2G Ram
nVidia GeForce Go 7600
160G WD Scorpio HD


Anyone have any thoughts or suggestions?  Help!?!

---

### Post by Inxsible on 2008-05-17
If its not too much hassle, I would say installing them all over would be the best bet. Start with installing XP. Then make space for Mac (I am not sure if all your hardware will be supported..) Then install Ubuntu last, which will give you a nice GRUB to select which OS you want to boot to.

---

### Post by TattooedRunes on 2008-05-17
> **Inxsible said:**
> If its not too much hassle, I would say installing them all over would be the best bet. Start with installing XP. Then make space for Mac (I am not sure if all your hardware will be supported..) Then install Ubuntu last, which will give you a nice GRUB to select which OS you want to boot to.

Right, sure, of course... although what I was saying was that I've been trying to do that but so far I've been unsuccessful because of the problems I listed above.

---

### Post by jrusso2 on 2008-05-17
If Xp is not finding the hard drive it probably has a SATA hard drive which was invented after XP.

If your XP has SP2 slipstreamed this adds support for some sata drives.

If that is not working its possible to add the driver during the xp install but this usually is from a floppy which does not help if you don't have one.

I think there is a way to do this with a cd or usb key but you would need to look up how as I have not had to do this before.

---

### Post by Inxsible on 2008-05-17
Can you boot into your Ubuntu install?

Post the output of ```
sudo fdisk -l
``` -l is lowercase L and ```
df -h
``` If you cannot, then put in the Gutsy live Cd and then perform the commands.

---

### Post by TattooedRunes on 2008-05-18
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x495d01ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux

=====================================================================================

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1013M   16M  998M   2% /lib/modules/2.6.22-14-generic/volatile
tmpfs                1013M   16M  998M   2% /lib/modules/2.6.22-14-generic/volatile
varrun               1013M   96K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   68K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
tmpfs                1013M   12K 1013M   1% /tmp

ok... this represents what my drive looks like right now as one big unformatted partition while I run the Gutsy live CD.

---

### Post by TattooedRunes on 2008-05-18
> **jrusso2 said:**
> If Xp is not finding the hard drive it probably has a SATA hard drive which was invented after XP.

If your XP has SP2 slipstreamed this adds support for some sata drives.

If that is not working its possible to add the driver during the xp install but this usually is from a floppy which does not help if you don't have one.

I think there is a way to do this with a cd or usb key but you would need to look up how as I have not had to do this before.

Yeah, you're right.  It's the SATA thing... damn.  After cracking my laptop open, I am realizing that it's set up for SATA only.

When I plug in my external hard-drive the Windows disk wants to format that (its an older WD Scorpio ATA mounted in a Rocketfish caddy), but unfortunately that drive is full of all of my backup files and such so I'm not going to be willing to overwrite it.

---

### Post by TattooedRunes on 2008-05-18
Ok, so I found the recovery disks (XP/SP1) for my old laptop and they didn't seem to mind that my new laptop had a SATA hard drive, and it installed properly (or so I thought).  Currently, I've got an ntfs partition with XP on it and an ext3 running as root with Gutsy (and 1G for swap).  Now Ubuntu and Grub recognize that there is a Windows XP Home Edition system, but every time I try to load windows from the Grub, it gets about 4 seconds into things and I get the blue screen of death.  Help!

---

### Post by PmDematagoda on 2008-05-18
> **TattooedRunes said:**
> Ok, so I found the recovery disks (XP/SP1) for my old laptop and they didn't seem to mind that my new laptop had a SATA hard drive, and it installed properly (or so I thought).  Now Ubuntu and Grub recognize that there is a Windows XP Home Edition system, but every time I try to load windows from the Grub, it gets about 4 seconds into things and I get the blue screen of death.  Help!

If you used recovery discs from a different laptop then that might be the reason, or perhaps XP SP1 may not play well with your hardware. Perhaps you aught to ask your PC vendor or maybe Microsoft themselves since you do have genuine XP don't you?

---

### Post by TattooedRunes on 2008-05-18
They're genuine in that I own them and they came with the laptop that I owned before I bought this one.  I'm not sure Microsoft would approve of my use of them however, and certainly, my vendor (HP) would not either.  Even though the disks are for an older HP system, given how proprietary HP is, I'm sure they wouldn't take kindly to my tamporing with the "perfection" which is their system running Vista.

Anyway, I now have a new error message at startup with Windows.

Windows could not start because the following file is missing or corrupt:
\WINDOWS\system32\config\SYSTEM

Has anyone encountered this before?   Any advice/suggestions?

---

### Post by Canis familiaris on 2008-05-18
Mac will not run ordinarily in a HP machine. Apple usually locks its OS to its own PC. There are ways to run Apple Mac OS X on a standard PC but I can't discuss them because they are illegal even if you own a legal copy of Mac OS X Leopard.

---

### Post by TattooedRunes on 2008-05-18
> **Anurag_panda said:**
> Mac will not run ordinarily in a HP machine. Apple usually locks its OS to its own OS. There are ways to run Apple Mac OS X on a standard PC but I can't discuss them because they are illegal even if you own a legal copy of Mac OS X Leopard.

Yes I am beginning to see that problem... right now I've abandoned the Leopard idea for the time being, and I'm focusing purely on the project of getting a xp up and running.

---

### Post by JKyleOKC on 2008-05-18
Have you considered installing Ubuntu to use the entire drive (initially, at least) and then installing a virtual machine such as VMWare or VirtualBox, putting XP from your CDs into the virtual machine?

It will be slightly slower than a native XP install, but not a lot. I'm running XP in a VMWare setup under Xubuntu, on a box that natively does not have enough resources for XP. The Ubuntu layer handles all of the physical interfaces, so the SATA/PATA problem will vanish. You might even be able to run Leopard in a second VM...

---

### Post by lswest on 2008-05-18
Just wanted to say that running a Mac OS on a non-apple hardware config or in a VM is against their license agreement (at least, last time i checked).  Chances are it won't run anyways.

*EDIT* ah, didn't realize someone had said something similar before, sorry.  And about XP on an HP laptop, did you delete the original NTFS partition?  Try creating an NTFS partition at the front of your hard drive setup, it may work then.  (use GParted off the liveCD of Ubuntu if you need to).

---

### Post by hovzio on 2008-05-18
As far as I know your not gonna be able to use a recovery disk for a pc other than the one that it came  with.(Brand type etc..)

---

### Post by TattooedRunes on 2008-05-18
> **JKyleOKC said:**
> Have you considered installing Ubuntu to use the entire drive (initially, at least) and then installing a virtual machine such as VMWare or VirtualBox, putting XP from your CDs into the virtual machine?

It will be slightly slower than a native XP install, but not a lot. I'm running XP in a VMWare setup under Xubuntu, on a box that natively does not have enough resources for XP. The Ubuntu layer handles all of the physical interfaces, so the SATA/PATA problem will vanish. You might even be able to run Leopard in a second VM...

this might be a good idea... maybe I'll give that a try

---

### Post by johnn1949 on 2008-05-18
Unfortunatley you only own the xp for the system that it was installed on originally.  You can't legally install it on another computer.

I would call microsoft and see if they will let you downgrade (their words,not mine) the Vista to XP.  Then you can install Ubuntu.

---

### Post by prshah on 2008-05-18
> **TattooedRunes said:**
> Yeah, you're right.  It's the SATA thing... damn.  After cracking my laptop open, I am realizing that it's set up for SATA only.


In the BIOS, you will have an option to treat the SATA as legacy IDE; the exact option varies from BIOS to BIOS, but look for something related to "SATA" with options for "Legacy" or "IDE Compatibility mode" or so on.

You can toggle the setting, install XP, and once it's running fully with all updates, change it back to the original to get full SATA performance.

---

### Post by TattooedRunes on 2008-05-18
> **prshah said:**
> In the BIOS, you will have an option to treat the SATA as legacy IDE; the exact option varies from BIOS to BIOS, but look for something related to "SATA" with options for "Legacy" or "IDE Compatibility mode" or so on.

You can toggle the setting, install XP, and once it's running fully with all updates, change it back to the original to get full SATA performance.

Yay, this actually worked... thanks so much.  Now I've got XP installed!  All I have to do is get it up to speed.  Thanks again.

---

### Post by Canis familiaris on 2008-05-19
> **prshah said:**
> In the BIOS, you will have an option to treat the SATA as legacy IDE; the exact option varies from BIOS to BIOS, but look for something related to "SATA" with options for "Legacy" or "IDE Compatibility mode" or so on.
You can toggle the setting, install XP, and once it's running fully with all updates, change it back to the original to get full SATA performance.

It would come at the cost of performance penalty. Isn't it? The OP wouldn't be able to gain performance advantage offered by SATA!
I think the OP should consider installing XP SP2.

(EDIT): OK I didn't read your post fully. You asked him to update and change back.

---

