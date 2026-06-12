---
title: "Dual Booting (2 SSDs)"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by jferreir on 2014-01-20
I installed Ubuntu 12.04 on a 128GB SSD, and Windows 8.1 on a 256GB SSD. Both operating systems work if I select the correct drive via the BIOS, but the GRUB boot loader for Ubuntu (or whatever it's called) doesn't list Windows 8.1 as an option. I get a purple screen that allows me to select only Ubuntu. When I start from the Windows 8.1 SSD, it just loads Windows - I'm not given an option to select the OS. 

Ideally, I'd like to use the Ubuntu GRUB boot loader to select the OS on startup. How do I do this? Any help would be appreciated because I'm really stumped on this one. Thanks!

P.S. I already ran the recommended settings of Boot-Repair in Ubuntu, but that didn't seem to work.

---

### Post by esdoka on 2014-01-20
Hi,

Correct me if I'm wrong, but you have SSD1 with GRUB in MBR + Ubuntu behind it. SSD2 has only Win 8.1. I think you must manually edit bootloader files with proper entries saying that you have another disk with extra OS.

Then - IMHO - you will have this flow: power -> MBR -> bootloader -> question which OS to launch.

---

### Post by oldfred on 2014-01-20
Is this a new system with both UEFI & BIOS and then are both installed in the same boot mode.
Also is Windows 8 still have fast boot on or the always hibernated state?

May be best to see details.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by jferreir on 2014-01-20
> **esdoka said:**
> Hi,

Correct me if I'm wrong, but you have SSD1 with GRUB in MBR + Ubuntu behind it. SSD2 has only Win 8.1. I think you must manually edit bootloader files with proper entries saying that you have another disk with extra OS.

Then - IMHO - you will have this flow: power -> MBR -> bootloader -> question which OS to launch.

Yes, that's exactly right. 

Can you please explain, in idiot-proof terms, how I can manually edit the bootlader files so that it detects Windows 8.1 on SSD#2?

---

### Post by grahammechanical on 2014-01-20
Linux uses terms like sda for the first hard disk and sdb for the second hard disk. I do not think that a Windows boot loader will ever put Ubuntu into its boot menu but the Ubuntu Grub menu should list an entry for Windows 8 (loader). You can load Ubuntu and try this command

```
sudo update-grub
```

And watch to see if the Grub os-prober utility lists Windows 8 as being recognised. If it does then you may get an option to load Windows 8 (loader) in the Grub boot menu. If you do not then run this command

```
sudo grub-install /dev/sda
```

Assuming that Ubuntu is on the first drive (sda).

Regards.

---

### Post by jferreir on 2014-01-20
> **grahammechanical said:**
> Linux uses terms like sda for the first hard disk and sdb for the second hard disk. I do not think that a Windows boot loader will ever put Ubuntu into its boot menu but the Ubuntu Grub menu should list an entry for Windows 8 (loader). You can load Ubuntu and try this command

```
sudo update-grub
```

And watch to see if the Grub os-prober utility lists Windows 8 as being recognised. If it does then you may get an option to load Windows 8 (loader) in the Grub boot menu. If you do not then run this command

```
sudo grub-install /dev/sda
```

Assuming that Ubuntu is on the first drive (sda).

Regards.

Thanks, I'll give this a shot when I get home from work later tonight. 

Out of curiosity, do you know why Grub isn't recognizing the Win 8.1 drive? I believe I have Win 8.1 installed on sda, a mass storage drive installed on sdb, and ubuntu installed on sdc. I installed ubuntu first, and then Win 8.1. Does the order of installation make a difference when you're using two different drives? I wouldn't think so, but I didn't encounter this problem previously when I had Win 8.1 installed first.

---

### Post by oldfred on 2014-01-20
Order may not make a lot of difference, but where boot files get installed with multiple drives can be an issue.

Grub normally installs to sda. Windows normally  installs its boot partition into the drive that is set to boot from in BIOS or in the efi partition of the boot drive if UEFI. And those can conflict.  Again BootInfo report will show lots of details.

---

### Post by jferreir on 2014-01-20
So I tried the grub update, but the output in Terminal made no mention of Windows 8.1. I then used boot repair, selected the recommended settings, and followed the instructions. I still think something is massively off, though. Here is the current boot report: [http://paste.ubuntu.com/6788655/](http://paste.ubuntu.com/6788655/)

When I used the boot repair utility, I received messages about legacy grub, and windows efi something (I don't know what any of this means). Now when I get to the system BIOS, there's two additional boot options, one is a windows booter and the other a ubunutu booter, but they both appear distinct from the actual HDDs that the OSs are installed on. 

I have no idea why this is so damn complicated. I just want to see two options: Ubuntu SSD, and Windows SSD, with the option to select the OS from the Ubuntu boot menu. Help?

---

### Post by oldfred on 2014-01-20
You need to have systems installed in the same boot mode to have them dual boot easily.
But you have Windows in UEFI boot mode on sda and Ubuntu in BIOS boot mode in sdc.

You also installed grub2's boot loader to the partition. That almost never is required, but should not create any new issues as that space is not normally used.

But your efi partition sda2 is empty.

And it looks like Boot-Repair tried to convert Ubuntu to UEFI, but sdc is MBR partitioned. UEFI only works with gpt partitioned drives which both sda & sdb are. 

I would reformat sdc and include an efi partition. Even if the efi partition on the sda drive is used, it is good that each drive boot without the other. I believe even if Windows boot files are in efi  partition in sda & grub/Ubuntu's files are in sdc UEFI should work.

Boot-Repair cannot fix missing Windows boot files. You need a Windows repair flash drive.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Windows also has backups of some boot files:
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

But you cannot dual boot Windows from Ubuntu installed in BIOS mode. Once you start booting in one mode you cannot change, so grub menu will not work to boot UEFI system if booting stated with BIOS. 

Reinstall grub to sdc in UEFI mode. See these and other links in the link in my signature to install in UEFI mode.
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system

[/URL] For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system"]
[/URL]

---

### Post by jferreir on 2014-01-21
I'm sorry, but I can't understand any of that. It's way too technical and I don't have a background in comp sci. Hell, I don't even know what GRUB and EUFI stand for, or what the basic difference is between them. My computer skills are strictly limited to a google search.

Let's try this: Pretend I'm your 80 year old grandmother.

I presume I need to format/re-install Ubuntu 12.04 on sdc. How do I do this the proper way, making sure that it plays nice with sda/Win 8.1? I don't want to have to reformat both drives unless I have to, because it will take hours to reinstall all of the programs and customize windows the way I like it. I can reinstall Ubuntu with less headaches, although I wish the stupid thing would just install properly the first time. There's no reason why dual booting should be this complicated/difficult.

P.S. I followed these instructions when installing Ubuntu 12.04, and clearly they don't work as intended: [http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by jferreir on 2014-01-21
bump?

---

### Post by oldfred on 2014-01-21
The link you had was for Windows 7, you have Windows 8 in UEFI mode. If you notice there was a link for UEFI boot in that thread, but Windows 8 has other issues like secure boot and always on hibernation.

With more than one drive you must use something else or manual install. And that makes it a bit more complicated as you either have to partition in advance or partition during install.
How you boot installer in either UEFI or BIOS is how it installs.

From UEFI menu you should have two boot options for flash drive, one UEFI and the other BIOS/CSM/Legacy or whatever your system may call it.

  I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. I prefer to partition in advance. See post #9 for suggested partitions.

This shows both BIOS & UEFI, if not in UEFI mode go back and reboot before installing.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jferreir on 2014-01-22
> **oldfred said:**
> The link you had was for Windows 7, you have Windows 8 in UEFI mode. If you notice there was a link for UEFI boot in that thread, but Windows 8 has other issues like secure boot and always on hibernation.

With more than one drive you must use something else or manual install. And that makes it a bit more complicated as you either have to partition in advance or partition during install.
How you boot installer in either UEFI or BIOS is how it installs.

From UEFI menu you should have two boot options for flash drive, one UEFI and the other BIOS/CSM/Legacy or whatever your system may call it.

  I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. I prefer to partition in advance. See post #9 for suggested partitions.

This shows both BIOS & UEFI, if not in UEFI mode go back and reboot before installing.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

So if I understand this correctly, I need to format the 128GB SSD so that it is partitioned using GPT and not MBR. To do this, I need to create a LiveUSB of Ubuntu 12.04, making sure that the system boots from the USB in EFI mode, and not the standard BIOS mode. Presumably, I would do this by pressing F12 or DEL at system startup, entering the system BIOS utility, and then selecting the EFI mode of the USB stick from the BIOS boot menu. Is this correct?

Once Ubuntu is loaded in EFI mode from the LiveUSB, I would then proceed to install the OS, choosing 'Something Else' from the partition menu. From there, how do I properly partition the drive so that it is GPT? I read that GPT partitioned drives do not have logical partitions, but the only tutorials I have found online involve logical partitions (like the link I followed previously, which was intended for dual booting Ubuntu/Win 7). Can you please tell me *exactly* what I need to do? The drive is 128GB and will be used solely for Ubuntu.  How much space do I allocate for each partition/division, and what options do I select? I re-read post #9, but I can't make sense of it - it's way too technical.

Frankly, I'm not sure why the 128GB SSD wasn't formatted as GPT in the first place. I had both OS's installed on their respective drives previously, and I was booting via GRUB where both Ubuntu and Windows 8 were listed. I was using an enterprise version of Windows 8 at the time, and I recently replaced it with the retail version of Windows 8.1 Pro. Would that have caused the issue? I still don't understand how I found myself in this mess.

P.S. If it helps, my motherboard is the Asus Z87-A, and I presently have 8GB of RAM.
P.P.S. I understand that Ubuntu 14.04 will be released in April 2014. Will I be able to simply upgrade Ubuntu, or will I have to go through this painful process from the beginning? I'm so fed up with Ubuntu right now that I may simply trash 12.04 and wait until April.

---

### Post by oldfred on 2014-01-22
Your motherboard is both UEFI and BIOS, you just need to select one and always boot in that mode.
How both Windows & Ubuntu install is the same as the mode you boot install media in. 

Many suggest disconnecting the Windows drive, so then you can just install using the auto install. But that will only give / (root) and swap.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Then create partitions as I suggested in post #9. 
Then use Something Else when booted in UEFI mode and assign the / partition to / and format ext4, assign the partition you want for /home to /home and format as ext4, if you have created swap in advance then it will auto find that and the efi partition will be found. If Windows drive still plugged in specify the drive with Ubuntu for boot loader install.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Your system is so new that you may need 13.10, or wait for 12.04.4 in early February. Either should let you upgrade to 14.04 after it is released. But I usually do a new full install.

---

### Post by jferreir on 2014-01-22
> **oldfred said:**
> Your motherboard is both UEFI and BIOS, you just need to select one and always boot in that mode.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Then create partitions as I suggested in post #9. 
Then use Something Else when booted in UEFI mode and assign the / partition to / and format ext4, assign the partition you want for /home to /home and format as ext4, if you have created swap in advance then it will auto find that and the efi partition will be found. If Windows drive still plugged in specify the drive with Ubuntu for boot loader install.



So, I have to boot into the LiveUSB of Ubuntu, partition the 128GB SSD using Gparted from within the LiveUSB, and then restart the computer back into the LiveUSB of Ubuntu, then install as "Something Else", and define the parameters of the partitions that I created using Gparted? Is that right? 

Again, I don't understand post #9, so you have to be absolutely explicit about how I install Ubuntu via the 'Something Else' option. Simply saying 'create your root partition' means nothing to me. You need to say something like "Assign XXXXX MB to sdc/5, select ext4, etc. etc.". You have to use simple language that a 5 year old will understand or else I will mess this up worse than it already is. Also, my system should be perfectly compatible with 12.04 since I was able to dual boot without issue only a few weeks ago.

I appreciate the help, BTW.

---

### Post by oldfred on 2014-01-22
Once you have partitions created then it is just like the screen shot I posted above. 

You choose that partition, you choose its format like ext4, you choose the mount like / or /home.

Post #9 is one suggestion for partitions and sizes, each user has different requirements, so you can adjust if you want. 

 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

You can read thru some threads with two drive installs.

 **Two Drive UEFI installs**
[http://ubuntuforums.org/showthread.php?t=2192378](http://ubuntuforums.org/showthread.php?t=2192378)
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

### Post by jferreir on 2014-01-22
Sorry, I still don't understand... 

I just formatted the drive as GPT. What in God's name do I do now? I see available space, but I have no idea how to partition the damn thing. Look, all I want is the recommended settings. That means the recommended swap space, the recommended boot space (or whatever), and whatever space I have leftover I want to use for the Home folder (which I understand as the C drive in Windows). 

I need you to tell me what partitions I need to create, and exactly how many MB to allocate to each. I have a 128GB drive, so the math should be simple. I would do it myself if I knew what the hell was going on here.

Remember, I'm only using this drive for Ubuntu, and I have a separate 3TB HDD for mass storage. So, what do I do from here...??? Also, it shows only 119.24GiB of available space. Is this normal?

---

### Post by oldfred on 2014-01-22
Partition takes space, and drive Mfg count in 1000, where every thing else is 1024's. So numbers never match.

Use gparted, make a 300MB partition format it FAT32 and add the boot flag. With gparted that makes it an efi partition when gpt partitioning is used.

Then for Ubuntu create a 25GB partition, and thenuse most of rest of drive (all but 2GB) as another partition for /home. You can format or not as we will tick format again during install. Then at end of drive make 2GB for swap. If you have 4GB or more of RAM you may never use swap and some do not like it on SSDs, but if never or rarely used it does not matter.

Then start install and use Something Else and choose the 25GB partition, change, and select ext4,  use a / (root), select larger partition select ext4 and /home. In combo box at bottom chose drive sdb or whatever your SSD drive is.
Screen shots I posted show the screen you see when choosing partitions in installer.

---

### Post by jferreir on 2014-01-22
What is a boot flag? And I presume the other partitions (25GB, /Home, etc.) should be "ext4"? Do I have to put a label on them too?

---

### Post by oldfred on 2014-01-23
When partitioning with gparted you can right click on the partition and you can choose boot options an set the boot flag.
I like to label partitions, but that is optional. It is only for your info. On my larger drive I have so many I have to label to keep track of which is which.

If not familar with gparted.
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Screen shot shows check on bios_grub, you want to check the boot flag.

---

### Post by jferreir on 2014-01-23
I figured out that you can only add the boot flag after the partitions have been created (i.e., after applying operations). Anyhow, I followed your instructions exactly and it still didn't work.

I partitioned the disk as instructed (GPT), installed from LiveUSB (booted via EFI), and the bootloader didn't work. I then ran Boot-Repair from the LiveUSB, and again, it didn't work. I then unplugged the Windows SSD entirely, did the standard Ubuntu install on the 128GB SSD, and the boot loader still doesn't recognize Windows 8.1. I did Boot-Repair again, and again it didn't work. 

I went into the system BIOS to disable the secure boot, but that option isn't available. I can only choose between "EUFI Windows" or "EUFI Other OS". There's no explicit option to disable secure boot. So, I selected "other OS", tried the various steps noted above (again), and still nothing. At this point, what is there even left to try? I'm certain my hardware is compatible because I was able to dual boot with Win 8/Ubuntu 13.10 previously via grub, so something is amiss here.

---

### Post by oldfred on 2014-01-23
Part of the issue could just be 12.04, It is about to be updated to 12.04.4 (Early Feb) with many of the updates like 13.10 has, but now is older and does not have all the UEFI updates the newer versions have.

Post link to BootInfo report. You can run from your live installer, but have to reinstall every time you reboot from live installer. Have both drives plugged in to see everything.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by newbie2244 on 2014-05-21
QUESTION: When you are in **grub**,  is there a listing of various files or is there just one option for selecting ubuntu?

---

### Post by oldfred on 2014-05-21
Grub is a boot loader, it does not show files.
But will show which files it is booting with in the grub menu boot stanza. 
You can see those with e on grub menu.

 General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

