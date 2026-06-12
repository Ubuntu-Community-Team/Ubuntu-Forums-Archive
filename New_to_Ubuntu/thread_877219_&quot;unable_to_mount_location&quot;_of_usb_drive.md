---
title: "&quot;unable to mount location&quot; of usb drive"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by kcir1957 on 2008-08-01
noobie, newbie, retard, I'm all the above when it comes to ubuntu. I'm using a live cd of 8.04. I have a wd essential 500gb usb drive that was attached to my dish network 722vip hd dvr when for some reason the receiver stopped recognizing the hd. Dish netork reformats hds with a linux partition as I understand it. So now I have a 500 gb usb drive which I can't use on my xp os as I can only see it in device manager as WD. I cannot access it through disk management or any other venues. So, I'm trying ubuntu. When I go to computer, it was listed as usb drive but when I double click or right clicked to mount I received "unable to mount location". I tried a couple of commands at what I think was the root level, one of which was the fdisk and it recognized my two internal drives but not the usb. I unplugged the usb and reconnected and it was then listed as a scsi drive under computer but still unmountable. I'm not trying to copy encrypted files or anything like that. Just want to reformat my usb drive back to fat32 or ntfs so I can use it again. HELP!

---

### Post by benfindlay on 2008-08-01
Reformatting to NTFS can easily be done in Windows by right clicking on My Computer, choosing Manage and then selecting disk management. You can format the drive from there. Alternatively, to format it in ubuntu, you need to install the gparted package (as I don't think it is installed by default). This tool is then listed under System>>Admin>>Partition Editor. Just select the drive in question, right click on the partition, and it's fairly self explanatory!

Hope this helps

---

### Post by silkstone on 2008-08-01
If you want to format it NTFS or FAT32, can't you do that through XP's Disk Manager? If Windows recognises the drive, it should show up there but with an unknown or raw filesystem, and you can then format it.

EDIT/ Beaten to it! But you won't be able to install gparted when running from the live CD, so formatting from XP is the easiest option.

---

### Post by dca on 2008-08-01
You should be able to detect it in Windows, though...  Go to control panel, then Administrative Tools, then Computer Management, then Disk Management'.  Right click on the drive and select format...

---

### Post by benfindlay on 2008-08-01
> **silkstone said:**
> But you won't be able to install gparted when running from the live CD, so formatting from XP is the easiest option.

Ah yes, if it's the live cd it should already be installed I believe as the installation tool uses it to set up partitions for you doesn't it?

---

### Post by kcir1957 on 2008-08-01
benfindaly, silkstone and dca, thanks for the quick responses but I assure you that the drive is not viewable in disk management.

---

### Post by kcir1957 on 2008-08-01
sorry benfindlay

---

### Post by kcir1957 on 2008-08-01
also...can't view disk through ghost, acronis true image, or partition expert

---

### Post by egalvan on 2008-08-01
> **kcir1957 said:**
> ...for some reason the receiver stopped recognizing the hd. 

The  drive may be damaged/dead. Does the BIOS see it correctly?


> **kcir1957 said:**
> ...I'm not trying to copy encrypted files or anything like that. Just want to reformat my usb drive back to fat32 or ntfs so I can use it again. HELP!

If you want to completely erase the drive and start over, I suggest attaching it as the only drive, then boot "Darik's Boot and Nuke".
 DBAN will erase the drive.

get dban from [www.dban.org](www.dban.org), burn the iso. It's small, and fast.

when dban is done, the drive will be clean.

At this point, install like you would any brand-new drive.

---

### Post by kcir1957 on 2008-08-01
drive is seen only under device manager, disks and shows only as WD with no other info. Claims "device is working properly". So to use "Darik's Boot and Nuke", I need to disconnect my two internal hds, then with usb drive attched, boot from cd iso?

---

### Post by kcir1957 on 2008-08-01
Oh, other problem is that usb drive is not seen in bios as afaik because when I boot with usb drive attached screen to change boot order and enter bios freezes and os won't boot until I disconnect usb drive then all is fine.

---

### Post by egalvan on 2008-08-01
> **kcir1957 said:**
> drive is seen only under device manager, disks and shows only as WD with no other info. Claims "device is working properly". So to use "Darik's Boot and Nuke", I need to disconnect my two internal hds, then with usb drive attched, boot from cd iso?

If device manager show the drive, you MAY be able to erase it.

But I use dban, because "it just works".

You CAN leave the other drives attached. Disconnecting them is just a (*huge) safety factor.

dban does not forgive errors, and there is NO un-erase or "oops" button.
Safest is just to isolate the drive, and a bootable CD.

---

