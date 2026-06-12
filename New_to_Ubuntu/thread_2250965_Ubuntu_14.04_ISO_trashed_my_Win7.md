---
title: "Ubuntu 14.04 ISO trashed my Win7"
date: 2014-11-01
forum: New to Ubuntu
---

### Post by voxmagna on 2014-11-01
Hi, I had a much older version of Ubuntu installed on a single drive in a EXT partition and coexisting with FAT formatted Win XP. I don't let Ubuntu modify the XP boot loader for XP. I have GRUB installed on a flash card and when I need Ubuntu the PC boots GRUB from the external card. I do this because Ubuntu is then not visible to other users and the PC boots up into XP. 

I now have a newer PC with a 320 Gb drive which came pre-installed with Win8_64.  I wanted Win7 with Ubuntu 14 and after nuking the hard drive and setting the BIOS switches for non-compatible UEFI I created 2 NTFS partitions and installed Win7 on the root 'C'. Then in preparation for Ubuntu 14 I created EXT4 and SWAP partitions. I wanted to be absolutely sure that my Win7 NTFS partitions remained untouched after the Ubuntu install. I executed the Ubuntu install and went for the last option, choosing the EXT4 partition for the Ubuntu root and a USB flash stick for the boot files. 

**To my horror the whole hard drive had new partions created which I didn't recognise**  - they were not NTFS (GPT I think), including a restore partition which is exclusive to windows 8 not windows 7!

I now have go back and find out what went wrong, but clearly something in the Ubuntu install may be responsible and working with the BIOS,drive or PC firmware to make the world Windows 8! Unfortunately I created a third NTFS partition holding holding a backup image of the working install - that got trashed to. Moral is don't put image backups in a separate partition on the same drive.

I have a thought that my new PC BIOS is UEFI compatible and although the BIOS switches are set for compatibility, does Ubuntu 14 pick this up and reformat the whole disc to be compatible with Win 8, or is it something to do with newer hard drives and GPT format? 

I thought I was picking the safest way to keep my existing Win7 O.S intact. It was a big mistake and I hope others don't repeat what I did.

I will try downgrading the PC BIOS to the non-UEFI version and Nuke the drive again, which might stop any attempt by a formatter to make it Win8 compatible.

Has anybody got ideas on where I went wrong? 

How can I can SAFELY install Ubuntu on a NTFS drive to a pre-formatted EXT4 partition and GRUB loader on a memory stick, without the installer modifying the MBR on my existing (NTFS) partitions?

---

### Post by sudodus on 2014-11-01
I'm not sure what went wrong, but if you used 'Install alongside' at the partitioning window, you might have been hit by this bug.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

It is in the process of being squashed ... there seems to be a solution, but it is not in the current iso files.

It should work properly if you use 'Something else', which means manual partitioning. (It has always worked for me, and I have not heard of any bug, so, 'Something else' should be safe, it gives you control of the partitioning.)

---

### Post by voxmagna on 2014-11-01
Thanks, I did use 'Something Else' and it did appear to give me all the options I wanted but you are blind as soon as the install starts. If it was going to trash my Windoze install it should have come back with a warning. I just tried to 'downgrade' the BIOS to non-UEFI and the Acer BIOS installer said no. So I am back to thinking that even though the BIOS is set to legacy and the hard drive is nuked clean, there is something going on which makes Ubuntu think I have Win 8 on the target drive and create GPT partitions with this recovery partition with a name like'single key recover', or something like that. 

I'm really struggling on this and I'm wondering if I should now run the Ubuntu ISO to install to USB flash then move the image to my ETC hard drive partition. At least I know that isn't going to corrupt my existing and I am not blind to what is happening as with the ISO install. Can I move a Ubuntu install from flash to my hard drive and sort out the GRUB?

---

### Post by grahammechanical on 2014-11-01
What does "nuked the hard drive" mean.

I am a little surprised that a Linux installer would create a Windows 8 restore partition. If Windows 8 is installed in EFI mode and Ubuntu is installed in EFI mode then it will make use of the existing EFI partition that Windows 8 stores its boot loader files in. This is my understanding. As far as my experience goes the Something Else option does not create partitions that the user does not instruct the partitioner to create.

With the Something Else option the partitioner shows us all the partitions on the hard disk. Surely it would have shown these NTFS partitions. Did it?

Regards.

---

### Post by whitesmith on 2014-11-01
Here, exactly, is what I would do:

Wipe the drive and go with GPT; older methods can't handle larger drives and it won't be long before you'll need > 3+ GB, the limit when you've formatted MBR (unless you play games with extenders, and this is so 1990s).

Install Ubuntu 14.04.1 LTS. Format for ext4. 

If you *must* use that Other Operating System, you know, the costly choice that so many prefer because it's "simple," then run that thing as a VM (VirtualBox is my preference) under Linux. Loads are lightning fast and (almost) everything works just fine, except for USB that requires a proprietary extension. I am a software professional, not a gamer, so it may be that games are not 100% under VirtualBox. Check their website.

If you follow these rules you'll uncomplicate your life and have a reliable system that runs without problems.

Forget about dual boot and all workarounds. Why workaround when you can simply work? Regards.

---

### Post by sudodus on 2014-11-01
The problem can also be that the operating system does not see 'everything' depending on the UEFI/BIOS system, or that some traces are left in the beginning of the drive, which makes the installation follow a route, that you don't want.

Yes, it is possible to clone an installed system from a USB drive to an internal drive and vice versa. I have done it many times.

I have also used ***rsync*** and ***tar*** to copy the files in the root partition and after that installed the grub bootloader to boot into it. This method is reliable at least with old style BIOS and MSDOS partitioning, but more complicated with UEFI and GPT. If you want to avoid GPT, maybe you should wipe the first megabyte with ***mkusb*** and start with a fresh partition table using ***gparted*** (in both cases when booted from a live drive (booted from DVD/USB).

If you install Windows after Ubuntu, the bootloader will be overwritten, and you have to (re-)install grub to make it a dual boot system. But it is not too difficult, see

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by oldfred on 2014-11-01
How did you install Windows 7. It default install usually converts the Windows 8 drive from gpt to MBR(msdos), but does it incorrectly. It leaves the backup gpt partition table and then you have issues in Linux as both MBR & gpt is seen.
If you installed Windows 7 in UEFI mode then drive is still gpt and Ubuntu using Something Else would not erase Windows. And the bug where drive is erased erases everything including recovery partitions.

Post this from Live install:
sudo parted -l

Windows only boots from gpt partitioned drives with UEFI and requires several extra partitions if you partition in advance.
Both Windows and Ubuntu only boot in BIOS mode from MBR drives.
But Ubuntu will install in either UEFI or BIOS boot mode depending on how you boot install media if drive is gpt.
And always best to have both systems UEFI or both BIOS.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by voxmagna on 2014-11-01
> What does "nuked the hard drive" mean.

Sorry, I use dareks 'nuke' which erases everything on a drive and fills with '1's or a pattern. Anything lurking put on by the oem PC manufacture should be erased, but never sure with these new large drives and format changes.

> How did you install Windows 7. It default install usually converts the Windows 8 drive from gpt to MBR(msdos)

I formatted the clean drive with 2 partitions NTFS for windoze, a EXT3 and swap partition to receive Ubuntu. I gave the windoze installer the AHCI drivers at F6 and had set the bios to MBR compatibility mode not UEFI. I am pretty sure the drive was not converted to GPT, but since I am repeating the install  with an image backup this time. I will check immediately after. I know GPT is mandatory for win8 but I didn't think it was for Win7_32 which is why I'm using it. I am only setting up the drive with 4 partitions which worked fine for an earlier Ubuntu with XP on a non UEFI drive in the first 2 partitions. I will settle for both bios MBR, because all my utilities work with the older format and I am not creating lots of partitions.

> The problem can also be that the operating system does not see 'everything' depending on the UEFI/BIOS system, or that some traces are left in the beginning of the drive, which makes the installation follow a route, that you don't want.

Yes that is my suspicion.

> Yes, it is possible to clone an installed system from a USB drive to an internal drive and vice versa. I have done it many times.

That is the way i'm heading once I confirm a Windoze7 install still leaves me with the same msdos partition structure.

The one thing I wanted to try was remove UEFI completely from the bios because MBR compatibility could mean an OS installer might still be able to get around that.

That is a good point about other data on a hard drive. These new drives have 'Drive lock' with password options in the bios. I don't have any passwords set, but it suggests there may be a data area or eeprom storage with code I have not erased or can see with partition tools.

Will post a follow up after some more work.

---

### Post by oldfred on 2014-11-01
If drive was gpt run this. 
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

Windows 7 or 8 can be installed in UEFI mode or BIOS boot mode. 
But if Windows BIOS boot drive must be MBR, and if UEFI drive must be gpt partitioned.
And now you boot installer is how it will want to install, UEFI or BIOS, best to have partitioning match before installing or have a blank drive.

---

### Post by voxmagna on 2014-11-01
Repeating what I did:

Win7_32 definitely on same msdos partitions with mbr and is in bios boot mode. All my partitions are as before 3@NTFS,EXT4,SWAP and unallocated.
The first 2 partitions were setup and running Win7 fine. After Ubuntu was told to use the EXT partition and changed the entire disc, no partitions labelled GPT were anything like the sizes of my original NTFS so I assumed it trashed them. The only partition that could have held about the right size of data Win7 OS + Apps was labelled 'single button recover' or something like that. I think that is a Win8 feature and since I deleted the oem install from Win8_64 to get a clean Win7 install, I couldn't recover it anyway (without putting back Win8).

I think Windoze 8 is really good news for Linux users, because it really shows how MS can shackle an OS so much that working with it is like moving through treacle.

---

### Post by oldfred on 2014-11-01
Partitions are not labeled gpt, partitions have formats like NTFS for Windows or ext4 for Linux.

The underlying partition structure is either gpt or MBR(msdos).

Post this:
sudo parted -l
sudo fdisk -lu

---

### Post by voxmagna on 2014-11-02
Maybe not on the Parted world. But in Windoze using MiniTool Partition Panager I've trusted for a long time, it reported the partitions as gpt. The fact that any of the original disc structure got changed after I executed Ubuntu 14 to install to a specific partition already set up is what concerns me.

---

### Post by oldfred on 2014-11-02
Again almost every user that installs Windows 7 over Windows 8 uses BIOS/MBR mode not UEFI/gpt. 
And the Windows 7 installer does not correctly convert from gpt to MBR. You have a MBR primary (only one with MBR) and the gpt backup partition table. 
Linux tools see both and report it as an issue or do not work, or only erase drive if you so say you want to convert fully to one or the other.

Not sure when you have both MBR and backup gpt what other partition tools report.

---

### Post by voxmagna on 2014-11-02
I didn't install the way most do, which is the roll back route Win8 to Win7, already read the horror stories about that and we all know these kind of major MS routines carry a risk of failure.

1. You can't get the HDD formatted internally as DOS MBR in the original machine because the UEFI BIOS protection stops it. You get really screwed with BIOS/hard drive protection and DOS partition utilites not working. I think this is why most go the route of converting the HDD format from gpt to DOS/MBR as MS says, because they've made it so difficult. I'm choosing Win7_32 as my first partition install before Ubuntu 14 32 bit. If I went 64 bit, I would be forced into a Windoze gpt install. The rest of the world may have been pushed to 64 bit, but I'm quite happy with 32 bit for what I run.
2. I physically removed the HDD from the laptop Nuked it (secure erase), then formatted it DOS/MBR on an XP machine (No UEFI/gpt) The drive was absolutely clean as far as I could tell.
3. The clean drive was replaced in the laptop with the BIOS set to run only legacy BIOS/MBR. I saw no gpt partition backup.
4. Windoze 7 was installed to the DOS NTFS partition with oem F6 AHCI drivers.
5. Windows install was checked and there were no gpt partitions or any I did not create on the drive.
6. I used Ubuntu 14 ISO to supposedly install to the EXT4 partition I had reserved.
7. I did not tell Ubuntu to mess with my partitions. But it did and seemed to create GPT partitions.
8. Now I don't trust what the installer is doing I will disconnect my local DOS/MBR fat drives on a second machine, Plug in a spare 8Gb USB stick and get the installer to install Ubuntu 14 on that, whilst telling it to create the GRUB boot on a second smaller flash stick.
9. Confident there is no Ubuntu installer to do things in the background I don't want, I hope I will end up with Ubuntu on the 8Gb stick booting from a smaller stick or card.
10. Then I will try transplanting the USB install on to a pre-formatted EXT4 partition on the hard drive.
I suspect I could have issues with drive letter and partition recognition, but that's nothing compared to getting a trashed drive.

---

### Post by oldfred on 2014-11-02
If using Ubunt 32bit ISO it will not install in UEFI mode and then I do not think it uses gpt unless drive is over 1+TB and drive is totally blank. It will just use the MBR partition and install in BIOS boot mode.

We have seen Windows 8 64 bit installed in BIOS boot mode. It just is how you boot installer on how it installs to hard drive. BIOS boot will always install in BIOS boot mode on hard drive.

When you installed Ubuntu did you use one of the auto install options or the Something Else and manual install?

Copying an install has lots of UUID and drive issues. It can be done but you have to update/reinstall grub, update fstab and a few other entries with new UUID & drive info.

I would liked to have see Boot-Repair's summary report before & after install to confirm. It there really is an issue it needs to be reported as a bug, but they want lots of detail and will not recognize just a complaint as it often then is user error. This is a reported bug on Ubuntu overwriting entire drive with UEFI installs and using auto install option only but only with re-installs. And LVM auto installs are always a full drive install.

---

### Post by voxmagna on 2014-12-03
Hi All, I've been quiet for a while whilst I restore and repair my Win7_32 OS and reconsider my approach to a future Ubuntu 14.04 Install.

Call me a wimp but I decided having Ubuntu do its own install on a working Windoze platform without any control over what it could do to my hard drive and win OS was a risk I wasn't going to repeat. My suspicion is the installer is written to recognise Windows installed, then creates the dual boot option since that is how most would want it (even though I selected the 'no' option). I've worked with dual boot loaders before and they are a pain when they fail and always modify the MBR. As I said, I already had Ubuntu 8 installed in a EXT3 partition co-existing with XP and not modifying its NTFS partitions. I could boot the Ubuntu OS with a SD card or USB pen holding the GRUB boot. Unfortunately, I can't remember how I was able to get Ubuntu 8 on the hard drive alongside XP NTFS partitions to be invisible to XP but active when booted from the SD card.

If I could have found a certain way to protect my XP FAT32 partitions from writes, I would have given the Ubuntu installer a second chance.

I have now decided that Ubuntu is safest being installed to run in its own primary drive and partition.  I've tested a few USB flash drives for speed and Sandisk Extreme USB3 will do 160mb/s read and 60Mb/s writes which is not far off SATA I.  Yes I know flash is supposed to have limited writes before failure, but once an image backup is taken it is easily cloned.

One nice thing about doing the full install on USB is Ubuntu 'worked' when I transferred it to my desktop PC. Being used to Windoze I was surprised because the hardware on my laptop and PC is different, although they both use Intel CPUs - How does it do that? That is useful because I can do work on the desktop, then switch the USB stick back to the laptop when I'm travelling.

The first annoying thing I found is Ubuntu did not allow me to control the screen brightness of my Acer Travelmate screen. Travelmates use Intel GFX drivers. This is pretty disappointing because nobody wants to run a new OS without control of the screen. If you use command lines a lot, the blacks are washed out by excessive brightness. Now, I did find a way of changing the GRUB boot line so the system settings brightness bar would work, but Oh so sadly it doesn't remember screen brightness settings across re-boots.  Under Windoze, Intel provide a tray App with their drivers which allows all the screen parameters to be customized (and remembered!). The problem with the Travelmate and most laptop screens is their poor displays and default contrast settings. The best way to fix them is not with brightness adjustment but by changing gamma. So I had to write a couple of lines of script to start up my screen gamma to 0.6. Life should have been easier!

Thanks again for your help and replies.

---

### Post by sudodus on 2014-12-03
> **voxmagna said:**
> ...
One nice thing about doing the full install on USB is Ubuntu 'worked' when I transferred it to my desktop PC. Being used to Windoze I was surprised because the hardware on my laptop and PC is different, although they both use Intel CPUs - How does it do that? That is useful because I can do work on the desktop, then switch the USB stick back to the laptop when I'm travelling.
...

As long as you use the free and built-in drivers (for example for graphics and wifi), things are detected and the correct driver used automatically (in run-time). I agree that this portability is a great feature :-)

If your computer has a graphics chip or wifi chip or there is some other hardware device, where you need to install a proprietary driver, you will loose the portability.

> ...The best way to fix them is not with brightness adjustment but by  changing gamma. So I had to write a couple of lines of script to start  up my screen gamma to 0.6. Life should have been easier! 

Please share your script for brightness adjustment!

---

