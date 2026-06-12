---
title: "System sees Windows 7 which doesn't exist"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by Beardedturtle on 2012-11-29
Why is Ubuntu 12.04 thinks that my spare/backup HDD has Windows 7 on it? i never ever installed Win7 just using it for backup.

---

### Post by pqwoerituytrueiwoq on 2012-11-29
did you backup everything on a windows 7 partition?

---

### Post by Beardedturtle on 2012-11-29
> **pqwoerituytrueiwoq said:**
> did you backup everything on a windows 7 partition?
No I copy and pasted to it, file system is NTFS. I only copied programs, movies and music.

---

### Post by deadflowr on 2012-11-29
Where is it telling you that it's Windows 7?

Are any Windows files on the disk?

Where'd you get the disk?

A stab in the dark, I'd say its probably just the label.

---

### Post by Beardedturtle on 2012-11-30
> **deadflowr said:**
> Where is it telling you that it's Windows 7?

Are any Windows files on the disk?

Where'd you get the disk?

A stab in the dark, I'd say its probably just the label.
Sometimes Ubunntu crashes and trys to load windows and says it is missing the boot files I will then go to the bios and see it has the HDD as the first boot option instead of the SSD...(SSD is Kingston Hyper X whole lot better then my old OCZ drive), Oh and flashed the SSD so there would be no trace of Win7.

---

### Post by haqking on 2012-11-30
> **Beardedturtle said:**
> Sometimes Ubunntu crashes and trys to load windows and says it is missing the boot files I will then go to the bios and see it has the HDD as the first boot option instead of the SSD...(SSD is Kingston Hyper X whole lot better then my old OCZ drive), Oh and flashed the SSD so there would be no trace of Win7.

I suspect because the drive is NTFS, and perhaps there is an old MBR on there, make sure you delete the MBR on it too.

---

### Post by shaktiman1234 on 2012-11-30
Beardedturtle
Please mention your problem in question Title, That will be a lot helpful for other people in the forum.

---

### Post by forrestcupp on 2012-11-30
I can't believe no one has answered this correctly yet. I would say that it's because your computer came with a small recovery partition to reinstall Windows 7 if you need to. If you don't want that on there, you can always use GParted to delete it and expand your primary partition. If you do that, just make sure to back up your files and be careful to know for sure that that is what you're doing.

---

### Post by sffvba[e0rt on 2012-11-30
***Moved **to Absolute Beginners Section.*

Also renamed, slightly better but not perfect I am sure.


404

---

### Post by haqking on 2012-11-30
> **forrestcupp said:**
> I can't believe no one has answered this correctly yet. I would say that it's because your computer came with a small recovery partition to reinstall Windows 7 if you need to. If you don't want that on there, you can always use GParted to delete it and expand your primary partition. If you do that, just make sure to back up your files and be careful to know for sure that that is what you're doing.

Thats is true, though I wouldnt think it would be seen as it is not marked as active and is a hidden partition usually but may be the case.

Either way gpart the whole thing and make sure any MBR is removed along with hidden partitions

I have seen with NTFS USB drives at least if BIOS is set to boot from USB and it sees the drive even though it has no OS on it it will error with "cannot find NTLDR" indicating it is looking for windows

---

### Post by oldfred on 2012-11-30
Post the link to this as then we can easily see why grub is finding Windows:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by forrestcupp on 2012-11-30
> **haqking said:**
> Thats is true, though I wouldnt think it would be seen as it is not marked as active and is a hidden partition usually but may be the case.
They're always visible from GParted, but I've also had them visible from Grub, too. Also, sometimes they show up from within Nautilus ,or whatever file browser, as a drive that can be mounted, at least in my experience.

They're usually only hidden in Windows.

---

### Post by haqking on 2012-11-30
> **forrestcupp said:**
> They're always visible from GParted, but I've also had them visible from Grub, too. Also, sometimes they show up from within Nautilus ,or whatever file browser, as a drive that can be mounted, at least in my experience.

They're usually only hidden in Windows.

yeah I know gparted can see them, i meant hidden as in seen from boot, never looked from grub.

Anyways be interesting to see what the OP comes back with, I have had the message a few times due to a drive at boot being NTFS such as USB etc.

---

### Post by Beardedturtle on 2012-11-30
[http://paste.ubuntu.com/1400845/](http://paste.ubuntu.com/1400845/)

I did a secure wipe of the drive idk why it still shows Win7...gonna give Gpart a try. (If you don't here from me in a few  days it means it blew my machine up).=P

---

### Post by oldfred on 2012-11-30
You are showing one NTFS partition on sda1. But no Windows boot files. And grub has no entry for Windows??

Where are you seeing Windows 7 or is BootInfo report after more changes?

If you are keeping a NTFS partition you need either Windows or a Windows repairCD or flash drive to periodically run chkdsk. Ubuntu runs filechecks after 40 or 60 reboots but cannot run chkdsk.

---

### Post by checoimg on 2012-11-30
maybe you can see if os-uninstaller finds this windows showing up to uninstall it.
[https://launchpad.net/~yannubuntu/+archive/os-uninstaller](https://launchpad.net/~yannubuntu/+archive/os-uninstaller)

---

### Post by Beardedturtle on 2012-11-30
Tried pendrive to make my usb drive bootable but since I am on Ubuntu there is no drive letter so I do not have a bootable  usb drive. No go for Gparted =\

---

### Post by Beardedturtle on 2012-11-30
Got Gparted onto usb drive booted to it and the GUI opens up and splat what a waste of time where the words are supposed to be are a little tiny microscopic sized squiggly lines and I cannot tell anything apart is there any other partioner tool that is easier to use?

---

### Post by Beardedturtle on 2012-11-30
> **oldfred said:**
> You are showing one NTFS partition on sda1. But no Windows boot files. And grub has no entry for Windows??

Where are you seeing Windows 7 or is BootInfo report after more changes?

If you are keeping a NTFS partition you need either Windows or a Windows repairCD or flash drive to periodically run chkdsk. Ubuntu runs filechecks after 40 or 60 reboots but cannot run chkdsk.
sda1: __________________________________________________________________________      File system:       ntfs     Boot sector type:  **Windows Vista/7: NTFS**     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:        


Gparted is totally unusable still searching for a alternative on how to remove SDA1

---

### Post by haqking on 2012-11-30
> **Beardedturtle said:**
> sda1: __________________________________________________________________________      File system:       ntfs     Boot sector type:  **Windows Vista/7: NTFS**     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:        


Gparted is totally unusable still searching for a alternative on how to remove SDA1

are you having an issue booting to your OS ? That message just means it is NTFS which is a Windows FS so it labels it as Win vista/7 it doesnt mean it thinks Windows is on there.

If you dont have Windows then you shouldnt really be using an internal drive as NTFS anyways, you would be better off using a Linux FS such as Ext4 if its gonna be data

---

### Post by Beardedturtle on 2012-11-30
> **haqking said:**
> are you having an issue booting to your OS ? That message just means it is NTFS which is a Windows FS so it labels it as Win vista/7 it doesnt mean it thinks Windows is on there.

If you dont have Windows then you shouldnt really be using an internal drive as NTFS anyways, you would be better off using a Linux FS such as Ext4 if its gonna be data
Grub sees it as a os....

---

### Post by haqking on 2012-11-30
> **Beardedturtle said:**
> Grub sees it as a os....

it is seeing the bootsector, it is assuming an OS of Windows nature on there due it to being NTFS, NTFS 5 which is why its labelling it as Vista or Windows 7.

Is that the issue ? are you actually having a problem or you dont want it to say that ? in which case change the FS, I think you said you are not using windows at all so in which case then you should change the filesystem anyways.

the error upon boot about it missing boot files is when you or the machine try to boot to the drive and it cant find NTLDR, so change the physical order of the drives in the machine or change the BIOS settings so it never tried to boot to that drive, it is a data drive by the sounds of it so should never try to boot to it

---

### Post by Beardedturtle on 2012-12-01
> **haqking said:**
> it is seeing the bootsector, it is assuming an OS of Windows nature on there due it to being NTFS, NTFS 5 which is why its labelling it as Vista or Windows 7.

Is that the issue ? are you actually having a problem or you dont want it to say that ? in which case change the FS, I think you said you are not using windows at all so in which case then you should change the filesystem anyways.

the error upon boot about it missing boot files is when you or the machine try to boot to the drive and it cant find NTLDR, so change the physical order of the drives in the machine or change the BIOS settings so it never tried to boot to that drive, it is a data drive by the sounds of it so should never try to boot to it
There are rare times that my SSD will crash and the bios would go to the spare instantly on reboot oh it will skip the post message so it will go straight into it it requiring a second boot...Zotac Mini ITX Sandy Bridge.

---

### Post by Beardedturtle on 2012-12-01
Went to root (sudo su) then gparted and went to the spare drive it is flagged as boot >_< which flag should I pick?

Edit I picked the lvm flag and now the main SSD drive is flagged as boot.

---

