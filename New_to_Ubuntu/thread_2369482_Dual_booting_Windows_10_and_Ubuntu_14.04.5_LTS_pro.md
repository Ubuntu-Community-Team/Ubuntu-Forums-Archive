---
title: "Dual booting Windows 10 and Ubuntu 14.04.5 LTS problem"
date: 2017-08-23
forum: New to Ubuntu
---

### Post by quce on 2017-08-23
Hello, i am new to Linux. Today i wanted to dual boot Windows 10 and Ubuntu 14.04.5 LTS (i can't use 16.04 LTS because of amd drivers).I booted up my usb flash drive with Ubuntu 14.04.5 LTS and i clicked to install it.The part where i can't continue is on the Installation type.I was expecting to have the option Install Ubuntu alongside Windows 10 but i don't have it.

I watched tutorials on Youtube about dual boooting so i knew what to do.I needed to shrink the volume out of my Partition ( I have 1 TB hdd and only one partition which is C).I did this part and when i was back in Ubuntu installer i clicked Something else.

There was only one thing there, and it was 1TB HDD and it was free space.No Windows Boot manager,nothing.Only my hdd and it saying that its free space.I tried with another installation of Ubuntu but same thing.I don't know what to do.

Forgot to mention that my bios mode is legacy if that will help.

---

### Post by Autodave on 2017-08-23
Did you disable *fast boot *in the BIOS?

---

### Post by quce on 2017-08-23
Hello there,i dont have fast boot in the bios because i set it on legacy support. I have fast boot option on UEFI support but not in legacy.And i can't set it to UEFI because my HDD is not showing on UEFI support.

---

### Post by oldfred on 2017-08-23
What brand/model system? What video card/chip?

If Windows is UEFI, you need to boot installer in UEFI mode, so Ubuntu install is UEFI.
Legacy may work but then you can only dual boot from UEFI boot menu & may have to go into UEFI and turn on/off UEFI/Legacy depending on which system you are booting.

See link below in my signature.

Make sure Windows fast start up is off. Otherwise Linux NTFS driver cannot see NTFS system partition to know you have Windows.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by quce on 2017-08-23
I have Lenovo G50-70 with AMD Radeon HD 8500M. Windows is Legacy and im booting Ubuntu from legacy. Also i tried to boot from UEFI but same thing.Windows fast start up was off.

---

### Post by oldfred on 2017-08-23
I am surprised that system is legacy. Hardware is UEFI and if originally from vendor Windows 10 must be installed in UEFI mode. Only if upgrade from Windows 7 may it be BIOS/MBR.

If BIOS/MBR then you may have used all 4 primary partitions allowed with MBR partitioning.
Post this:
sudo parted -l

We can convert one primary partition  to an extended partition, so you can have an unlimited number of logical partitions. Windows has to boot from a primary partition with BIOS/MBR, but Linux will boot from a logical partition.

---

### Post by quce on 2017-08-23
I bought SSD which is UEFI but now my ssd is on service right now.And also my hdd was replaced because of failure.And with sudo parted -l is asking me if it contains GPT signatures, and is it a GPT partition table.I writed "y" and it saying that the backup GPT table is corrupt, but the primary apprears OK.After that its my HDD model and its that.Nothing changes.

If its necessary i can copy all the text from the terminal and i can paste it.

---

### Post by anidxi on 2017-08-23
Hey! 

Go on to windows, and type msinfo32 into Run/Cortana to see what mode your laptop booted in - you will either see UEFI or Legecy under BIOS mode. UEFI would imply it's GPT.

Also go onto Comand prompt as admin and type in diskpart, wait for the command line to change to  DISKPART> and type **list disk**. on Disk 0, your internal drive, you should see a '*' under the gpt column, as in the code below. That means that your disk has a  GUID partition table.
```

C:\Windows\system32>diskpart

Microsoft DiskPart version 10.0.15063.0

Copyright (C) Microsoft Corporation.
On computer: ANIRUDH

DISKPART> list disk

  Disk ###  Status         Size       Free     Dyn  Gpt
  --------   -------------    -------     -------   ---   ---
  Disk 0     Online          931 GB  2048 KB           *
  Disk 1     Online          931 GB  1024 KB


```

---

### Post by quce on 2017-08-23
Hello, in msinfo32 its saying that BIOS Mode is Legacy and in diskpart i dont have this "*".Maybe i need to wait for my ssd to arrive and then to try?

---

### Post by oldfred on 2017-08-23
How soon will you have SSD?

Who installed Windows on HDD? It really should be UEFI with UEFI hardware.

Drives are not UEFI or Legacy. 
But partitioning is normally gpt with UEFI and MBR(msdos) with BIOS boot installs.

UEFI hardware can have the now 35 year old BIOS/MBR configuration, just for legacy purposes.

---

### Post by quce on 2017-08-23
I don't know i guess after 2,3 weeks

I installed the windows but when i picked up my new HDD it was only visible in legacy mode (its not showing on UEFI mode).What can i do to make it visible on UEFI or something like this?I know how to convert it to gpt but i will lose everything.

---

### Post by oldfred on 2017-08-23
Once installed in BIOS/MBR boot mode that is the way you have to boot.
Windows only boots in BIOS mode from MBR and UEFI mode from gpt.
But with UEFI boot you have to add several partitions, so not exactly easy to reconfigure.

You may need your Windows repair flash drive or see if f8 works to get into Windows internal repair console.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options

[/URL]
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 

[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---

### Post by quce on 2017-08-24
Sorry for that late reply, I didn't understand what to do from your post.Should I convert it to gpt or just to wait for my ssd?

Or i can do something?

---

### Post by anidxi on 2017-08-24
Hey!

I had the same issue - I got a laptop that came preinstalled with only freeDOS, and had to install my copy of Windows on an MBR table since the installer did not accept a GPT disk. I had to then convert the disk my Windows installation was on to a GUID partition table. I've done it thrice, and I'm not going to say that it is easy, or not fraught with risk (you might end up with a unbootable system that would take some effort to fix). However, if you follow the instructions carefully, you should be fine.

I can't find the source of the tutorial I used, but I'll post it here. It is not somethong I devised myself, but it is logical.
```

1. Download gpt-fdisk (gdisk) for Windows.
2. Copy the binary to a known location.
3. Boot into Windows Recovery Environment.
- If you don't have one, download Windows10ISO from: [https://www.microsoft.com/en-in/softw...]("https://www.microsoft.com/en-in/software-download/windows10ISO")
- Create a bootable USB by following [https://www.youtube.com/watch?v=Q8gQu...]("https://www.youtube.com/watch?v=Q8gQuYekACU") or by burning the ISO to a DVD.
4. Shutdown Windows and boot using this media (Legacy or UEFI Mode).
5. Get to the command prompt. Either by pressing Shift+F10 or by navigating to it.
6. Go to diskpart and find out the disk identifier for your Windows installation.
diskpart
list disk
sel disk X
list par
7. Navigate to the location where gdisk binary is kept and type:
gdisk -l X: (Replace X with the disk number)
This will list out the partitions available in the disk. Make sure this is the one your want to convert.
8. Now, convert the partition table from MBR to GPT.
gdisk X:
Type w to write changes. Press Y whenever prompted.
9. Type the following commands:
diskpart
sel disk X (Replace X with the disk number)
list par
# Now we make some space for our EFI partition
# Note the partition number of the partition which you want to shrink
sel par X (Replace X with the partition number)
# You may delete the System Reserved partition and replace it with the EFI partition. To do that, type:
# sel par X (Replace X with the System Reserved Partition)
# del par override
# The shrink command is not required if you do the above two commands.
# I'll just go ahead and shrink. 500MB extra doesn't matter to me :D
shrink desired = 200 minimum = 200
# The following commands are common:
create par efi
format fs = fat32 quick # Format this with fat32 file system
assign letter = Z:
exit
9. Copying boot files.
Find out the partition in which Windows is installed. Note, the partition letter here might be different than the partition letter you see in Windows. Perform dir X: on each partition letter you think can have the Windows installation and confirm X. Then type:
bcdboot X:\Windows /l en-us /s Z: /f ALL
10. Done. Now reboot in UEFI mode.


```

Try it out, and post when you're done.

---

### Post by quce on 2017-08-24
Hey i just downloaded linux mint 18.2 on new usb drive and its working!I can install mint alongside windows, everything is working like it should be.

I will try to burn the ubuntu 14.04.5 LTS iso onto my new usb drive and i will write again.Oh and can this be the problem, just one usb drive?

EDIT:Nah, not working again :( I will try Linux Mint 17.3 because if im not mistaken its based of ubuntu 14.04 and my gpu have drivers for this version!I will write again if its working

---

### Post by oldfred on 2017-08-24
How you boot install media, UEFI or BIOS is then how it installs.
If UEFI system, you would want to boot installers in UEFI boot mode to install in UEFI mode.

Flash drive should have two boot options for booting USB flash drive one UEFI:flash and the other flash which then is the BIOS boot & where flash is name or label of flash drive.

But to get boot settings you often have to change settings in UEFI. If UEFI Secure Boot is on, you almost always have to turn on allow UEFI boot of flash drive. And many require that even with Secure boot off. In BIOS mode it may allow USB boot by default.

---

### Post by quce on 2017-08-24
Mint 18.2 and Ubuntu 16.04 LTS is working perfectly.Today i will dualboot Windows 10 and Ubuntu 16.06.4 LTS.Thank you for all the advices you gave me ! :)

---

### Post by quce on 2017-08-25
Hey i just want to say that everything is working with 16.04 and windows 10 ! :)

---

### Post by oldfred on 2017-08-25
Glad you got it working.

If you want to post what details made it work that would be great.
And change to Solved.

---

