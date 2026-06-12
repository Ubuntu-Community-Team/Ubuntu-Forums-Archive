---
title: "Install Grub2 to another disk with Boot-repair"
date: 2022-03-16
forum: New to Ubuntu
---

### Post by walstib2 on 2022-03-16
I have a Ubuntu 18.04 installation (actually a webserver I build long ago) on normal "old fashioned" spinning harddrive.  I want to have it on SSD so I used Gparted to copy the partitions to the new drive and set the boot-flag. Now I want to copy the grub from the old disk to the new SSD and I was under the impression "boot-repair could do this without endangering my old drive. Or is there another smarter way?
I  h a v e read alot of different ways and tried a few but to no avail.
Sincerely):P

---

### Post by walstib2 on 2022-03-16
I should add that I somehow got grub on the new SSD but that it doesnt boot but just shows the black screen with grub> on it.
I should also add that I have the physical possibility to put the new  SSd in another machine and edit it from there if thats easier. I am am  however inclined to use the original installation (the spinning disk) as  little as possible. 				
And..: isnt it possible to connect both disks to another machine and copy the original grub to the new SSD?

---

### Post by walstib2 on 2022-03-16
I should also add that I have the physical possibility to put the new SSd in another machine and edit it from there if thats easier. I am am however inclined to use the original installation (the spinning disk) as little as possible.

---

### Post by grahammechanical on 2022-03-16
I have never used Boot Repair but I have attempted to study many Boot Repair summary reports from users having booting problems. As far as I can tell the standard repair that Boot Repair recommends is to re-install Grub. Why did you think that Boot Repair would copy Grub and its configuration files from one disk to another. I do not think that is the purpose of Boot Repair,

I wonder if you should be discussing cloning one drive to another? Every partition on any drive has a Universally Unique Identifier (UUID) code number. It is usually a very long combination of letters and numbers. The Grub configuration file (grub.cfg) makes use of the UUID to locate the Linux kernel to load. A mismatch between the UUID code number in grub.cfg and the actual UUID of the partitions of the SSD could be the reason for Grub loading to a Grub rescue prompt.

Regards

---

### Post by oldfred on 2022-03-16
Typically you do not copy grub, but just reinstall it.
And with UEFI, you may have to reinstall or know how to use efibootmgr to create new UEFI entry.
You cannot have duplicate UUIDs or GUID(partUUID), so if true clone, you cannot have both drives connected when rebooting.
Or if UUIDs & GUIDs were updated, then new install of grub is required as everything is different.

If reinstalling grub, you may need Boot-Repair's Advanced mode or use a full chroot into install from a live installer.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by walstib2 on 2022-03-16
Yes but as I copied the partition to the SSD it should have the same UUID, shouldnt it? My latest thought is that I make a Usb-stick with Ubuntu 18.04 (the same as the original and the SSD-drive) and boot from that with the nSSD connected. I think there is an option in Boot-repair as to to where to write the grub, than I can choose the SSD and do it. Im on it as I type so Ill know in a little while. My thoughts are that when now the SSD is a !00% copy of the old one I just have to make it bootable.

---

### Post by walstib2 on 2022-03-16
Not uefi. [http://paste.ubuntu.com/p/7pssn8zDcj](http://paste.ubuntu.com/p/7pssn8zDcj)

---

### Post by walstib2 on 2022-03-16
Should I wait for analysis or did you mean I should run it as in 2nd option? ([https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/))

---

### Post by oldfred on 2022-03-16
You have an UEFI system and booted live installer in UEFI mode.
If using Boot-Repair to make fixes better to have the live installer in the same boot mode as your install.
It does look like Boot-Repair even though in UEFI mode, sees no ESP - efi system partition so will default install grub in BIOS boot mode.

Grub in MBR is looking for an UUID that does not exist in the report.
Do not set grub timeout to 0, as then you cannot get to grub menu when you need to, even if one install.

Starting at line 66 are all your UEFI boot entries. 
It looks like you did install many systems in UEFI boot mode, before.
You should houseclean all the old entries. There was an issue with having too many entries & locking up system so tight you  had to return to vendor to fix. They originally blamed Linux, but then it was shown it could be done with Windows & was a vendor issue. Supposedly fixed, but best not to keep old entried.

# from liveDVD or flash booted in UEFI mode and use efibootmgr (BIOS install will not have efibootmgr)
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by walstib2 on 2022-03-17
My bad, I had booted installer so many times that I forgot to choose Legacy-mode intsead of Uefi in bios. Anyway, when tryin to run sudo efibootmgr-v it told me that it didnt exist so  I rebooted the installer in Legacy-mode. I deal with that uefi-problem later. :
[http://paste.ubuntu.com/p/NQpc6QQ33h/](http://paste.ubuntu.com/p/NQpc6QQ33h/)

---

### Post by oldfred on 2022-03-17
Line 16, grub is tying to boot from an UUID that does not exist.
You need to reinstall grub.

---

### Post by walstib2 on 2022-03-17
Worked! Fixed! Thanx a million!

---

