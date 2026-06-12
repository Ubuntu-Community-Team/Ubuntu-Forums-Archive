---
title: "Accidentally deleted all kernels."
date: 2017-04-18
forum: New to Ubuntu
---

### Post by roseruby on 2017-04-18
I accidentally deleted all my kernels when trying to make space to run an update, and now am trying to follow the steps on: [https://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](https://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels) but am stuck on step 6. (very big newb here) and have no idea which one is my partition.
This is the output from the terminal:
Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size   File system  Name  Flags
 1      1049kB  538MB   537MB  fat32              boot, esp
 2      538MB   794MB   256MB  ext2
 3      794MB   1000GB  999GB                     lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 995GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  995GB  995GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4169MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  4169MB  4169MB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVDRAM GHB0N (scsi)                                       
Disk /dev/sr0: 1554MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      7389kB  9880kB  2490kB               EFI

If I've somehow screwed something up to the point of no return is there anyway to recover some of my files and photos before doing a clean install?

---

### Post by Autodave on 2017-04-18
Can't help you with the deleted kernel issue, but if you boot the PC using the same disk or USB image that you used to install Ubuntu, you can chose "Try Ubuntu" when prompted. You will then be able to access the HD and be able to copy your files to an external source.

Hopefully someone else can help you get your system back. But in any case, you still need to get a backup copy of stuff you don't want to lose.

---

### Post by roseruby on 2017-04-18
Thank you I didn't realise I could still access my files from the live cd. Will be making a back up just in case I need to do a clean install.

---

### Post by sp40140 on 2017-04-18
Also, a while ago, I broke my Ubuntu install as well. When I booted with installer (a bootable usb), I vaguely remember ubuntu giving me an option to "repair" ( not sure) or me just installing on same partition, just fixed the issues and all of my data and configs were there as before the crash.

---

### Post by oldfred on 2017-04-18
Boot-Repair's advanced mode has the reinstall of grub and a checkbox for including newest kernel.

But Boot-Repair has issues with LVM with encryption. Just make sure you have mounted the LVM and given password to unencrypt your system.
Both RAID & LVM use /mapper, so Boot-Repair tries to figure out which you have but does not always work & then encryption prevents it from seeing / (root).

See the first steps to mount your encrypted LVM up to the part where it says you can now do other repairs or maintenance.
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641) 

The old instructions also were before UEFI. So you also have to mount your ESP - efi system partition.

I do not know LVM, if someone does that would be better to help this user.

---

### Post by roseruby on 2017-04-19
> **oldfred said:**
> Boot-Repair's advanced mode has the reinstall of grub and a checkbox for including newest kernel.

But Boot-Repair has issues with LVM with encryption. Just make sure you have mounted the LVM and given password to unencrypt your system.
Both RAID & LVM use /mapper, so Boot-Repair tries to figure out which you have but does not always work & then encryption prevents it from seeing / (root).

See the first steps to mount your encrypted LVM up to the part where it says you can now do other repairs or maintenance.
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641) 

The old instructions also were before UEFI. So you also have to mount your ESP - efi system partition.

I do not know LVM, if someone does that would be better to help this user.

I checked out the link, but it's way over my head and I don't understand what it is I'm suppose to be doing?
Follow the steps from step 1?, sorry really big newbie here.
Also I got a back up of all my folders and photos but is it possible to somehow back up all the bookmarks I had in my browser?

---

### Post by oldfred on 2017-04-19
You can backup or copy the entire Firefox profile, same with Thunderbird profile.

       [http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced](http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced)
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I do not consider LVM for new users. But it you need full drive encryption you have to use LVM. Then you need to learn all about LVM.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by Enigma12 on 2017-04-19
> is it possible to somehow back up all the bookmarks I had in my browser?

If you used Firefox, you should find a (usually hidden) folder in your /Home folder named .Mozilla. A sub-folder to that one is called Firefox. This contains pretty much everything about Firefox. Save that Firefox folder to a thumb drive. Then once you've gotten your new kernal working,, run Firefox once, then close it, then copy that Firefox folder into the new .Mozilla folder. That has worked for me for every installation I've used.

---

### Post by Geoffrey_Arndt on 2017-04-19
Plus, these days, it's really smart to set up "sync" on Firefox and any other browsers you use.   Very simple to do . . . after clicking the right option in preferences, you basically register on the Firefox server and from then on, all your bookmarks are saved and synced across machines.

---

### Post by roseruby on 2017-04-20
Hi everyone, Thank you so much for all the help so far.

Decided to reinstall ubuntu but now ran into a new problem :/
When the install starts a window popped up saying Installation Failed:

The installer encountered an error copying files to the hard disk: [Errno 5] Input/output error This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

The CD I'm using is new and seems clean with no damage, I chose the slower burning option when I burnt the CD.
Can't see any dusk in the drive (haven't opened up the desktop though, just peeked through the slot where the CD's inserted) and left my computer off for a while to let it fully cool down before trying to install it again but got the same message.
Ran the 'Check disc for defects' and got a 1 error found.

Do I try and burn another iso to another disc or is there something I'm doing wrong?

---

### Post by oldfred on 2017-04-20
That is why years ago I changed to use flash drives. They are reusable.
I used to also burn several repair CD as part of new install. So I had gparted, Boot-Repair, Parted Rescue and others.
But then made lots of coasters (bad burns, errors). 
With flash drive I can updated and reuse it.

If you have any error on download or on CD/DVD drive you must redo it. You are using DVD, you mention CD?

---

### Post by roseruby on 2017-04-21
Thank you for the reply. 
Yes I am using a DVD-R, sorry used to calling it CD out of habit.
I will try burning a new DVD when I have time in the morning, if that doesn't work I'll go and buy a flash drive to use instead.

---

### Post by NM5TF on 2017-04-21
I am also curious why a self-described "big newbie" would chose to go with LVM....not something
for the faint of heart....

anyway, you might find something useful here:  [COLOR="#FF0000"]http://tldp.org/HOWTO/LVM-HOWTO/intro.html[/COLOR]

good luck....

---

### Post by roseruby on 2017-04-22
update on whats happening:
Tried another DVD-R got the same 1 error when I ran 'Check disc for defects' on it so went out and got a flash drive but when I ran the check I got the same error.
got the iso downloaded on another computer before I put it on the discs or usb.
Not sure what I'm doing wrong, going to try and download the iso again and try again.
To NM5TF: When making the switch from windows I was following all the install instructions from a magazine and it said to use it.

---

### Post by oldfred on 2017-04-22
Only those new users that want or need full drive encryption which requires LVM should be using it.
And it has a steeper learning curve as you must use LVM tools in addition to standard partition tools. The logical volumes are like partitions inside the standard partitions which makes it more complicated.

And with encryption you absolutely must have really good regular backups. Often a normally repairable error cannot be fixed when inside encryption and LVM. 
But you should have good backups of all your data anyway.

What tools are you using to download & then install to flash drive.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
            Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by roseruby on 2017-04-23
Thank you oldfred for all your time and patience.
Lesson learnt, will never heedlessly follow step by step magazines instructions without having at least some knowledge on what I'm installing ever again.

I downloaded the iso from [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
then burned the iso onto a disc, for the flash drive attempt I used these instructions: [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu).
In both disc and flash drive I can 'try unbuntu without installing' but not install. 
 
Did not know about the MD5SUM, checked it and the iso hash does not match so am downloading it again ( is taking awhile took half a day last time )
Will let you know how it goes.

---

### Post by roseruby on 2017-04-23
Thank you!
Computer works again!
This time the downloaded iso didn't have any errors and I reinstalled everything without a hitch (making sure to leave LVM and encryption unchecked this time and well alone).
Big big thank you oldfred for all your guidence and patience, was having a really bad week and all your help really means a lot to me. Thank you :)

---

### Post by oldfred on 2017-04-23
Glad you got it working. :)

---

