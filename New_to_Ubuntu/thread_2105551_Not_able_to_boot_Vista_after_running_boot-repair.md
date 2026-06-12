---
title: "Not able to boot Vista after running boot-repair"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by nkl on 2013-01-16
Hi all,
          I have Ubuntu 10.04, Ubuntu 12.10 and windows Vista installed on my laptop. Recently I installed Windows 8 on another partition. But after installing windows 8, there was no option to choose Ubuntu in the boot. Using boot-repair, I got grub menu back with both ubuntu and vista entries (not windows 8 entry). But the names of Vista and recovery were swapped (Windows Vista loader is on /dev/sda1 and recovery is on /dev/sda3). Here is the pastebin link:

[http://paste.ubuntu.com/1534373/](http://paste.ubuntu.com/1534373/)

I tried fixing this using grub-customizer and burg, but in this process, I mistakenly wrote grub2 on all partitions. Now I am not able to boot Vista or recovery. Pastebin link of current state:

[http://paste.ubuntu.com/1537614/](http://paste.ubuntu.com/1537614/)

How can I get back my Vista running?

---

### Post by nkl on 2013-01-16
So, basically my problem is that I have install grub 2 on windows partitions also and I want to install default windows boot manager (bootmgr or MBR ? , I don't know much).
And starting vista is necessary as it has many important softwares installed in it which are necessary for my project work.

---

### Post by mad2-814 on 2013-01-16
Boot into recovery with either the recovery partition or a recovery disk.  Then open a command prompt and run the following commands

```
bootrec.exe /fixboot
```

```
bootrec.exe /fixmbr
```

You then may need to boot into an Ubuntu live cd to reinstall grub as I believe the mbr will be rewritten, but this will allow you to get back into your vista install then recovering grub should be fairly easy.

---

### Post by oldfred on 2013-01-16
mad2-814's suggestion is the Windows way to fix the issue, but sometimes Windows will not even recognize a NTFS partition with a totally corrupted NTFS PBR - partition boot sector. And grub makes it totally corrupted to Windows.

Testdisk which you can install from the Ubuntu repository to Ubuntu or Ubuntu liveCD/DVD/Flash or is part of most Linux repairCDs. You need to run this on all the NTFS partitions with grub installed. Grub in the Linux partitions will not matter as it is not used and will be ignored, otherwise.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by centaurusa on 2013-01-16
> **nkl said:**
> But the names of Vista and recovery were swapped (Windows Vista loader is on /dev/sda1 and recovery is on /dev/sda3)... How can I get back my Vista running?

You can check (and customize) the entries in the grub boot menu by following the instructions given at:

[http://linuxnorth.wordpress.com/2011/03/09/grub2-revisited/](http://linuxnorth.wordpress.com/2011/03/09/grub2-revisited/)

Repairing the MBR for Windows can be achieved using the System Recovery Disk; however, this will load a Windows-only MBR and so you will then need to recover grub, perhaps using Rescatux - formerly Super Grub Disk ([http://linuxnorth.wordpress.com/2012/12/31/cloning-a-hard-drive-to-a-smaller-ssd/](http://linuxnorth.wordpress.com/2012/12/31/cloning-a-hard-drive-to-a-smaller-ssd/)).

There are other ways to do the latter, such as:

Boot-Repair ([http://linuxnorth.wordpress.com/2012/02/07/repairing-grub/](http://linuxnorth.wordpress.com/2012/02/07/repairing-grub/))

Command line ([http://linuxnorth.wordpress.com/2013/01/09/re-installing-grub2/](http://linuxnorth.wordpress.com/2013/01/09/re-installing-grub2/))

---

### Post by mad2-814 on 2013-01-16
> **oldfred said:**
> mad2-814's suggestion is the Windows way to fix the issue, but sometimes Windows will not even recognize a NTFS partition with a totally corrupted NTFS PBR - partition boot sector. And grub makes it totally corrupted to Windows.

Testdisk which you can install from the Ubuntu repository to Ubuntu or Ubuntu liveCD/DVD/Flash or is part of most Linux repairCDs. You need to run this on all the NTFS partitions with grub installed. Grub in the Linux partitions will not matter as it is not used and will be ignored, otherwise.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Totally forgot about testdisk,  it's a great tool as well

---

### Post by nkl on 2013-01-17
I tried repair using Testdisk, but it is not giving me backup BS option, that means my backup boot sector is also corrupted. I have an HP laptop, I created recovery disks 3 years back and never checked it (needed 3 disks for this). But now when I checked them, one of them (first one) is completely empty, don't know why, and other two have 2nd and 3rd part in them. That means I can't use my recovery disks. Can I do this using bootable pendrive of windows vista?

---

### Post by nkl on 2013-01-17
I created a bootable Vista USB stick and then ran the command in cmd:

bootrec.exe /fixboot

Now grub 2 is removed from windows mbr. Now when I select windows entry in boot menu, a blank (black) screen appears with a cursor blinking on the top left. After few keystrokes press, it starts making beep sound  when any key is pressed (except for shift, ctrl, alt and caps,num lock). And restarts when I press ctrl+alt+del.

I am attaching the new file generated by boot-repair with this post.

What should I do now?

---

### Post by oldfred on 2013-01-17
It looks like you have boot flag on sda3 which only has two boot files, that often is just a vendor recovery. 
Boot flag should be on sda1 as that looks like your full install. But grub does not use boot flag and will boot a working Windows without it. But to boot Windows directly boot flag must be on sda1.

I do not know about burg. I understand it is not maintained any more and may not work with the newest grub.

Do both versions of Ubuntu boot ok? You have the grub of your 10.04 in the MBR.

You may also need to run chkdsk on your Vista partition. Move boot flag first with gparted, Disk Utility or command line. Only have one boot flag per drive on the Window primary partition used to boot.

Better to post link to BootInfo report as it is easier to open. :)

---

### Post by nkl on 2013-01-17
Hi Oldfred,
Yes, sda3 is a recovery partition. And I had removed the burg, but still its themes and other entries are in the report.
Yes, both versions of Ubuntu boot ok, though there is a problem with the plymouth theme of 10.04, colours are not coming properly (I am using Ubuntu-sunrise theme).
I have moved the boot flag to sda1 (Vista partition) using gparted. I wil now try rebooting the system.
I have not used the second command given by mad2-814:
bootrec.exe /fixmbr
Do I need to run this as well? (I read in some post that we only need to run the first one, not the second.)

---

### Post by nkl on 2013-01-17
Problem still persists, even after moving the flag.

---

### Post by oldfred on 2013-01-17
The fixMBR command puts the Windows boot loader into the MBR so you then boot to the partition with the boot flag. That is all the Windows MBR code does, is look for a partition with a boot flag and jump to that PBR to find more boot code. 

You can do that to see if Windows works on its own or until you fix Windows as grub only boots a working Windows. From grub menu some have said they can get to the Windows repair console with f8 but have to be really quick as the timing is quick. Where from MBR boot you do not have to be as quick.

But you will have to reinstall grub to MBR, if you have installed the Windows boot loader to the MBR. You can use Boot-Repair or just use commands. If familar with Boot-Repair that may be easiest, but you will have to download into the Ubuntu install liveCD/DVD/Flash.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by oldfred on 2013-01-17
Often Windows also needs chkdsk to finalize all the fixes, have you run that?

---

### Post by nkl on 2013-01-17
I ran both commands fixboot and fixmbr, and also chkdsk C: /F. But still not able to boot. Only difference is, now there is no beep sound when pressing any key, and no restart when pressing ctrl+alt+del. And when I go in the repair mode of bootable vista pendrive, earlier it was recognizing recovery and vista as partitions, but now it is giving windows 8 and vista as paritions (though I don't have windows 8 now, I formatted it after the problem started). And in startup repair option, It is giving message that OS booted successfully, with all tests passing successfully and error code 0x0. Is it that the earlier entries in boot options of windows 8 causing problem now?

---

### Post by oldfred on 2013-01-18
Windows only boots from the active partition or what we see as boot flag. Second installs of Windows will install its boot files to that same active partition overwriting the older installs boot files. It will update BCD to let you boot either install.
So if you install Windows 8 after Vista, Windows 8 will rewrite the Vista boot files with Windows 8 boot files and the Windows 8 partition will not have any boot files.
So what Windows tool are you using to repair? If you have Windows 8 boot files you should repair with Windows 8 repairCD. If you have deleted Windows 8, you may need the Vista boot files back but not sure if that then may be part of the issue.

---

### Post by nkl on 2013-01-18
I have created bootable vista pen drive and I'm using this to repair the system. Initially, when I had both vista and windows 8, and vista was not booting (only vista entry was there in boot menu), I thought there might be some problem in vista boot file. So I tried reinstalling windows 8, as it was anyways newly installed. So I formatted the older one, and tried installing again, but the installation stopped at 31%, giving some 0x80070570 error (*Windows cannot install required files. The files may be corrupt or  missing. Make sure all files required for installation are available,  and restart the installation. Error code: 0x80070570") *though I used the same setup earlier to install windows 8.
What will I need to do to get vista boot files back?

---

### Post by oldfred on 2013-01-18
They are in your Vista repairCd. And running the full set of repairs should work.

---

### Post by nkl on 2013-01-18
Can you explain it in details? I don't have Vista repairCD (I only have bootable vista). And how to run full set of repairs? I have recovery disks, but don't know why, the first part (1st of 3 DVDs) is empty, though I created them myself, and without making first one, there wouldn't be option to create second part, and I have the second and third part.

---

### Post by oldfred on 2013-01-18
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

My info is just a summary from several of the Windows links.

---

### Post by nkl on 2013-01-21
Hi oldfred, thanks for you help.
When I run the ScanOs command and RebuildBcd command, it gives me this message: 

Total identified windows installations: 0
The operation completed successfully

But it is showing vista (and window 8, which I don't have now) when I select the repair pc option in recovery pen drive.

---

### Post by oldfred on 2013-01-21
Post a link to a new BootInfo report, just to see what has changed.

You may do better in a Windows forum as we are not experts on all the Windows repair details, just basics. :)

---

### Post by nkl on 2013-01-21
[http://paste.ubuntu.com/1555934/](http://paste.ubuntu.com/1555934/)

in line number 970, why is it giving no-boot?

I have posted this problem on vista forum also. But they take too long to reply.

---

### Post by oldfred on 2013-01-21
I think that is just saying you do not have a separate /boot partition. 

If Vista did not work from when you had Windows 8 installed then it must have major internal issues. Boot repair only shows that the normal boot files and partition structure look ok.

---

### Post by Mark Phelps on 2013-01-21
As far as I know, while you CAN repair Vista boot using Win7 Repair CD (as folks reported being able to do that), you can NOT repair Vista using a Win8 Repair CD or USB.  

What most likely WILL work, if what you really want is to restore the ability to boot into Vista, is running Startup Repair from a Vista Repair CD.

Since you don't have one of those, if you're willing to spend $20, you can go to the site below, pay the money, download an ISO image -- and burn that to a CD.  You can then boot from that CD and run Startup Repair three times -- that's right, three times:

[http://systemdiscs.com/?utm_source=neosmart&utm_medium=article&utm_campaign=Vista_Recovery]("http://systemdiscs.com/?utm_source=neosmart&utm_medium=article&utm_campaign=Vista_Recovery")

---

