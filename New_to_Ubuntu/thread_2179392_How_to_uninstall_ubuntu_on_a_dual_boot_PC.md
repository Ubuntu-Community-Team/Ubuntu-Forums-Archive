---
title: "How to uninstall ubuntu on a dual boot PC"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by mushypeas on 2013-10-08
Hi

I have dual booted with windows 7 and ubuntu for a couple of years. Over the last 6 months I have found I rarely use ubuntu as I have specific software that I regularly use on Windows that I prefer to the open source alternatives (and WiINE wasn't reliable enough for those programs).

Anyway, is there any way I can uninstall ubuntu so my PC boots straight to windows 7 rather than going to the GRUB menu and loading ubuntu after 10 seconds?  I can't seem to find how to get rid of it going to the grub menu (short of reinstalling windows 7 over the whole pC)

Thanks

---

### Post by theDaveTheRave on 2013-10-08
mushypeas,

I've never performed this option, but here is some info that may get you most of the way to where you want to go.

First back up your data that you need to keep. Ensure that you have instalation media for your windows system (just in case).

Read all the following before you start, if you have a concern you don't want to do this untill you are absolutely sure of what 'should' happen. Also as I say I have never done this, this is information that I have gathered from searching the net, you may do well to read the reference threads also prior to starting, as it may give you some idea of the problems you may get, and further search terms to investigate

Boot into the Ubuntu live CD.

Find out where the GRUB boot manager is located, you do not want to delete this, although you may need / decide to re-install a new grub partition (probably advisable). Read the instruction on the [GRUB installing]("https://help.ubuntu.com/community/Grub2/Installing")  on the ubuntu wiki pages. You need to confirm that GRUB is installed on a separate device, I have had a quick read of the page I linked to, you should read this carefully to decide how you want to proceed.

Edit the GRUB boot loader to default to boot the windows partition.

Open gParted and you will be able to format the partition that has Ubuntu on it. You will need to format it to NTFS or windows will not be able to see it. Be carefull not to format the partition that has windows on it (it should be fairly obvious, but if not you'll need to log into your main ubuntu partition and gParted or fdisk from there to figure it out).


Second option.

This may sound safer, and is probably how I would go about it.

You will want to get the 'alternate install ISO' of ubuntu or another Linux OS.
Again format the original ubuntu partition back to NTFS
Create a 'new' very small partition for a minial linux install. This will be a command line only install, no extra stuff, you should be able to find a linux version that requires only a few MB of disk space.
Install your minimal linux to this new tiny space.
This will ensure that GRUB is correctly installed on your system.
Make sure that windows is the default OS to boot to from this newly installed GRUB (should be accessable from the GRUB menu)

Some references:
[removing an unwanted second ubuntu partition]("http://askubuntu.com/questions/79813/how-to-remove-a-second-ubuntu-install"): this is where most of my ideas where taken from
[GRUB]("https://help.ubuntu.com/community/Grub2")
[ubuntu GRUB tutorial]("https://help.ubuntu.com/community/Grub2")
[Smallest possible Linux install]("http://unix.stackexchange.com/questions/2692/what-is-the-smallest-possible-linux-implementation")


Hope these ideas help out.

David

---

### Post by westie457 on 2013-10-08
@ mushypeas
If you are going to keep your Linux partitions 'theDavetheRave's advice is right.
If you want to completely remove the non-Windows OS to will need either a Windows recovery CD or an original Windows DVD.

Boot from the Windows media and select the 'Repair computer' option, do not use the 'Automatic Repair', it won't work. Instead drop to a 'Dos Prompt' - usually this is at the bottom of the window.

In here you will need to run these commands:-

1  Bootrec.exe /FixMBR
2  Bootrec.exe /FixBoot
3  Bootrec.exe /RebuildBCD

Exit out of everything and reboot to Windows.

These instructions will over-write the GRUB Boot-loader so you will not be able to boot into any other OS even though the other partitions are intact.
You can then either wipe that partition and reformat it to use with Windows or leave it as is for when you want to come back to Linux.


Hope this helps.

---

### Post by vamshikrishna072 on 2013-10-08
i have tried the same thing but the grub did not go . [IMG]http://i1273.photobucket.com/albums/y409/vamshikrishna072/ubuntu_zpsf63f3028.jpg[/IMG]
i have even tried from this link 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
help me solve out this issue

---

### Post by Mark Phelps on 2013-10-08
Boot into Win7, then use the Backup feature to create and burn a Win7 Repair CD.

Boot from that CD and run Startup Repair three times -- that's right, three times.  

When you reboot after that, you should go straight into Win7.

---

### Post by oldfred on 2013-10-08
If this is UEFI boot you have to manually remove the ubuntu folder from the efi partition and UEFI internally stores boot info and you have to erase that firmware entry in UEFI.

Some UEFI may have this:
 Enter your UEFI menu, select "Boot maintenance manager", then "Boot options"

Or launch an efi shell.

 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by vamshikrishna072 on 2013-10-08
i tried that but that dint work out .
actually i wanted to reinstall ubuntu .i installed it   .
thanks oldfred

---

### Post by mushypeas on 2013-10-08
Thanks for help everyone. Will have a go

---

### Post by Allavona on 2013-10-08
Hopefully you didn't wipe your recovery partition. Most manufacturers do not include Recovery discs anymore. And to top that off, most only have two options in their recovery environments, System Restore and Factory reset. 

You could use Grub Customizer to make Windows 7 the default OS and keep both. You can get it from Softpedia.

---

