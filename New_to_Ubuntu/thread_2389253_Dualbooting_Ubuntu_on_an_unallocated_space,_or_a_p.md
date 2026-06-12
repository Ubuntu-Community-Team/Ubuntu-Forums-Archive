---
title: "Dualbooting Ubuntu on an unallocated space, or a premade space?"
date: 2018-04-13
forum: New to Ubuntu
---

### Post by bsodx on 2018-04-13
Hello there:

After a lot of thoughts and VM'ing Ubuntu, I made my mind for making Ubuntu and Windows dualboot. I currently have Windows 7 installed, have 4 GB of RAM, some integrated graphics card and a 450 GB HDD.

I found some guides around and the mainline is:

1.Take a backup of your Windows installation.

2.Partition the disk to make some space for Ubuntu.

3.Live-boot the Ubuntu from a thumbdrive and install alongside Windows.

I have done the backup and partition part -after having to deal with 2 3rd party partition softwares, and a failed attempt just because the disk wasn't defragged enough-so far, and I currently have a full backup of my Windows, a 300 GB Windows partition (C:) and 100 GB unallocated space(which I plan to install Ubuntu on) in the same disk.

I have two questions.

First one is whether is it worth to take the risk. I can repair the MBR or GRUB ,or simply restore the entire backup, but if I mess up with my HDD, it will be a painful time for me to buy and install a new one.

Second one is during the install, which option should I use? The "Install alongside Windows", or "Something Else",since I may need to shape that unallocated space (Do I?) Would it install in that unallocated space?

Thanks for the help.

(Note: I'll do a test flight with the Live USB after posting this. I'll edit with the results.)

(Edit: It showed some hardware errors and firmware bugs at the start, but everything's fine. I'll remake the Live USB with another flashdrive to be sure.)

---

### Post by oldfred on 2018-04-13
If Windows 7 it is probably BIOS with MBR partitioning and the 4 primary partition limit.
Post this:
sudo parted -l

If you have used all 4 primary partitions, you cannot use unallocated space. But need one primary partition to become an extended partition that then can old any number of logical partitions.
If UEFI and gpt partitioning, you in effect have all primary partition and the limit is 128 partitions, which an user can even change.

---

### Post by bsodx on 2018-04-14
It is an MBR, and I realized Windows uses all four.
One for System Reserved, one for Windows, one 2 GB, which Lenovo pre-made with the drivers, bloat ware, and stuff, and the recovery partition. Guess I'll delete that 2 GB one, since I have its backup, or convert one to extended (to be honest I have never done one and don't know how) 

Also, it looks like I have to trigger this command from live USB. Am I right?

Also thanks for the reply.

---

### Post by leunam12 on 2018-04-14
You have to shrink your Windows partition to create unallocated space for Ubuntu, this is best done in windows using the disk manager and then run chkdsk.
If you don't run chkdsk your Ubuntu installation may fail. But you mentioned that you are going to delete the recovery partition which may create unallocated
space that is not contiguous with the partition that you want to use for Ubuntu.

Moving partitions is possible, but sometimes risky. Your computer probably came with an utility that allows you to create recovery media on DVD or USB stick.
I would do that first if you have never done it. This is just an extra security measure in case everything fails.

---

### Post by oldfred on 2018-04-14
+1 on leaunam12's suggestions

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media) 
   Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
sudo Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by bsodx on 2018-04-14
I did the command in the live USB and the output is:

```
Model: ATA WDC WD5000LPCX-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  211MB  210MB   primary  ntfs         boot
 2      211MB   351GB  351GB   primary  ntfs
 3      460GB   487GB  26.8GB  primary  ntfs
 4      487GB   500GB  13.1GB  primary  ntfs         diag
(Strangely the unallocated space doesn't show up there, does this command only show formatted parts?)

Model: General USB Flash Disk (scsi)
Disk /dev/sdb: 8053MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8053MB  8052MB  primary  fat32        boot, lba
(This USB is the Live one)
```

I checked out some more things: The disk is an MBR, but apparently I suspect there's an UEFI loaded in this computer.(Saw EFI boot option for the Live USB while starting Ubuntu, and there was a Win8 sticker at the bottom of the computer) I won't mess with the disk to make it GPT though.

To everyone, I have a Macrium Reflect backup and a Macrium PE ready. I also put a WinPE somewhere to make sure.
I shrunk the disk (Without knowing it may mess with preinstalled OneKey Recovery, not sure if it works anymore but not much of a matter anymore), I have 100 GB of unallocated space and four partitions. The partition I mentioned has Lenovo drivers and all the bloatware and it seems like it can be safely deleted.

So, what should I move on with? I'll delete that part, and install Ubuntu in the legacy BIOS way.(If not I'll open the Legacy mode for now, after seeing these errors with UEFI it looks like for a total novice like me to move with the legacy)

I'll keep you updated about what I do.

Edit: It has UEFI, but Windows 7 x64 is loaded in Legacy mode and UEFI switched to legacy too. Probably from the hands of a unofficial computer service.

---

### Post by oldfred on 2018-04-14
If system was Windows 8, then it was UEFI with gpt partitioning.
And the Windows 7 DVD only installs in BIOS boot mode with MBR partitioning. The installer can be converted to UEFI install by copying to a flash drive and moving/renaming some files, but just about impossible to convert a BIOS install to UEFI without reinstalling.

But if drive was gpt and you install Windows 7, it incorrectly converts drive from gpt to MBR. One advantage of the newer gpt is that it has a backup partition table at end of drive. Windows leaves that backup gpt and converts to MBR. But then Linux tools see both MBR & gpt and normally fail or just stop working. You then have to remove the backup gpt table. We can post instructions for fixparts tool, if that is the case.

The parted command only shows existing partitions.

Since hardware is UEFI, and Ubuntu installer can be booted in either UEFI or BIOS mode be sure to boot installer in BIOS mode as how you boot install media is then how it installs. And if you attempt to force the Ubuntu install in UEFI mode, you may corrupt BIOS boot of Windows.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by bsodx on 2018-04-14
So that I'm not choosing EFI boot, make sure it boots up with a purple accesibility screen. 

The installation is a legacy one, and I'm not meddling to change it to a UEFI until I make my mind and money to buy a Win10(very low chance though). I got this computer from a relative who doesn't know that much about computers, such as he can't tell whether it's a mac or Linux, or if it's a Win10 or Win7 etc. Only thing I know about is it was preinstalled with a Win8, and a Win7 was set up instead. So the recovery partition contains a 8 or 8.1 image. I don't mind if the factory recover refuses to work; as long as Macrium is up I'm okay. 

My designated way is now:

-Delete that part, and make an extended volume(Should I use parted/gparted or windows disk manager here?)
-Make my way through the install(Install alongiside or something else here?)
-If needed, fix the grub
-Optionally, customize the grub(No, can't settle with current grub because there's people who doesn't know english and will probably fire up memtest or recovery trying to start Windows even if it is default, I want to make it two or three simple icons)

The 2 GB partition is a safe to delete one. 

Now, is there anything I should also pay attention to? Or am I good to go?

---

### Post by leunam12 on 2018-04-14
I don't see the 2GB partition in your previous post, I see 210MB, 351GB, 26.8GB and 13.1GB

To install you have to pick "something else" and install on the partition(s) that you have made and reserved for Ubuntu.

---

### Post by bsodx on 2018-04-14
My bad. It's the 26,8 GB one. I mistook it with the used size.

What are your recommendations for the home, root and swap sizes (4GB RAM)? And can you shortly explain how? Can't seem to understand the internet guides to be honest.

---

### Post by yancek on 2018-04-14
If you have 100GB of unallocated space, use about 20GB for the system files, 4GB for swap and the rest for /home or a /data partition.
Since you need to delete one of the partitions in order to do the install, I would do that from windows and also run disk defragmenter after and reboot and maybe run chkdsk also.
The Install Alongside option usually works but it is basically an auto-install which means if something goes wrong, you won't have any idea what it was.
Lots of tutorials on this method if you select it.  The manual (Something Else) option is a little more detailed but you will know what is happening and need to make some choices.
You might do an online search for tutorials on each method before deciding and make certain you boot Ubuntu Legacy when you install.

---

### Post by bsodx on 2018-04-14
I'll try these up in a day or two.

So the drill is:

Make extended partition from Windows->Reboot and run defrag-chkdsk->Boot into Live CD->Something Else->20-25 GB partition(ext3 or ext4?) for system, 4 GB for swap and what's left for Home->Install->Have a coffee->Bask in glory about something I managed to do right.

Seems simple in my opinion.

Last questions: 
*Which filesystem would be better, ext3 or 4? And also should I use the encrypt option and LVM?
*Is it normal that my Windows clock resets after I boot from livecd and restart?
*Is an LTS better than the latest release?
Sorry for bothering that long, and thanks for all the info I didn't manage to find around.

---

### Post by oldfred on 2018-04-14
Do not use Windows to create partitions. It often converts to dynamic from basic which is a proprietary Microsoft partitioning system. But do use it to shrink NTFS partitions.
Use gparted to partition in advance or partition during install.
I generally like to use gparted as it seems slightly easier, but you still have to use Something Else install option and change button on existing partition or make new partitions.

If you use the default LVM with encryption install, you erase the entire hard drive and convert to LVM partitioning which is somewhat like the Windows dynamic and will not let you install/reinstall Windows into it. There are advanced ways to make LVM part of a drive, but the advantage of LVM is when it controls entire drive. Usually used with server installs, but also required with full drive (entire physical drive) encryption.

Use ext4, that has been the standard for years. Where are you getting any suggestions to use ext3? I have not seen anything about ext3 for years.

Partitioning is very personal and depends on your use. So as a new user just about any options will work.

---

### Post by bsodx on 2018-04-14
Ext3 was featured on some guides I've read, with the reason of "compatibility with other Linux distros when multiple on same PC".

Guess I'll look more around the partitioning to make sure. 

LVM and encryption is hard to apply to a part of drive you say, guess I have to forfeit some security.
Okay, it looks like that's all for the install. I'm going to make the install soon, I'll inform you once I'm done.

---

### Post by oldos2er on 2018-04-14
Be sure to check the date of information online, as oldfred suggested. Ubuntu's gone through some major changes in the past several years, and info regarding older versions won't always apply to newer versions.

+1 to ext4. It's been the standard file system on most desktop distros for years.

---

### Post by bsodx on 2018-04-17
Everything went well, made an extended partition in gparted, did the disks on install. Grub installed finely. I have a little lag on boot in Windows and the time gets reset everytime I switch back to Windows from Ubuntu, but seems fine around. Ubuntu looks slick and swift on this PC, boot takes 20 seconds including grub. I replaced grub with burg (after failing to install and purging everytihng back and installing once more) and we're now complete.

Oh snap I screwed up the coffee part-

Thanks for all the help.

---

