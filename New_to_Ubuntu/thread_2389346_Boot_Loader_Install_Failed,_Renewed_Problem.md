---
title: "Boot Loader Install Failed, Renewed Problem"
date: 2018-04-15
forum: New to Ubuntu
---

### Post by majorlunac on 2018-04-15
I have been having problems installing Ubuntu Ubuntu 17.10.1 and Linux Mint 18.3 Sylvia (uses same install system), with errors popping up about the Boot Loader failing to install and grub failing to install. So far, no one has been able to truly pin-point the exact cause or really solve it, with only trial-and-error ending up inadvertently solving it. But I want to suggest a more solid solution and cause, from my testing.

References to the error:
1.) [https://ubuntuforums.org/showthread.php?t=1631746](https://ubuntuforums.org/showthread.php?t=1631746)
2.) [https://askubuntu.com/questions/689595/bootloader-install-failed](https://askubuntu.com/questions/689595/bootloader-install-failed)

As mentioned, the error leads to pop-ups that cannot be closed and all buttons on the pop-ups don't work.

**PROPOSED SOLUTION:**
Steps:
1.) When prompted to "Run Ubuntu without Installing", choose that. Then run the Ubuntu installer from whatever media you put it on.
2.) Choose "Something Else" when choosing how to install on the hard drive. Choose "Make a New Partition Table". Make sure to make a UEFI partition of about 300 MB first, and then make whatever other partitions you need.
3.) When one of the errors pops up "Boot Loader Install Failed" or "grub failed to install" that you are locked into and can't close, go to the Applications menu at the lower left of the whole screen and search for System Monitor. At the Processes list in the System Monitor, change the listing to All Processes using the _=_ button at the top right. Then right-click on xorg or x-server and kill it. (If you have another way to end the pop-ups and close the installer program, please do tell.) Ubuntu live should restart automatically.
4.) Start the Ubuntu installer again, with the same steps 1-2. Make sure to choose "Make a New Partition Table" again and remake ALL the partitions from scratch. This should allow the installer to continue.

Based on how well and consistently this worked for me, and how it only showed that it would change 3 partitions the first time (UEFI, / {root}, /home) and only 2 partitions the second time (/ {root}, /home), I suggest that the installer needs the UEFI partition to be pre-installed for it to install properly. Maybe this is an installer issue/bug, but this is the limit of my knowledge and observations at this time. Please fill in any gaps if you know.

---

### Post by yancek on 2018-04-15
If there is another OS already installed using Legacy/MBR, this will create problems and make one system unbootable especially if you create a new partition.
If you use something else option and have a blank drive, you first need to create the EFI partition during the install, format it vfat and mark it as active/bootable.  After that, craete your root/ swap and any other partitions.   If as is the case with some users, there is another OS already installed EFI, there will be an EFI partition.  If it's a blank drive, then you need to create all partitions. All users are not using EFI so installing in Legacy needs to be an option on the installer.  Also, some users will have another OS installed and want to keep it.

If one has an EFI system or wants to install EFI, the install media needs to boot EFI.  That is expalined at the Ubuntu documentation link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It seems you may have had a bad download or a bad burn to DVD or an incorrectly created usb.   What you describe is certainly not what one would expect during the install.

---

### Post by majorlunac on 2018-04-15
No, it was not a bad download/burn or anything, because I verified the ISO and I used a USB stick, and because it worked without changing the USB stick at all, on the second try. My system boots perfectly now and everything works perfectly.

Even in the link you provided, it mentions that if UEFI is not already installed from a previous OS install, you need to use GParted to make one before you run the Ubuntu install setup program. So my guess is there should be a step in the Ubuntu install setup program that checks for UEFI, installs a new one first, then partitions the rest? Maybe the situation wasn't accounted for and it needs to be added to the installer?

---

### Post by yancek on 2018-04-15
Yes but you can create an EFI partition in the installer the same way you create the root filesystem partition, swap partition or other partitions.  Not sure the installer can mark it as ative/bootable so GParted may be necessary.  

> So my guess is there should be a step in the Ubuntu install setup  program that checks for UEFI, installs a new one first, then partitions  the rest? Maybe the situation wasn't accounted for and it needs to be  added to the installer? 		

The installer does check for an EFI partition and if one already exists,  it is used and a new one should not be created in that case, other than that I would agree.

---

### Post by oldfred on 2018-04-16
If you partition in advance you need to use gpt and create the ESP - efi system partition (FAT32 with boot flag). 
It can be installed to MBR(msdos) partitioned drive, but you then still need an ESP.

If you just do a default UEFI install and erase drive, it will create an ESP. Or if you have another UEFI install it will find & use that ESP, but add a new folder /EFI/ubuntu.

But if you partition in advance and install to gpt without an ESP for UEFI or a bios_grub for BIOS boot, then grub install fails.

---

### Post by oldrocker99 on 2018-04-16
I have had GRUB not install, and I finally figured out that if you get a warning about UEFI, choose "Go Back." That way, you'll have a clean install that won't abort. 

Works for me.

---

