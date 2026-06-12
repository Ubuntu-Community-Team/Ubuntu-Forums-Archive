---
title: "Lost Ubuntu boot option"
date: 2016-07-19
forum: New to Ubuntu
---

### Post by weephatz2 on 2016-07-19
Hi,

I'm relatively new to Linux and had just decided to start the free edx introduction course. 
Tonight I had to briefly nip back to my Windows partition (couldn't mount it) to retrieve a file. 
I exited Ubuntu using the Restart option, then let the laptop boot into Windows (which it does by default).
After getting the file I shutdown Windows, powered back up and hit F12 to get back to Ubuntu. Normally when I do this I get a black screen with a blue box in the middle which lets me pick a partition, but this time the Ubuntu option is gone, my only options are Windows bootloader or one of the 2 HDDs :(

The Ubuntu option is gone.

I'd been using this Ubuntu partition for a while, so I'd rather not have to start from scratch. Is there a way I can recover that option?

Apologies I know this is long winded and not technically worded. 

Any help would be greatly appreciated

Side note:

I'm sure some people will be rightly looking at this and saying: You could've googled this and used boot repair you lazy person.

My concern is that, I don't know if grub is the issue.

Normally when I boot:
1. Hit F12
2. Blue box, pick Ubuntu
3. Black screen with white box around edges. This has Ubuntu option too, so I'd either hit enter or let the timer expire.
4. Ubuntu splash screen then login

As far as I know, is grub not step 3 here?

Ie. If I'm not getting to step 3 is grub even the issue?

[http://paste2.org/YGfIcmCy](http://paste2.org/YGfIcmCy)

*update:
So I tried the boot repair recommended option, link above. 
It said repair was successful, but after reboot the result is the same, no Ubuntu option. 

If it helps:
This laptop has 2 drives. 1 for storage, 1 for the 2 Operating Systems.
When hitting F12 I get Windows bootloader, along with the 2 drives.
Selecting Windows goes straight to Windows
Selecting the drive with OSes gives efi failed error (windows 8 BTW)
Selecting drive with just storage (just in case) does nothing, as expected

---

### Post by weephatz2 on 2016-07-19
So apologies for replying to myself here, I'm not trying to bump the thread.

I sat and read through the boot repair output. Most of it went over my head, but towards the bottom was a line that suggested a windows command which looked like it was changing the boot path. 
I'm not that clued up on Linux and partitions (part of the reason I've just started the edx course) but I tried that command and it worked :D
Not only did it work, it has set Ubuntu to the default boot option! No more wearing out the F12 key every time I boot.
I'm sure someone here would have walked me through this eventually, but figuring it out for myself was really satisfying.

Apologies admins for spamming up the forum with this, I'll understand if you want to delete it.

---

### Post by yancek on 2016-07-19
> 
This laptop has 2 drives. 1 for storage, 1 for the 2 Operating Systems.

According to the boot repair output, you have two 1TB drives.  The first has windows and the second has Linux/Ubuntu.  You have an EFI system which does have an EFI partition on the first drive (windows) with both windows and Ubuntu efi files.  I'm not sure why you have the windows (FAT32) filesystem on the second drive where you have Ubuntu.  That would not be related to the problem.  Did you try the suggestion at the bottom of the page to set the second drive to first boot priority in the BIOS?  I would start with that option before the second.

---

### Post by weephatz2 on 2016-07-19
Thanks Yancek. Looks like you just explained what I stumbled across by fluke.

I guess my partitioning is a mess.

Think I'll spend this weekend backing up files from Windows then I'll make the leap to get rid of it for good. Just an Ubuntu drive and storage drive.

---

### Post by grahammechanical on 2016-07-19
With UEFI boot systems Windows 8/10 will be installed in EFI mode and that means a special efi_boot partition for the Windows efi boot files. And in your case that is the second partition on the first hard drive = sda2

With Windows installed in EFI mode Ubuntu must be installed in EFI mode as well. The Ubuntu installer will default to installing the Ubuntu efi boot files on to the first hard drive (sda) and it uses the same efi_boot partition as Windows and the two sets of efi boot files co-exist without the Ubuntu efi boot files over-writing the Windows efi boot files. That is what happened.

If we direct the Ubuntu installer to install the Grub boot loader to the second hard drive (the one with Ubuntu on - sdb) then it would have put the Ubuntu efi_boot files into the first partition of the second hard drive = sdb1 = file system - vfat & boot sector type - FAT32.

Some of us prefer to have Windows boot files on the Windows drive and Ubuntu boot files on the Ubuntu drive with the motherboard set to load from the Ubuntu drive. The Grub boot loader should then give us an option to load either Ubuntu or Windows and if anything causes Ubuntu to break we can still use the UEFI to load Windows from the Windows drive.

Regards.

---

