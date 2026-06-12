---
title: "Installation of Ubuntu on a Windows desktop"
date: 2024-09-15
forum: New to Ubuntu
---

### Post by alan44zz on 2024-09-15
Hello,
Sorry to post such probably stupid questions but...

I have a desktop running under Win10 and want to install Ubuntu24 on it, on a dedicated HD.
In the computer U have 6 hard disks, all used by the Windows system, MBR partition style and NTFS formatted.

I made a bootable USB disk with Ubuntu, and have 3 questions:

1- About dual boot. As I understood, GRUB will manage the boot. Will it work correctly with the MBR partition style for all disks ?

2- Will the other disks be concerned by the Ubuntu installation ? I remember that, maybe 15 years ago, I tried to install a Linux OS in a Windows desktop and it "initialized" ALL disks inside. Data was lost... I can of course physically unplug the disks, but... :)

3- Will I be able to use the other disks in the computer, currently used by Windows, with Ubuntu ? Data only, not software of course.
I read online that is it possible but the exact question is to know if, after using them with Ubuntu (for example writing some data), can I use them again with windows, with all "new" data written by Ubuntu, usable ?

Thank you!

---

### Post by ajgreeny on 2024-09-15
As your Windows 10 is unusually installed in MBR/UEFI  mode you will have to ensure that you boot the USB install drive in the same MBR mode which will then install Ubuntu in that mode.

Both OSs must be the same mode for grub to work and offer both at boot.

---

### Post by grahammechanical on 2024-09-15
I suggest that for safety's sake. Disconnect those hard drives that you use for Windows. Have just the har drive that you want to put Ubuntu on. After installation of Ubuntu replace those Windows drives. Then load into Ubuntu and open a terminal and run this command:

```
sudo update-grub
```

Watch the printout. Grub should identify the Windows operating system and when to bot you should get a Grub menu with options to load either Ubuntu or Windows. 

This forum thread provides useful information

[https://ubuntuforums.org/showthread.php?t=2491292](https://ubuntuforums.org/showthread.php?t=2491292)

You may also need to install a special driver to read/write to NTFS drives.

This might be too much information. At least it shows the package you need is ntfs-3g

[https://manpages.ubuntu.com/manpages/noble/man8/ntfs-3g.8.html](https://manpages.ubuntu.com/manpages/noble/man8/ntfs-3g.8.html)

```
sudo apt install ntfs-3g
```

Regards

---

### Post by yancek on 2024-09-16
>   About dual boot. As I understood, GRUB will manage the boot. Will it  work correctly with the MBR partition style for all disks ?

It can if you boot and install correctly.  If you are very inexperienced it would probably be best to disconnect your windows drives.  If you boot the Ubuntu install USB and from a terminal run the command below, it will tell you if you have a gpt Partition table or  dos.  I expect it will be a dos drive if windows is an MBR install which as pointed out above, is pretty unusual for the windows you are using.  Must have pretty old hardware.    If it is dos, then boot and install with your BIOS set to Legacy/CSM for the sake of simplicity.  If you do an EFI install of Ubuntu on one physical drive and have a Legacy install of windows on a separate physical drive, the Ubuntu Grub should still boot windows.  This works for me but for the sake of simplicity, I would install/boot all in the same mode.   You need to know which drive you are installing to and know Linux drive/partition naming conventions. 

```
sudo parted -l
```

As far as accessing and overwriting other disks, if you know the drive on which you wish to install Ubuntu and are familiar with Linux drive/partition naming conventions it should not be a problem.  Installing Ubuntu properly to a specifically selected drive will not affect other drives.  Maybe you did an LVM install without knowing what it did in your previous attempt.  

You should be able to write data to windows partitions with a windows filesystems but you are not going to get a guarantee from anyone.

---

### Post by alan44zz on 2024-09-19
Hello!

Well, I installed Ubuntu, ont its dedicated HD, no problem. Just the dual boot doesn't work.

In the (legacy) BIOS I put first ubuntu disk, it boots directyly into Ubuntu. No Grub menu.

In the (legacy) BIOS I put first windows disk, it boots directyly into Win 10.
I then here tried to add a boot entry with EasyBCD : Grub2, it detected the Ubuntu path (attached picture)
When I reboot, I get the "windows choice" between Win10 and Ubuntu.
If I choose Ubuntu, it stops at the screen shown in the second attached file.
What must I do if I want this first option ?


In fact as my goal is to get rid of Windows, I think I should put the Ubuntu disk at first in the BIOS boot section, and try to get Grub offer the option to boot in Windows too. So later if I remove the WIndows disk, all will work smoothly.
In this option as told above, the box boots directly into Ubuntu, no Grub menu.
What must I do if I want this second option ?

Thank you :)[IMG]https://ibb.co/zJKyb6D[/IMG]

---

### Post by alan44zz on 2024-09-19
According to the current situation, seems there's something wrong :)

---

### Post by ajgreeny on 2024-09-19
See Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.

**Do not run the default repair just yet** but simply copy back here the **pastebin** link you get which will show us a lot more about your system.

---

### Post by yancek on 2024-09-19
So you have verified that windows is installed in Legacy mode and Ubuntu is also installed in Legacy mode on a different physical drive, correct?  What you describe is expected behavior as Grub in Ubuntu no longer probes for other operating systems by default.  Boot into Ubuntu and using a text editor and sudo, edit the file /etc/default/grub to add the line below:

> GRUB_DISABLE_OS_PROBER=false 

If that line exists in the file make sure you do not have # at the beginning of the line and if you do, delete the # character.  Save the change and run sudo update-grub and you should see output for other operating systems detected if any are found on the connected drives.  Watch for  a windows entry and if you see one, set the Ubuntu hard drive to first boot priority in the BIOS.

Verify that Ubuntu is not UEFI.  Is Ubuntu on a GPT disk?  You can get this information with the simple command below which will List the partition info:

```
 sudo parted -l
```

If both systems are Legacy, I would expect EasyBCD to work but it won't work if Ubuntu is UEFI and I don't know how or if it will work on a GPT disk so doing this check should help.  If you want to use windows software like EasyBCD, post your question on a windows forum.  I used it in the past and it seemed to work but it's been years.

---

### Post by alan44zz on 2024-09-19
[https://paste.ubuntu.com/p/K28XWgH7zj/](https://paste.ubuntu.com/p/K28XWgH7zj/)

---

### Post by oldfred on 2024-09-19
You show mostly BIOS/MBR, but do have sda as gpt partitioned.
Not sure how you have Windows in old BIOS/MBR mode.
Microsoft has required vendors to install Windows in UEFI boot mode from gpt partitioned drives since 2012.
The old BIOS/MBR mode only was kept so old hardware could get an install of Windows 8. 
New systems starting in aboutn 2020 are UEFI only.

Do not get rid of Windows until you have converted all NTFS partitions to a Linux format. Windows will need chkdsk or defrag and that can only be done from Windows.

Looks like you are tying to dual boot from Windows, you need to dual boot from grub.
But grub only boots working Windows. That means no chkdsk required and fast startup must be off. Windows updates may turn fast startup back on. Fast startup sets hibernation flag and prevents the Linux NTFS driver from fully accessing the NTFS partitions to prevent loss of data when hiberfile restored when booting Windows.

But long term you need to consider converting drives to gpt. Conversion from MBR to gpt will totally erase entire drive, so good backups required.
Ubuntu will boot in BIOS mode from gpt partitioned drives if you add a bios_grub partition. I booted Ubuntu from gpt with BIOS starting in 2010, so I know it works. With first UEFI system I used gpt with both bios_grub and ESP - efi system partition which is required for UEFI boot. But with bios_grub partition I could easily reinstall grub for BIOS boot.

---

### Post by alan44zz on 2024-09-20
Sorry, I don't understand anything :(

---

### Post by alan44zz on 2024-09-20
> GRUB_DISABLE_OS_PROBER=false                      

Ok

grub-update : OK, windows entry has been added.

Yes ubuntu is on gpt disk.

Then I put the Ubuntu disk to boot first.
     
 
Reboot = Neither Grub nor windows, but error message saying Windows is corrupted ?!

That means that now I cannot even boot to Ubuntu at all...

I put back the Windows disk first. Reboot.

When I try to enter Ubuntu (EasyBCD choice...) I got this as told yesterday:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294261&d=1726766034[/IMG]

So it seems there's something to fix in the grub ...

---

### Post by tea for one on 2024-09-20
Your disk arrangement is complicated and still using old-fashioned Legacy installations and extended partitions.
I hope that you would consider oldfred's comments in post 10.
In essence, back up your data, start from scratch using modern UEFI and GPT.
One disk for Windows 10/11 and a separate disk for Ubuntu 24.04.
Grub would manage both very easily if you wish.
Even easier if you only want Ubuntu (as you mentioned in post 5)
More robust and future proof.

---

### Post by tea for one on 2024-09-20
> **alan44zz said:**
> Yes ubuntu is on gpt disk.
According to the boot-repair report, Ubuntu is located at:-
Line 142 -  OS#3:   Ubuntu 24.04.1 LTS on sdb6
Line 166 - sdb	: notGPT

---

### Post by yancek on 2024-09-20
The image you posted in post 12 clearly shows GRUB4DOS which is windows software and NOT Grub.  Since you booted that after running EasyBCD I guess that would be expected.

>  Reboot = Neither Grub nor windows, but error message saying Windows is corrupted ?!


When you set the Ubuntu drive (sdb) to first boot priority this is what you get?  Does that mean you do not see the Ubuntu Grub menu?  I would not expect you to see the windows is corrupted message until you have selected windows from the boot menu.  This drive is unusual as you have only one primary partition on it and that is used to hold logical partitions including a large windows partition before the Ubuntu partition.  Note the last line in boot repair.  I don't know if changing that would resolve the issue.  I would expect that since you have Ubuntu Grub code in the MBR of sdb where Ubuntu is installed that you would at least be able to see and boot Ubuntu.

---

### Post by alan44zz on 2024-09-21
Well! First, thank you everybody for your replies.

Yesterday I decided to go UEFI, converted all disks to GPT. And began problems with the OS disk... Converted through Partition Master, ok. But impossible to boot in UEFI with this GPT disk... Reverted to MBR, LEGACY boot, and also impossible to boot ! The windows repair disk couldnt repair anything :) Well, finally I could repair manually, ok now Win is working. But Ubuntu isn't booting anymore.

As I am for sure not able to repair myself I will wipe the Ubuntu disk and install it again, as before. If dual boot doesn't work at once, I will not use it, will just change the BIOS details to boot Ubuntu or Win.

[B][I]The question is: As I am stucked to LEGACY with my Windows (Win 10 LBTS), how must I prepare the disk for Ubuntu ? MBR ? GPT ? If GPT, will it boot with LEGACY BIOS ?

And in Rufus to create the install USB, must I select MBR or GPT ?
[/I][/B]
Thank you !

---

### Post by oldfred on 2024-09-21
Windows requires gpt partitioning for UEFI boot. 
Windows requires the very old MBR(msdos) partitioning for BIOS boot.
Ubuntu does not care either partitioning works with either boot mode, but it really should require gpt for UEFI.

With UEFI you must have an ESP - efi system partition, FAT32 with boot,esp flags. Only one per drive is allowed by most UEFI implementations. Windows & Ubuntu will share if dual booting on one drive. 
Often better with multiple drives to use ESP on same drive as install, but installer normally defaults to first drive's ESP and will give errors if no ESP on first drive.

With BIOS boot on gpt Linux requires a tiny 1 or 2MB unformatted partition with bios_grub flag.

I used Ubuntu in BIOS mode on gpt starting in 2010. When first converting to UEFI, I put both an ESP & bios_grub on new drives. Only difference with UEFI & BIOS boot for Ubuntu is ESP & bios_grub partitions and version of grub. Or just reinstalling grub in other boot mode can convert an install.

Grub2 only boots working Windows. That means Windows cannot be hibernated nor need chkdsk. And Windows fast startup sets hibernation flag for a quicker boot. It also may turn fast startup back on with updates.

Normally you cannot dual boot with one system UEFI and other BIOS on same drive. But with multiple drives, it is possible to boot in different mode. Grub can only boot other installs in same boot mode, but you can always boot from UEFI/BIOS one time boot key, if boot loaders are on different drives.

Do not use grub4dos. Not sure how much it has been updated, but it is based on grub (legacy grub), not grub2. And grub2 became standard in 2010. We often call grub2 as grub as it is standard grub now.

---

### Post by alan44zz on 2024-09-21
Well, all is good now, installed Ubuntu as a "full wipe disk" install on its dedicated disk, then added the grub menu, it found windows, and all is working fine booting from the Ubuntu disk. Thank you everybody for helping, will probably have other questions later.

---

