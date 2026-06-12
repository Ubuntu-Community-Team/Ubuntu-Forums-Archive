---
title: "Ubuntu is installed on drive but can't seem to boot it"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by Kris_Nakamura on 2014-08-30
Hello,

I am extremely new to ubuntu (have only used it slightly on school computers) and may have done something wrong.
I have tried multiple times to try and install it on my laptop -- which has no OS on it according at boot -- and I can't seem to figure out why.
After browsing forums I tried to use boot-repair but it didn't fix my problem.

This is the link it provided at the end: [http://paste.ubuntu.com/8187652](http://paste.ubuntu.com/8187652)

Any help is appreciated,
Thanks!
-Kris

---

### Post by fantab on 2014-08-30
```
Model: ATA TOSHIBA THNSNF12 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
1      1049kB  538MB  537MB  fat32        EFI System Partition  boot
2      538MB   794MB  256MB  ext2
**3      794MB   128GB  127GB                                     lvm**
```

Ubuntu / and swap are 'lvm'. Most of us here don't use LVM as 'default' is ext4.
Following pages might help:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

or if you dodn't know why you have 'lvm', then you can can delete the 'lvm' partition, create ext4 partitions and install ubuntu all over again. Use [Gparted]("http://www.dedoimedo.com/computers/gparted.html") (partition utility) from Live Ubuntu DVD/USB.

---

### Post by Kris_Nakamura on 2014-08-30
Thanks for the input!  Unfortunately it still doesn't work when I change the lvm to ext4.  I also believe that happened during the multiple times I tried to install Ubuntu with different options.

I changed it to ext4 (at least I'm pretty sure I did?) but it still doesn't boot up.  Here's an updated boot-repair report:  [http://paste.ubuntu.com/8192744](http://paste.ubuntu.com/8192744)

-Kris

---

### Post by whitesmith on 2014-08-30
From line 73 of the last Boot Info Script you provided:```
/dev/sdb1    *             63    15,154,271    15,154,209   c W95 FAT32 (LBA)
```
Linux won't boot on a Windows partition (FAT32, for example). I would reinstall and keep it simple by giving the whole disk to Ubuntu. If you need Windows you can easily set up a VM to handle apps that require it. Cheers.

---

### Post by fantab on 2014-08-30
/dev/sdb is the live USB... and it is where ubuntu live boots from. 

> UEFI/Legacy mode:
Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
**Secure Boot enabled**.

Have you disabled 'Secure Boot'? Disable it if you haven't already.

> BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0004,0001,0000,0003,0002
Boot0000* USB Memory
Boot0001* HDD/SSD
Boot0002* LAN2
Boot0003* LAN1
Boot0004* ubuntu.

Also check in UEFI menu to see if you: 
1. have UEFI enabled
2. have default OS to boot is set to 'Ubuntu'...

---

### Post by Kris_Nakamura on 2014-08-31
I have disabled secure boot, checked and the BIOS states that UEFI is already enabled.  I cant seem to find where I would change a setting to have the default OS as Ubuntu (but there isn't any other OS on this computer so shouldn't be much of a problem?)  I have also been browsing the forums to see if it has anything to do with my computer, some people have had problems with the internal LAN being enabled.  I have tried everything I just mentioned but it still hasn't worked..
Also I found this [http://tombuntu.com/index.php/2011/09/25/how-to-change-boot-order-in-ubuntu-11-04/](http://tombuntu.com/index.php/2011/09/25/how-to-change-boot-order-in-ubuntu-11-04/) and tried to utilize it but when I try it states that I need to install gksu.  When I try to install it, it states that it has no installation candidate and I can't use the commands listed there.

Again, since whitesmith brought it up, I am NOT trying to dual boot windows on the drive.  I am trying to solely run Ubuntu without any other OS installed.

The most updated boot-repair file [http://paste.ubuntu.com/8196299/](http://paste.ubuntu.com/8196299/)

I wonder if my problem is something really complex or if its just something really simple and stupid....
Thank you for your continuous help,
-Kris

---

### Post by fantab on 2014-08-31
There should be UEFI boot order, most of 'em have, for instance see [this image]("https://help.ubuntu.com/community/UEFI#Disabling_SecureBoot_in_the_BIOS")...

By the way, what hardware specs do you have there on your lap/desktop?
What partitioning tool did you use to create partitions on the HDD?
I don't use LVM and I am not sure what this is:
> sda3: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type 'swsuspend'


... however 'parted -l' shows the partition as 'swap'.

From the terminal post the output of:
```
sudo gdisk /dev/sda
```
About [gdisk]("http://www.rodsbooks.com/gdisk/walkthrough.html").

---

### Post by Kris_Nakamura on 2014-08-31
My boot is set to start from the Drive.  
Specs on my laptop is:
Toshiba Portege Z935
Memory: 5.7GiB
Processor: Intel Core i5-3337U CPU @1.8GHz x 4
Graphics: Intel Ivybridge Mobile

For partitioning, I just let Ubuntu do its own install so I didn't really do anything manually. 

GPT fdisk (gdisk) version 0.8.8
Partition table scan:
MBR: protective
BSD: not present
APM: not present
GPT: present
Found valid GPT with protective MBR; using GPT.

-Kris

---

### Post by JeQhdMD on 2014-09-01
If you're wanting Ubuntu as the sole OS on the machine, why not just reformat the whole drive (sda) with ext4 and one swap parttion using gparted live CD or Parted Magic Live CD.   Then when booting up the Live USB flash stick (sdb) . . . start the install process and specify ubuntu to utilize the whole disk (sda).   Be sure to check that Grub is being installed to sda (where it will be installed to sda1 typically).

Be sure you don't initially have any MS type file systems like fat16, fat32, ntfs, etc. on sda.   Later on, after installing ubuntu, you can repartition the one large partition you have (leave swap alone), and then use the other partitions for backup or for loading other linux distros.

Be sure the Ubuntu live media (flash stick) is using the 64 bit version of ubuntu.   And if secure boot is turned off, the standard install process should do the rest.    I think your problem may be the windows file systems on sda . . . get rid of them, you don't need any for now.

---

### Post by Kris_Nakamura on 2014-09-01
I have windows file systems on my drive?  I thought I wiped everything clean.  I'll try start again from a blank.

Thanks,
-Kris

PS: I have no idea how to check or specify where Grub is being installed, but one thing I realized after doing "sudo fdisk -l" (and also as I wrote in response to fantab's "sudo gdisk /dev/sda") is that my System is specified as a GPT instead of Linux as I see other people's system states.  I tried wiping my whole drive using gparted and reinstalled Ubuntu using the automatic settings but it still stays that way.  How do I change/how do I tell Ubuntu to install as a Linux system instead of what this 'GPT' is?

---

### Post by dave131 on 2014-09-01
I *think* GPT is the new partitioning scheme instead of the old one - there are no partition limits (that I know of) when using GPT.  I also *think* GPT is there because of UEFI - but I might be wrong on that.  I am also curious as to why you tried lvm?  I know it is supposed to make managing partitions easier, but I'm not sure if that might not be complicating things for you right now.  What I would try:

- reboot using the installation media (be it USB or DVD or whatever)
- when it gets to the part about how you want to use your disk, do as others have directed above and select use entire disk, and at the bottom of that screen be sure it will be installing grub boot loader to /dev/sda
- let the installation finish
- when you reboot to try the new installation, I would first go into the BIOS setup for your PC and be sure that the hard disk is included in the boot list - perhaps USB first, DVD/CD second, and the hard disk 3rd.

---

### Post by Kris_Nakamura on 2014-09-01
Again, I'm not too sure how or what I'm doing overall, I put the usb drive in, pressed install Ubuntu (using default settings, nothing in advanced) and because of that, I don't really see any choices of where grub boot loader is being installed.  And since the OS hasn't been working since forever, I haven't changed the hard disk being first to boot up option for a while.

During the course of the day, I managed to find in the forums on how to possibly install grub in the proper place : [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
but when I tried to do what was listed on the instructions, it all goes well until I try to grub-install /dev/sda.  Then it gives me an error saying cannot find EFI directory.  All of this is extremely confusing to me and all I could do was run boot-repair again and get another link: (not sure how much is changing each time really...) [http://paste.ubuntu.com/8205693](http://paste.ubuntu.com/8205693)

**MY MAIN THOUGHT**: Everyone's been bringing it up and I've seen it here and there on the forums too and I feel like my problem is that grub boot loader isn't being installed into /dev/sda?  I have no idea how to set it to do that nor am I too sure how to install it into /dev/sda manually from the live cd.  As I post this, im still going to try and see how to do this.

Really appreciate all the help!,
-Kris

---

### Post by fantab on 2014-09-01
GPT or GUID Partition Table is the new gen partition table and it is replacing 'msdos' as default partition table on HDD/SSD. No problem here.
[Advantages of GPT]("https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT")
Since you have already formatted the HDD, lets see the new:
```
sudo parted -l
```

---

### Post by Kris_Nakamura on 2014-09-01
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA THNSNF12 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

[TABLE="width: 100"]
[TR]
[TD]Number
[/TD]
[TD]Start
[/TD]
[TD]End
[/TD]
[TD]Size
[/TD]
[TD]File systems
[/TD]
[TD]Name
[/TD]
[TD]Flags
[/TD]
[/TR]
[TR]
[TD]1
[/TD]
[TD]1049kB
[/TD]
[TD]538MB
[/TD]
[TD]537MB
[/TD]
[TD]fat32
[/TD]
[TD][/TD]
[TD]boot
[/TD]
[/TR]
[TR]
[TD]2
[/TD]
[TD]538MB
[/TD]
[TD]122GB
[/TD]
[TD]121GB
[/TD]
[TD]ext4
[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]3
[/TD]
[TD]122GB
[/TD]
[TD]128GB
[/TD]
[TD]6331MB
[/TD]
[TD]linux-swap(v1)
[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

Model: TOSHIBA TransMemory (scsi)
Disk /dev/sdb: 7759MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  7759MB  7759MB  primary  fat32        boot, lba

---

### Post by LostFarmer on 2014-09-01
I think you need to give a little more info on just what happens when you try to boot.  Do you get a grub error ?  Any thing at all happens ? Any errors at all ?

---

### Post by fantab on 2014-09-01
Run the [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") utility booting ubuntu from dvd/usb. Try 'Recommended Repair'.
_Note down the url_ it creates to the bootinfo file.

---

### Post by christopher9 on 2014-09-01
What application did you use to prepare the install USB ?  Did you run Md5sum on the .iso file after downloading ?  Do you get the option to 'try without installing' from the USB ?

---

### Post by Kris_Nakamura on 2014-09-01
Boot-repair report: [http://paste.ubuntu.com/8210561/](http://paste.ubuntu.com/8210561/)

Summary of whats happened so far:
-I've tried installing Ubuntu 14.01.1 (64-bit) using the recommended settings and it looks like it installs.
-When I try to start the computer though, (with no USB or anything with the hard drive selected as first boot) I get the message "Insert system disk in drive.  Press any key when ready... " and I can't do anything from there except to shut down the computer or press a key (which does nothing except repeat).
-I've tried running boot repair with the recommended settings but it hasn't helped.
-I've tried wiping the drive clean multiple times, formatted one large partition into an ext4 type and used recommended settings to install Ubuntu 14.01.1 but didn't work.
-I also tried installing an older version, Ubuntu 13.10 (64-bit) using recommended settings and that also ended up the same way as trying to install 14.01.1
-Secure boot is off (from BIOS menu)
-Boot mode is UEFI (from BIOS menu)

So as I mentioned in the summary, answering lostfarmer's question, I don't really get an "error".  Just a "Insert system disk in drive.  Press any key when ready..." 

To answer christopher9's question, I used Universal-USB-Installer-1.9.5.5 as was recommended from the ubuntu install site to prep the USB.  I'm not sure what that Md5sum is?  and yes the 'try without installing' is what I've been doing for the last 2 pages of this post. (since I have no other OS on the laptop)

Thanks,
-Kris

---

### Post by fantab on 2014-09-01
Ok try 'enable Secureboot' and see if Ubuntu boots. Some Uefi's need it to be 'enabled'.
[MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") and [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM") determine the integrity of your downloaded .iso. If the check fails and 'sums' don't match, it means that your .iso is corrupted. You will have redownload and re-burn it.

---

### Post by Kris_Nakamura on 2014-09-01
I tried enabling Secureboot but that didn't work. I&#822; &#822;i&#822;n&#822;s&#822;t&#822;a&#822;l&#822;l&#822;e&#822;d&#822; &#822;M&#822;D&#822;5&#822;s&#822;u&#822;m&#822; &#822;a&#822;n&#822;d&#822; &#822;i&#822;t&#822; &#822;l&#822;o&#822;o&#822;k&#822;s&#822; &#822;l&#822;i&#822;k&#822;e&#822;  &#822;m&#822;y&#822; &#822;c&#822;h&#822;e&#822;c&#822;k&#822;s&#822;u&#822;m&#822; &#822;i&#822;s&#822; &#822;d&#822;i&#822;f&#822;f&#822;e&#822;r&#822;e&#822;n&#822;t&#822;?&#822; &#822;I&#822;'&#822;l&#822;l&#822; &#822;t&#822;r&#822;y&#822;  &#822;r&#822;e&#822;d&#822;o&#822;w&#822;n&#822;l&#822;o&#822;a&#822;d&#822; &#822;t&#822;h&#822;e&#822; &#822;i&#822;s&#822;o&#822; &#822;a&#822;g&#822;a&#822;i&#822;n&#822;
Nevermind, upon downloading a new file, the checksum was exactly the same so I looked it up again.  Realized that 14.04.1 and 14.04 is not the same thing.  So my secureboot is on, my checksum on the iso is correct.
I'm just near that point of giving up with an unusable laptop for the last 4 days....

-Kris

---

### Post by fantab on 2014-09-02
Your frustration is understandable.

Ok we have one more option to try before you can take the laptop back to the authorized service center.
Since you have nothing to lose, lets delete the partition table on that HDD and create a new one.
Make sure you boot your ubuntu usb/dvd in UEFI mode only: see 

Using Gparted select 'Device' from the menu. 
From the dropdown menu select 'create new partition table'. Next choose 'gpt' and apply. This will create a new partition table and you will be left with clean disk.
Create new partitions as follows:
# 5mb _unformatted_ partition.
# 512mb FAT32 partition (you will have to place a '**boot**' flag next to it by right clicking on the partition and selecting 'manage flags'. When installing boot loader during install you have to select this partition.)
# All the spaceGB Ext4 '/'
# 2Gb linux-SWAP partition
Apply changes and quit gparted.

Install Ubuntu. During Installation, from the 'Installation Type' dialog choose "Something Else' option. This will let you guide the install to created partitions yourself.
Select the third partition, /dev/sda3 Exit4 and set it up as follows:
Use as = ext4 
mountpoint = /
format = yes

Then select your bootloader location from the same dialog:
choose the FAT32 partition or /dev/sda2.... identify it correctly.

---

### Post by Kris_Nakamura on 2014-09-02
I'd really hope doing that would have worked but it didn't... Few questions though

1: Whats the 5mb of unformatted partition for?  It says "file System: unknown" on gparted after I applied the changes and stayed that way even after the installation of Ubuntu.
2: For your instruction on selecting Use as: Ext4 for editing the partition, the only option available that was similar was "Ext4 journaling file system" is that the same thing?
3: When I did all of what you said (I switched the order of creating linux-swap partition and creating the ext4 partition) and pressed "apply changes", some drives automatically had (created?) things in them already (eg: the ext4 partition said 1GiB used)

Also like I mentioned since I switched the creation of the linux-swap partition and ext4, I also changed the installation to /dev/sda4.  I'll try do everything again with creating the ext4 partition first.

Thanks,
-Kris

---

### Post by fantab on 2014-09-02
1. We'll try an use the 5mb partition later to boot in bios/legacy/csm mode. Everything else about is normal.
2. Yes they are same.
3. That shouldn't worry you. It doesn't matter.

Lets see how it goes.

---

### Post by Kris_Nakamura on 2014-09-02
Nope, formatted everything again, went through your instructions, installed and rebooted but still not working (tried it with secure boot both on and off).

-Kris

---

### Post by fantab on 2014-09-02
Okay...
Using gparted remove the 'boot' flag from FAT32 Partition and put a 'bios_grub' flag on the 5Mb partitition we made upfront.
Get into your UEFI menu and disable UEFI boot and enable 'Legacy/CSM' boot.
Run boot-repair and post back the bootinfo file url.

Good luck...

We are trying to boot from a GPT disk in 'legacy' mode. 
Make sure ubuntu boots in legacy mode with the purplish screen rather than the black bg grub menu.
The Boot-repair will identify the system as 'legacy' and re-install grub to the MBR.

---

### Post by Kris_Nakamura on 2014-09-02
after running boot repair, it told me to paste this as one of the commands "sudo chroot "/mnt/boot-sav/sda3" apt-get install -y -force-yes grub-pc linux"  and when I ran the commands, I got a message saying E: Unable to locate package linux.  If I just try to press forward on the menu it gives me an error saying GRUB is still absent. Please try again.  Since I cant move forward from there, it wont even give me a report.

-Kris

---

### Post by fantab on 2014-09-02
Re-run Boot-repair, and if it doesn't work again then Re-install Ubuntu. Only this time you have to choose /dev/sda as the boot-loader location.
Format the '/' ext4 partition.

---

### Post by Kris_Nakamura on 2014-09-03
I
GOT
IT
RUNNING
But I'm not sure behind the logic of what I did.  So I ran boot-repair again, this time it asked me where I'd like to install Grub, I selected /sda, let boot-repair do its job and then restarted.  Didn't work
I ran boot-repair again, I selected /sda AND /sda2 (I think it was sda2), let boot-repair do its job and then restarted. STILL didn't work.
I ran boot-repair again, I went to advanced options and chose the option for "Separate /boot/efi partition" and chose the only available option which was sda2.  Restarted, finally worked.

I'm not sure if what I did was "proper" but it seems to be up and running now.

Thanks so much for your help over the days Fantab I really really appreciate it!
-Kris

---

### Post by Kris_Nakamura on 2014-09-03
Wellll I seem to get "sorry, Ubuntu 14.04 has experienced an internal error" pretty frequently.  I can run everything I need to without much problem though.  Must have installed something wrong somewhere heh..
-Kris

---

### Post by fantab on 2014-09-04
Glad you got it working again.
Keep your Ubuntu up-to-date and those 'internal errors' should go away.
You can also report the errors at [launchpad]("https://launchpad.net/").

---

### Post by christopher9 on 2014-09-04
Good job on sticking with and seeing through what must have been a terribly fustrating experience! 

As mentioned, run Software Updater periodically to keep current.  DO NOT install the upgrades if Software Updater returns a "Install Partial Upgrades" message.  Just exit out and run Software Updater in 24 hours or so. 

I hope you enjoy your new OS!

---

