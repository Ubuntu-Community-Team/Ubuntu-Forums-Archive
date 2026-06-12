---
title: "Boot repair refuses to convert Ubuntu to EFI mode"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by Roranicus on 2013-07-19
Hey there, absolute newbie here.

I recently got a new laptop, this one. [http://www.asus.com/Notebooks_Ultrabooks/X550CA#specifications](http://www.asus.com/Notebooks_Ultrabooks/X550CA#specifications)

I would like to dual boot Windows 8 and Ubuntu. I've been trying to follow the instructions here. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

First problem I have, booting from usb or from a dvd under efi mode is impossible on my system. The only way it will boot from anything that's not Windows is in legacy mode. I did manage to install Ubuntu 13.4 this way, but now it won't boot. I then rebooted from the dvd again and ran boot repair, seeing if I could boot Ubuntu in legacy mode and ignore Windows altogether. It didn't work and I got this [http://paste.ubuntu.com/5891448/](http://paste.ubuntu.com/5891448/)

I also tried to convertt to EFI mode, as I believe this would be the best way to solve the issue and dual boot properly. It gave me an error message saying my version of Ubuntu isn't compatible, even though I know it is. 

At this point, I'm extremely confused and starting to get a bit frustrated. Any help would be greatly appreciated. I've considered formatting entirely and just getting rid of Windows 8, but would rather not do that just yet. 

Thanks in advance!

---

### Post by oldfred on 2013-07-19
Is yours one of those systems that only boots UEFI with secure boot on? That is not per standard but some have been modified to only boot Windows using the Windows efi file and with secure boot on.
But you should be able to boot Ubuntu with secure boot on and convert to UEFI.

Are you using Boot-Repair from you Ubuntu installer, so you have the same version?

Intel has been making lots of changes to its open source driver. More for its latest chips but the changes help the somewhat older versions also.
The newer versions of Ubuntu may work a bit better.

---

### Post by Roranicus on 2013-07-19
I'm booting from the same disk I used to install it and using boot repair this way, so it's all version 13.4. Isn't that the newer version? When you mean booting with secure boot on, you mean from the cd? Sorry, as I said, I'm new and not entirely familiar with the terminology yet.

I can boot uefi with secure boot off, but it will only boot windows, it won't boot from the usb drive or from a dvd. I haven't found a way to boot Ubuntu at all in any way except usb or dvd. 

edit, I'm using the 64 bit version. I know the 32 bit version wouldn't work.

---

### Post by oldfred on 2013-07-19
If Windows boots with secure boot off, you should be able to boot from UEFI to flash drive or DVD.

But even from BIOS mode it should see efi partition and under various options let you reinstall grub-efi.
 From Boot-Repair select advanced options, under grub location tab choose /boot/efi, & if you can only boot with secure boot on under grub options tick secure boot.

      
 How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)


 One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

---

### Post by Roranicus on 2013-07-19
> **oldfred said:**
> If Windows boots with secure boot off, you should be able to boot from UEFI to flash drive or DVD.

That doesn't work. Even if I switch secure boot off, it will only boot from flash drive or dvd if I set it to legacy boot, otherwise the option isn't even there. The system works fine with secure boot off though, I can easily start Windows that way. 

> **oldfred said:**
> From Boot-Repair select advanced options, under grub location tab choose /boot/efi

When I do this, I get an error message saying my version of Ubuntu isn't efi compatible. I also get this message when I click recommended repair. I really feel like this error message is the one biggest thing I should worry about, but then I could be wrong. 

      
 > **oldfred said:**
> How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)

This user mentioned"Restore EFI backups". I do not have this option in boot-repair. I'm afraid of following these instructions while being forced to skip a potentially important step. 

> **oldfred said:**
> How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

I hate to be a noob again, but I don't really get that one. :/

---

### Post by oldfred on 2013-07-19
I think some of the links are for those who already had it installed once, and then Boot-Repair backed that up.

I thought Boot-Repair would auto instal grub-efi and uninstall grub-pc. But you can do that manually but need to chroot into your install and run the commands from inside the install. Boot-Repair does have a helper walk thru for chroot. (I have never run that.)

       UEFI chroot:
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by Roranicus on 2013-07-20
I tried that and it did give me progress, I can now set the bios to boot  Ubuntu in either legacy or efi mode. However, I now get this problem  whenever I try to boot Ubuntu  [http://askubuntu.com/questions/78095/grub-elf-magic-error-message-after-installation-how-to-get-dual-boot-option](http://askubuntu.com/questions/78095/grub-elf-magic-error-message-after-installation-how-to-get-dual-boot-option)  and the proposed solution does not work. I could be doing things wrong.  I did make sure to mount sda6, the partition where Ubuntu is installed.  

I tried boot repair again to see if it would work and I got the same  result as earlier, so I think this option is still not a viable one.  Thanks for your help btw, I would never have figured out that last part  on my own, haha. :smile:

---

### Post by oldfred on 2013-07-20
That often is the wrong version of grub. Did you also get an update?
Or UEFI and BIOS write hardware info differently for system to use. So a UEFI install will not usually boot from BIOS and vice-versa as it will not see hardware correctly.
I just saw a new grub update where for UEFI boot it will always use grub's shim (file with Microsoft key) whether secure boot or not.

---

### Post by Roranicus on 2013-07-20
How can I tell? I followed the instructions to the letter, but I'm still not 100% certain what I'm doing.

---

### Post by oldfred on 2013-07-20
Run a new copy of BootInfo report from  Boot-Repair.
I think the instructions on AskUbuntu for for a BIOS type install and you have UEFI.

---

### Post by Roranicus on 2013-07-20
Boot repair again refused to work in efi mode, I did get this when I unclicked the efi option. [http://paste.ubuntu.com/5895066/](http://paste.ubuntu.com/5895066/)

edit: well, that'll teach me to hit reply too fast, It fixed it. I ran boot repair with efi clicked off, rebooted, went into bios and selected ubuntu in the boot options, now I got the proper dual boot menu and I successfully booted Ubuntu without the disk. I'll post here again if something weird happens, but I think this is solved, thanks again!

---

### Post by oldfred on 2013-07-20
If you are booting Ubuntu in BIOS mode it will not let you boot WIndows from grub menu. UEFI & BIOS write hardware info to system differently.
You should be able to go into BIOS and choose UEFI and boot Windows and choose BIOS/CSM and boot Ubuntu but it would be better to fix Ubuntu to boot in UEFI mode.

---

### Post by Roranicus on 2013-07-20
Yeah, I just tried and you're right, Windows won't boot without going into the bios. What I think I'll do is get acquainted with Ubuntu, learn the basic stuff and come back to this once I actually know how to install drivers, create icons and overall feel comfortable with my new OS. Once I get a better hang of it, I think I'll be able to look into this problem without worrying about breaking something, since I'll have a better grasp of the terminology and the logic behind it all.

---

### Post by ikt on 2013-07-30
satanic013666 I have moved your posts to a new thread here: [http://ubuntuforums.org/showthread.php?t=2164070](http://ubuntuforums.org/showthread.php?t=2164070)

---

