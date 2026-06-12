---
title: "Unable to boot Ubuntu 13.10 installed on USB Flash Drive - UEFI System"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by dss1873 on 2013-11-21
This is my first time trying to install and use Ubuntu. I have a Dell computer that came preloaded with Windows with UEFI and Secure Boot. Windows is installed on the first drive (a 240GB Samsung SSD) and a second 2TB data drive is also installed.

I was able to successfully create a pendrive on a USB Flash drive to try Ubuntu with persistence. I can boot the USB Flash drive w/o problem by hitting F12 at startup to obtain a list of boot options. Windows boot manager is listed as well as the PENDRRIVE.

I have then used the install Ubuntu option on the PENDRIVE to try to install an actual version of Ubuntu on a second 32GB USB Flash Drive (SANDISK). My goal is to have Ubuntul installed on a flash drive that I can plug into the computer and use when I want by hitting F12 at startup to get the the computer's boot option menu. I've read the various posts and doc about how to install for a UEFI system (I created two partitions, one an efi boot partition and a second ext4 partition for the Ubuntu install).

The install completed successfully on the SANDISK, but when I start the computer, hit F12 to get a list of boot options, the SANDISK does not show up. The PENDRIVE does.

It seems obvious to me that it should be able to work as the PENDRIVE (live Ubuntu version) works on my system so I don't understand why the fully installed version does not work.

I have run Boot repair in info mode and here is the link for what it generated:
[http://paste.ubuntu.com/6451480/](http://paste.ubuntu.com/6451480/)

---

### Post by simbauad on 2013-11-21
Doesn't seem like Ubuntu got something to do with it! Well you might try installing Ubuntu on your hard drive. Seems like your BIOS/EFI doesn't seem to recognize SanDisk as a bootable medium.

---

### Post by oldfred on 2013-11-22
You have an efi partition on sdg, but have no efi files in that partition.
And your fstab shows the Windows efi partition's UUID as the location of grub boot files, but they are not shown there either.
When you installed did you specify to install grub2 boot loader to sdg? Drive letters may change, but UUIDs will not.
Boot-Repair should be able to fix it, but do not use auto repair, but choose update MBR? and it should let you install grub-efi into sdb and should also update fstab. You may need to double check that.

Your install is like those that install to a second drive.

       Two Drive UEFI installs
HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by squakie on 2013-11-22
My suggestion: read and re-read everything you can find from user OldFred about UEFI/EFI and Ubuntu.  He has some specific links to information regarding problems with some PC's - including some Dells'.  I don't know if THE solution for you will be in those or not, but it may be enough to get you thinking about it from a different view point and work out the solution.  One thing I do remember, and I honestly don't know if it still applies or not, but you had to be using 64-bit Ubuntu for it to work along with UEFI/EFI.  Oldfred has been a termendous help to countless people regarding the UEFI/EFI issues.  That's why I suggest to read everything you can find from him.  He's a highly intelligent perosn and has a deep understanding of Ubuntu.

Good luck!

EDIT:  Noticed OldFred posted while I was typing, so just follow his advice ;)

---

### Post by dss1873 on 2013-11-23
Thanks very much. I had previously reviewed some of the threads you have listed for two drive installs, but as a beginner, was hard to follow everything.

When I installed, I made numerous attempts specifying both sdg (as the device for the boot loader) and sdg1 (the 100MB efi partition) as the device for boot loader. The install instructions are confusing as to when it says "device" does it mean the hard drive or a partition on the hard drive. The boot info file I posted was for an install where I specified sdg1 partition for the bootloader. But I have tried it both ways.

I should add that one of the many things I tried (per one of the threads you have listed I believe) was to disconnect the hard drive with windows installed and then install Ubuntu. That seemed to work until I reconnected the hard drive with Windows and then I was back to the same issue of Ubuntu not showing up as an option on the boot menu.

As a beginner, not sure what "fstab" is.

Also not sure what you mean when you say "Drive letters may change, but UUIDs will not." I think I understand the concept, but don't follow how to modify the install to use UUIDs. Maybe you are referring to something like in this thread: [http://askubuntu.com/questions/200923/what-scenarios-causes-a-hard-drive-uuid-to-change](http://askubuntu.com/questions/200923/what-scenarios-causes-a-hard-drive-uuid-to-change)

I will try using Boot_Repair as you suggested. But when you say, it should let me install grub-efi into sdb, do you mean that in a generic sense to stand for the second drive (which would be sdg in my case) or do you mean that in a specific sense to mean my sdb.

---

### Post by oldfred on 2013-11-23
Ubuntu changed to use UUIDs by default, so drives like an external that may change will work. My bootable flash drive is sde when plugged in, but on reboot it is sdb as I guess I skipped a SATA port when installing hard drives and USB flash drive becomes sdb.

You need to be installing in UEFI mode, and you get grub menu when in live mode, not purple screen. In UEFI mode grub is installed into the efi partition, but I think you still specify drive or sdb or sdg or whatever second drive is mounted as.
If installing in BIOS mode then you never specify a partition.

Many new UEFI are not totally clear on which boot mode you chose. Usually one will say UEFI and the other may be just about anything, CSM/BIOS/Legacy/AHCI or just a device label or name without UEFI.

fstab is a file used to auto mount partitions at boot. 
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by dss1873 on 2013-11-23
I'm installing in UEFI mode (the boot screen says at the top "Boot Mode is UEFI - Secure Boot On").

I do get GRUB menu with four options, 1)Try Ubuntu, 2)Install Ubuntu, 3)OEM install, etc. I then have tried both option 1 (booting to live Ubuntu and installing from there) and option 2 (going directly into the install program).

When installing Ubuntu, one of the options is to specify the device where the boot loader will be installed and as I noted previously, I have been specifying the efi partition on the USB flash drive. I don't understand then why there are no efi files in my efi partition on the USB drive.

When I start Boot_Repair, it says "EFI Detected. Please check the options."

When I select Advance Option in Boot-Repair, there is a grub location tab. The OS to boot setting shows Ubuntu on sdh2  (which is correct). The Separate Boot\EFI Partition setting shows sda2 (the hard drive with Windows installed and the EFI partition on that hard drive which is incorrect). When I click the drop down arrow to choose sdh1, there are no other choices available except for sda2

So, I'm not sure how I to use Boot-Repair to fix it.

---

### Post by oldfred on 2013-11-23
Is there something about the efi partition on the sdh drive that is not correct? 

Post this:
sudo parted -l

I do not see a difference in booting the Ubuntu installer as a flash drive and creating a new efi partition on your external drive??
Perhaps something in having secure boot on?
Have you tried with secure boot off?

---

### Post by dss1873 on 2013-11-24
>>I do not see a difference in booting the Ubuntu installer as a flash drive and creating a new efi partition on your external drive??

That is my point exactly! I do not see why one works and the other doesn't. I'm booting the Live Ubuntu trial version on a flash drive in UEFI mode and secure boot on. So, why won't the second flash drive on which I'm doing a true install of Ubuntu not work. Obviously, in one case I'm creating the live Ubuntu version using the windows pendrive program and in the latter, I'm using the Ubuntu installer. This would seem to me to indicate that it is not a UEFI or Secure Boot issue, but something going wrong in the install (as you pointed out that the boot files are not being written to my EMI System partition).

Here are the results of running the parted command:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  316MB  315MB  ntfs         Basic data partition          hidden, diag
 2      316MB   420MB  105MB  fat32        EFI system partition          boot
 3      420MB   555MB  134MB               Microsoft reserved partition  msftres
 4      555MB   256GB  256GB  ntfs         Basic data partition          msftdata


Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2000GB  2000GB  ntfs         Basic data partition  msftdata


Model: TOSHIBA TransMemory (scsi)
Disk /dev/sdg: 7759MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  7759MB  7759MB  primary  fat32        boot, lba


Model: SanDisk Extreme (scsi)
Disk /dev/sdh: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  106MB   105MB   fat32              boot
 2      106MB   32.0GB  31.9GB  ext4

---

### Post by oldfred on 2013-11-24
Parted shows the efi partition in the SSD, but only shows a gpt drive with a fat32 boot on your 32GB SanDisk. I thought a FAT32 with boot flag was always an efi partition in gpt partitioning?

Install gdisk from repository.
sudo apt-get install gdisk
#change to correct drive you are installing into:
       sudo gdisk -l /dev/sda

      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Only gparted/parted use boot flag to define efi partition. It actually is a long GUID in gpt(GUID) partitioning.
gdisk will show the efi with a short code of ef00.

I do not yet have an efi install but already partitioned my newest flash drive for two installs with both efi (ef00) and bios_grub (ef02) partitions.

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          976895   477.0 MiB   EF00  EFI System
   2          976896          978943   1024.0 KiB  EF02  
   3          978944        29650943   13.7 GiB    0700  sys
   4        29650944        60532735   14.7 GiB    0700  sys 
```

---

### Post by dss1873 on 2013-11-24
First I want to be sure to thank you for all the help you are providing and your reply to each and every one of my posts. I'm very appreciative and without your help, I would have given up at this point because it certainly is talking a lot of time and effort.

Sorry to be slow, but as a complete beginner, a lot of what you say is shortcut and too fast for me to follow so if I could ask some follow up questions to get clarification.

How are you able to tell that there is an efi partition on the SSD, but not on the Sandisk. The only difference I notice between the listings for sda2 and sdh1 is that sda2 has the name "Efi system partition" whereas the name is blank for both partitions on sdh. I was assuming that the "name" field is arbitrary (I could name any partition whatever I want).

Maybe you are asking for me to run gdisk and then post what is says to see if in fact sdh2 shows as an efi partition (with a code of EF00)?

>>#change to correct drive you are installing into:
What does the "#" mean in "#change"?

>>GPT fdisk Tutorial -srs5694 in forums
Not sure what "-srs5694 in forums" means. Is there another tutorial referenced by -srs5694 (I searched the forums and didn't see anything) or is this a reference to the link at rodsbooks.com?

---

### Post by oldfred on 2013-11-24
In many of the programming lanuages # is a comment, so I used that so you do not type or copy & paste those commands.
If you look at that thread, you will see that srs5694 was the user in that thread that posted gdisk info. In fact he is the Rod in rodbooks. His site then has more info on how to use gdisk.
I do just want the output from gdisk to confirm if the label is missing in the parted output, because of the way it was created or if somehow it is not an efi partition, which it does seem like it should be.

One advantage of efi partitions is that all the boot files are just files. UEFI then reads those files to boot. You can literally copy valid boot files into the efi partition and have it work. With BIOS you have to install boot data to MBR and often additional data elsewhere on drive as part of boot process, More boot files are required as MBR is so tiny.

---

### Post by dss1873 on 2013-11-26
Appreciate the explanation of efi partitions! So, can I then just copy the files from the efi directory of my Pendrive (the one that has the Ubuntu live version that successfully shows up as a boot option on my computer and which I'm using to install Ubuntu) to my USB Flash (Sandisk) that is missing the efi files? Probably not that easy as not sure what the efi files have to point to and if they would have to be updated for the different partition/directory structure on Sandisk vs. Pendrive.

In any case, here is the gdisk results for my Sandisk (sdh).
--------------
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdh
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdh: 62533296 sectors, 29.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8306A95F-47BE-41F9-AECD-D52DFA8870C0
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 62533262
Partitions will be aligned on 2048-sector boundaries
Total free space is 4210 sectors (2.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  
   2          206848        62531066   29.7 GiB    8300  [/CODE]
-----------------

(Note: I'm out of town for the rest of the week so it will be next week before I can follow through on whatever next steps you recommend.)

---

### Post by oldfred on 2013-11-26
I believe there is a stub of grub (or you need grub.cfg which is normally in /boot) that refers to install that would have to be updated so it can find / and if separate partition /boot.

I would try using Boot-Repair booted in UEFI mode and see if you can update MBR (it really then should update efi) and choose your install in sdh and boot location sdh. Or if you also gives the option to totally uninstall grub & reinstall it on sdh.
If it only offers sda, then copy then entire ubuntu folder in efi partition from sda to efi partition in sdh. Also copy /boot folder.

Someone posted this, but it is only a list of .efi files, there should be others. This does not show full path as it was from a chroot.
 -rwxr-xr-x 1 root root 123904 Nov 17 14:37 ./Boot/bootx64.efi
-rwxr-xr-x 1 root root 1604952 Sep 30 05:57 ./Boot/bkpbootx64.efi
-rwxr-xr-x 1 root root 1355736 Nov 17 20:34 ./ubuntu/shimx64.efi
-rwxr-xr-x 1 root root 123904 Nov 17 21:07 ./ubuntu/grubx64.efi

Someone also posted these exist. 
 /EFI/BOOT/grub/grub.cfg
/EFI/BOOT/grub/x86_64/*mod
/EFI/BOOT/grub/fonts/unicode.pf2

---

### Post by dss1873 on 2013-12-03
In Boot-Repair, MBR is grayed out.
Under Grub Options, I can select "Purge GRUB before reinstalling"
Under Grub Location, I'm given only "sda2" in the dropdown list for "Separate /boot/efi partition" choice.

On sda2, I do have /EFI as the top directory. In /EFI, I do have Boot, Microsoft, and Ubuntu subdirectories. The Boot directory has one file: Bootx64.efi. The Ubuntu directory has no files.
On sdh1, I have no directories. I understand your post to mean that I should create a /efi directory on sdh1 and then create the Ubuntu and Boot subdirectories and copy the files from those directories on sda2. Is that right?

If I use Boot-Repair to purge and reinstall Grub on sda2 (as it does not give me the option for sdh1 or sdh), will this mess up my boot files for Windows so that it will no longer work the same (act as a purely Windows machine that automatically boots Windows) if the Ubuntu flash drive is not installed into the USB port?

---

### Post by oldfred on 2013-12-03
Each system installs separate folders for boot files in the efi partition. So no conflicts. But:
But some of the auto fixes with Boot-Repair will rename Windows boot file and substitue grub2's shim file. That is for "buggy" UEFI that only boot Windows and the work around is to rename shim to be the Windows name so UEFI thinks it booting Windows and actually booting grub. So do not run any rename function in Boot-Repair.

You posted this which says you have an efi partition on sdh. The ef00 code with gdisk is an efi partition.

       1 2048 206847 100.0 MiB EF00 

If grub installs correctly the /efi/boot and /efi/ubuntu folders in the efi partition will be created. Depending on how mounted in may show additional paths in front. 

This was from tinycore, but I think the grub install is the same. Your path may be different.

 [http://forum.tinycorelinux.net/index.php?topic=13445.15](http://forum.tinycorelinux.net/index.php?topic=13445.15)
#USB directly structure from install create /EFI/BOOT first
sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable
/EFI/BOOT/BOOTX64.EFI [grub-efi created BOOTX64.EFI rather than grub.efi as soon as I used gdisk]
/EFI/BOOT/grub/grub.cfg
/EFI/BOOT/grub/x86_64/*mod
/EFI/BOOT/grub/fonts/unicode.pf2

I also have seen this:
      
 mounted the USB EFI partition at /media/test and I installed grub with
sudo grub-install --target=x86_64-efi --efi-directory=/media/test --bootloader-id=grub --removable --recheck --debug

---

### Post by dss1873 on 2013-12-03
Again, sorry to be slow on the uptake here...

So are you saying I can let Boot-Repair do a repair to my Windows install drive (sda) where it thinks it wants to repair the EFI files (instead of sdh1 which is really where Ubuntu is installed) and then copy the /efi/boot and efi/ubuntu files over from sda to sdh1 and that should work without messing up my Windows install and boot as long as I make sure not to select any rename options??

Or, are you saying I maybe should try the commands you listed to install grub on sdh1 directly?

In this section that you posted:
#USB directly structure from install create /EFI/BOOT first
sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable
/EFI/BOOT/BOOTX64.EFI [grub-efi created BOOTX64.EFI rather than grub.efi as soon as I used gdisk]
/EFI/BOOT/grub/grub.cfg
/EFI/BOOT/grub/x86_64/*mod
/EFI/BOOT/grub/fonts/unicode.pf2

I understand the first line is a comment. the second line is a command to execute in a terminal. The other lines (starting with /efi/...), are those the output of the command or directory structure or what?

---

### Post by oldfred on 2013-12-03
I think I would try Boot-Repair first. Just not an auto repair. 
You should be able to check update MBR (not really MBR with UEFI) and in Advanced choose a system and choose a location for install of grub. 
Just be sure to boot Boot-Repair in UEFI mode as repairs will be then in UEFI mode. If you boot in BIOS mode it may convert to a BIOS boot.

I think the command line installs are to just install a grub into a flash drive with UEFI. Not necessarily the grub for your install. It may then require additional configuration.

---

### Post by dss1873 on 2013-12-03
Tried running Boot-Repair. Gave this error message:[INDENT][I]An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/6517906/](http://paste.ubuntu.com/6517906/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].[/I]


[/INDENT]
Have not tried re-booting yet. Wanted to post now in case computer won't boot at all.

---

### Post by oldfred on 2013-12-03
Locked ESP is an efi partition that it cannot write into. It seems to happen with some systems, an we do not know exact cause.
Some have run chkdsk on the FAT32 partition and made it work.
Others had to fully backup the efi partition, delete the efi partition, create a new FAT32 partition with the boot flag so it is the ESP or efi partition and restore all backed up files.

Some have UEFI/BIOS that may also have settings that lock it. If your system needs a password that my unlock it.

 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477)
cannot mount /sys/firmware/efi/efivars on boot - 13.04 kernel issue
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868)

---

### Post by dss1873 on 2013-12-04
Very strange!

I used Windows diskpart to assign a letter to efi partition on sdh and ran chkdsk. No errors. I then tried to duplicate suggestions in some of the threads about creating a second efi partition on sdh. I then turned off the boot flag on the second partition so there is only one EFI System partition on sdh.

I reinstalled Ubuntu 13.10 from a Ubuntu live disk (installed on a USB flash drive - sdg) onto sdh (also a USB flash drive). Install completed and asked if I wanted to restart or continue to try out Ubuntu Live. I chose to continue to try, but then immediately did a shut down, removed the Ubuntu Live USB flash drive and then powered on the system. I held down F12 to get the boot menu (as before) and this time I had the following options listed: Ubuntu, Windows Boot Manager, Ubuntu (yes, Ubuntu was listed twice). I selected Ubuntu and obtained a grub menu with various options such as bot with advanced Ubuntu options. I chose to boot up normal Ubuntu and the newly installed Ubuntu (complete with my user name) booted up fine. I shut down, took out the USB drive with Ubuntu and re-turned on the computer to see if Windows would boot up. It did not, but instead gave me a grub prompt. I hit exit and Windows booted. I turned off the machine and restarted a couple of times and Windows booted normally. So I figure everything is working, reinsert the flash drive with Ubuntu, hit F12 to get the boot menu and Ubuntu is no longer listed as boot option.

Note that I had seen this behavior one other time previously a few weeks ago as I was trying to diagnose the problem which is that right after install, I did get a boot menu showing Ubuntu, Windows Boot Manager, Ubuntu and it worked until I booted Windows and then those boot options disappeared. So I don't think running chkdsk or adding a second efi partition made any difference.

---

### Post by oldfred on 2013-12-04
I thought UEFI remembered entries, and if fact to remove an entry often requires use of command line in UEFI with efibootmgr to delete an entry from it.
But sometimes it needs a reboot or two for UEFI to correctly scan and update UEFI entries. 

But I do not understand why it is not correctly finding the external. That should not be any different than booting the Ubuntu installer as UEFI??

This should show entries UEFI has.
 # from live CD and use efibootmgr
sudo efibootmgr -v

      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)

---

### Post by dss1873 on 2013-12-05
Before looking at what entries UEFI has listed, I double checked if the efi system partition was on sdh and whether there are any boot files.


[http://paste.ubuntu.com/6523332/](http://paste.ubuntu.com/6523332/)
As before, boot-repair shows no boot files on any of the partitions for sdh1 or sdh2. 

I don't know if this is relevant, but sdh1 shows a disrepancy in the boot sector info:
 According to the info in the boot sector, sdh1 starts 
 at sector 0. But according to the info from fdisk, 
 sdh1 starts at sector 2048.


gparted shows sdh1 as EFI system partition
[I had pased in a screen shot of gparted, but that was lost when I posted the reply]


sudo parted -l shows sdh2 as EFI system partition.[INDENT]Model: SanDisk Extreme (scsi)
Disk /dev/sdh: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  135MB   134MB   fat32                              boot
 2      135MB   240MB   105MB   fat32        EFI system partition  msftres
 3      240MB   32.0GB  31.8GB  ext4
[/INDENT]


So even if I can figure out how to modify the uefi entries, what would I point to as there are  no boot files on sdh1 (which is what I selected as the efi system partition when I did the install) or even on sdh2? Counld the discrepancy in the boot sector info be causing problems and should I try making the second fat32 partition the efi system partition at install and leave sdh1 as a spacer blank partition?

---

### Post by dss1873 on 2013-12-05
I've tried to upload and add the attachment I referenced in my previous post.

---

### Post by dss1873 on 2013-12-05
Here is the result of running efibootmgr:

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0008
Timeout: 2 seconds
BootOrder: 0004,0008,0006,0007,0002,0003,0005,0001,0000
Boot0000  P1: ST2000DM001-1CH164            Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001  SanDisk Extreme 0001    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0002  P2: PLDS DVD+/-RW DH-16AES        Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0003  UEFI OS    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0004* Windows Boot Manager    HD(2,96800,32000,2af8ab89-7493-4a88-b451-5e0f1d2d5b2b)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0005  Realtek PXE B03 D00    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0006  UEFI: IP4 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(b8ca3a8ccc7a,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0007  UEFI: IP6 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(b8ca3a8ccc7a,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0008* UEFI: TOSHIBA TransMemory 1.00    ACPI(a0341d0,0)PCI(1a,0)USB(1,0)USB(5,0)HD(1,3f,e73c21,7c3b63e4)..BO

---

### Post by oldfred on 2013-12-05
Without boot files it is not going to work.

I do not remember you having two FAT32 partitions before? You can only have one efi partition or a FAT32 with the boot flag in gparted or ef00 code with gdisk.
But the msftres is only required by Windows and must be unformatted not FAT32. Did you create partitions with Windows? Windows seems to always add that partition.

       Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by dss1873 on 2013-12-05
I had to use Microsoft diskpart in order to be able to run chkdsk. I then formatted the drive which added msftres automatically when set to a gpt disk. The problem was when it created the efi system partition, it was after msftres and it is recommended that efi system partition be first. Also given the threads on creating a second efi partition to fix the efi system partition locked, I used gparted to create a second efi partition and then removed the boot flag on the second partition and set it for the first partition (thereby getting a second fat32 partition. I then used gparted to set the msftres flag on the second partition.

---

### Post by dss1873 on 2013-12-05
gdisk agrees with gparted in showing sdh1 as efi partition:
   1            2048          264191   128.0 MiB   EF00  
   2          264192          468991   100.0 MiB   0C01  EFI system partition
   3          468992        62531491   29.6 GiB    8300  

So you think I can ignore this error from boot info:

> According to the info in the boot sector, sdh1 starts 
 at sector 0. But according to the info from fdisk, 
 sdh1 starts at sector 2048.

---

### Post by dss1873 on 2013-12-05
I re-tried the install. For sdh I mimmicked the partition configuration on sda which seems to work (i.e. I can boot Windows). I created an inital dummy partition and then made the second partition the efi system partition. The first partition sdh1 is labeled DUMMY

For sda, gdisk shows:
>    1            2048          616447   300.0 MiB   2700  Basic data partition
   2          616448          821247   100.0 MiB   EF00  EFI system partition
   3          821248         1083391   128.0 MiB   0C01  Microsoft reserved part
   4         1083392       500117503   238.0 GiB   0700  Basic data partition

For sdh, my configuration is:
>    1            2048          104447   50.0 MiB    2700  
   2          104448          309247   100.0 MiB   EF00  
   3          309248        62531904   29.7 GiB    8300 

This time when I did the install, I received an error message that the installer failed trying to install grub to DUMMY (the first partition sdh1) and not the efi partition (sdh2). I confirmed twice that when I did the install, I had selected sdh2 as the location where to locate the boot loader. So there seems to be a bug where the installer ignores the location I'm providing and installs to the first partition.

[http://paste.ubuntu.com/6526652/](http://paste.ubuntu.com/6526652/)
This may be related to the error I asked you about previously because boot-info shows an error that might explain why grub is attempted to being installed in the first partition.

> According to the info in the boot sector, sdh2 starts  at sector 0. But according to the info from fdisk,  sdh2 starts at sector 1044480.

---

### Post by oldfred on 2013-12-05
The first partition on your Windows drive is a Windows recovery or its repair. With BIOS that was part of the hidden 100MB boot partition.
I would just delete both sdh1 & sdh2 and create one new sdh1 partition FAT32 with the boot flag.
If it still then has an error, you can run chkdsk from Windows on it or from Linux run this. It should fix that start error as chkdsk or repairs also update PBR or partition boot sector (which is not used in UEFI, but is in BIOS).

       sudo /sbin/fsck.vfat -V <the fat32 device>
or
sudo fsck -t vfat /dev/sdh1
or

 Must be unmounted
sudo dosfsck -t -a -w /dev/sdh1

If you look at this I think it is saying the above commands are all the same.
man fsck.vfat

---

### Post by dss1873 on 2013-12-05
Did the following, but it didn't fix the error (I tried the other commands as well). A couple of days prior when I had used chkdsk, it also reported no errors on sdh1.

ubuntu@ubuntu:~$ sudo /sbin/fsck.vfat -V /dev/sdh
dosfsck 3.0.16, 01 Mar 2013, FAT32, LFN
Logical sector size is zero.
ubuntu@ubuntu:~$ sudo dosfsck -t -a -w -V /dev/sdh1
dosfsck 3.0.16, 01 Mar 2013, FAT32, LFN
Starting check/repair pass.
Starting verification pass.
/dev/sdh1: 1 files, 1/302442 clusters

Boot-Repair info still shows the same error on sdh1:
[http://paste.ubuntu.com/6527085/](http://paste.ubuntu.com/6527085/)

---

### Post by oldfred on 2013-12-05
Unrelated, I think but Boot-Repair says you left Windows with fast boot on and secure boot on. Both of those do cause issues in many cases.

But I do not understand issue with your FAT32 partition on sdh1. How are you formatting it? With gparted? or Windows? 
I formatted my flash drive with gparted and it just shows as vfat and no errors. But I cannot actually use the efi partition as I only have BIOS currently.

```
Disk /dev/sdb: 31.0 GB, 30992891904 bytes
255 heads, 63 sectors/track, 3768 cylinders, total 60532992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1    60,532,991    60,532,991  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              40       976,895       976,856 EFI System partition
/dev/sdb2         976,896       978,943         2,048 BIOS Boot partition
/dev/sdb3         978,944    29,650,943    28,672,000 Data partition (Windows/Linux)
/dev/sdb4      29,650,944    60,532,735    30,881,792 Data partition (Windows/Linux)

```

```
sdb1: _________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/tools/shellx64_v1.efi /efi/tools/shellx64_v2.efi 
                       /efi/ubuntu/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/tools/extras/diskpart.efi 
                       /efi/tools/extras/efichk.efi 
                       /efi/tools/extras/efifmt.efi

```

All the efi files I have are from Duet which really is meant to boot Windows with UEFI from a BIOS system, but I wanted to try it with Ubuntu. I get it to boot to duet UEFI shell, but the version I downloaded does not work with AHCI nor USB keyboards and I do not want to convert system just to test.

---

### Post by dss1873 on 2013-12-05
I didn't think that fast boot was on, but let me double check. I left secue boot on as ubuntu live wa booting just fine with it on.

I had tried turning uefi and secure boot both off at one point, but received a lot of errors.

I  have been using gparted to partition everyhing. I had also tried the install on a different usb drive just to make sure it wasn't somethjing peculiar to the Sandisk, but had the same problem.

I can try going through everything again with secure boot off.

---

### Post by dss1873 on 2013-12-09
I did not see a fast boot option anywhere in the Bios settings. I tried the install with secure boot off and received an error that I had received previously: Executing 'grub-install dummy' failed. I searched for this error and then tried running

sudo dosfsck -r /dev/sdh1

per one suggestion. Dosfsck found a possible error (a dirty bit) which I let it correct. Ran install again and received the same error.

I'm wondering as the Ubuntu live version that boots and runs is installed as a single partition which is FAT32, can I format my Sandisk as a single FAT32 partition and do the install on that?

---

### Post by oldfred on 2013-12-09
The installer is just FAT32 for the small flash drives.
You actual Ubuntu install needs Linux formatted partitions.

Did you try letting Boot-Repair install grub to the internal drive's efi partition. Then copy the files from that partition to the external drives efi partition. Sometimes it takes  a reboot or two for UEFI to find new efi partitions.

       Users who manually moved efi files around:
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)


 Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378  by ubfan1
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)
On the Ubuntu filessystem, you should have the signed versions of the following: /usr/lib/shm/shim.efi.signed, /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed. 
Copy them all onto the USB stick .../EFI/ubuntu directory without the ".signed" extension. 
Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi. 
Also copy the grubx64.efi to the EFI/Boot/grubx64.efi. 
There should be the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg

---

### Post by dss1873 on 2013-12-09
Thanks. I've posted a bug report #1259047 so let's see where that leads. They want me to use the latest release and try that.

This has taken way too much of my time and effort already for what I was expecting would be something quick and easy to try out Ubuntu. I'm not necessarily giving up, but am going to have to slow way down on the time I'm putting in to try things out.

I wanted to thank you again for all your help. It's greatly appreciated.

---

