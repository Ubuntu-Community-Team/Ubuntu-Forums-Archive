---
title: "Installation instructions for my dual boot Windows 7 and Ubuntu"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by ryan.crazyemu on 2014-04-03
I've completed a new build and I would like to make it a Windows 7 and Ubuntu dual boot system. I am brand new to Linux and, while I have done a lot of research into ways to partition my drives and so on, I am not super clear on how to do the installs properly. I want to get these installs right the first time, so I am hoping someone can give me a clear step-by-babystep to guide me through this process. Please remember I'm a newbie with Linux and with installing OS's in general :)
I have brand new drives and am going to be doing CLEAN installs. My basic understanding is:
Install windows first. Use the windows installer to set up the windows system partition on the SSD and the NTFS data partition on the HDD, leave the remaining spaces unallocated for now.
Install Ubuntu next. Use the installer (GRUB if I'm not mistaken) to set up the Ubuntu partitions on SSD and HDD, choosing where to mount each partition (/, /home, etc).
The OS's are now installed... Set up any symlinks, mounts, and so on

If it's any more complicated than I described in 1) and 2) (which I'm 100% sure it is), then I could really use some guidance on the finer details: what to do and when to do it, things to make sure of, boxes to check, etc, etc.
My motherboard is an ASUS Z87 Pro, which I believe is UEFI. I've read that UEFI may require special care in installing Windows and Linux for dual boot (have to use gpt partitions, etc). What are the steps and things to check in each installation process for this situation?

I intend to have both OS's on an SSD (120GB Samsung 840 EVO), with data and a couple other partitions on an HDD (1TB Caviar Blue) My intended partition scheme (assuming gpt partitions, which may be a bad assumption?):SSD - 120GB (Samsung 840 EVO):
[C:] 80GB (NTFS) -> Windows system partition
[sda1] 20GB (ext4) -> /
[sda2] 15GB (ext4) -> /home ... (moving folders for docs, media files, to HDD)

HDD - 1TB (Western Digital Caviar Blue)
[D:] ~800GB (NTFS) -> NTFS Data partition (Windows and OS-shared data)
[sdb2] ~100GB (ext4) -> Ubuntu-only data partition
[sdb3] 2GB (ext4) -> /var
[sdb4] 4GB (ext4) -> /tmp
[sdb5] 8GB (ext4) -> /swap (= my 8GB RAM for hibernation)
(if you have comments on my scheme, I'd appreciate hearing them, but that's not the point of this question)

A clear walkthrough of the installation processes for my case would be EXTREMELY appreciated. Thank you!

---

### Post by mastablasta on 2014-04-03
how much ram do you have?

i wouldn't overcomplicate things.

on SSD
create NTFS 80 gb and install windows on it. 
use the rest of the space unformated for ubuntu. in installer use option to install next to windows. it will automaticly create / (root) and /SWAP

if you have enough ram you probably won't ever touch much of /swap anyway. and you don't really need separate /home. i mean if you ever want to reinstall just backup the home to the NTFS drive, reinstall the OS and restore /home

HDD
format the whole one as NTFS and use for data storage. NTFS can be accessed well from Windows as well as form linux. you just won't be able to install linux programs there (which you don't seem to plan anyway).

why do you want separate /var and /tmp partitions?


about UEFI have a look here first: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Double.J on 2014-04-03
Hi there!

good choice on board! 

To be honest, the asus boards are pretty much the best for configuring secure boot. As you are home building, there shouldn't be too much trouble with win7 and ubuntu! Last few asus board (z77) I've installed windows 7 on haven't even had SB turned on to start with!

i'd agree you don't usually need a seperate /home in a dual boot because you'll likely be using the shared drive. If you see yourself reinstalling a lot - more than just release to release, then a separate home makes sense as you can just  mount it again in the new system and save some hassel.

i'd agree shared data ntfs partition is what i do - each  linux install has 15-25 gb only. 100gb seems a lot of space to have almost inaccessible in windows.

as for separate temp and var... I've not done that since my gentoo days 7/8 years ago, not had any issues. The idea behind it is that tmp var and home grow a lot over the life of an install so separating them means that the root fs does not become full and impede the speed of the os. The disadvantage is that you essentially resign disk space to waste so you don't run out of space in tmp and var. 

in my experience home installs of ubuntu have little to gain from doing it against the risk of an fs not mounting following an update!

---

### Post by oldfred on 2014-04-03
Windows 7 will not do secure boot and DVD will not do UEFI install, just BIOS. 
But you can convert DVD to flash drive and make it a UEFI installer.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Some in the past have suggested some Ubuntu system folders on rotating drive to prevent "wear" on SSD. But new SSD now have similar lives to HD (but not forever).
My goal has always been to have a fully bootable system on every hard drive and data on various hard drive(s).
I currently have my SSD with two / (root) partitions one my working 12.04 and soon second my new working 14.04. I have a about a 28GB / with 11GB used including /home inside /. But I move all data to rotating drive and link back including some hidden /home files & folders with more data like Firefox & Thunderbird profiles.

I would not separate / & /home on SSD since /home will not be large compared to /. It then just becomes one more partition to manage. If most data is on hard drive, /home is not large and easily backed up regularly and restored if you have to reinstall.

I dual booted with XP for years, but do not have huge data requirements. I (still) have a 100GB NTFS shared data and a 100GB Linux formatted /mnt/data partition for data. Since not booting XP since SSD added as XP would not work with AHCI, I have not reconfigured to eliminate NTFS shared data partition.

Note seen many threads on issues with Asus motherboards, which probably is a good thing.

 ASUS Rampage IV Extreme motherboard
[http://ubuntuforums.org/showthread.php?t=2063073](http://ubuntuforums.org/showthread.php?t=2063073)

Be sure to also partition rotating or data drive as gpt. I might include an efi partition at beginning of drive just in case you ever wanted to add another install to test or experiment with settings. It can be difficult to add efi partition at beginning of drive when drive is fully partitioned with lots of data. And efi partition of 200 or 300MB is not large compared to sizes of new drives.

---

### Post by ryan.crazyemu on 2014-04-04
Thank you all for the great responses and links.  I have some questions and clarifications I'd like to ask about...

Just to make sure I understand - this is the outline for the installation process as I understand it (please correct me if I'm wrong or confused):
[LIST=1]
[*]Use the instructions on [this page]("http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html") to make a bootable UEFI USB with a Windows 7 installation ISO using Rufus
[*]Use the instructions on [this page]("http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html") to install Windows from that bootable UEFI USB
[LIST=1]
[*]Partition the SSD leaving room for Ubuntu using the Windows 7 installer (questions about partitioning below)
[/LIST]

[*]Make a bootable CD with the Ubuntu 12.04 ISO
[*]Boot from the CD to run the Ubuntu installer
[LIST=1]
[*]Use the 'Something else' installation type so I can specify partitions (questions about partitioning below)
[/LIST]

[*]Move some /home subdirectories to HDD, other configurations for Linux. **What should I do to get my Ubuntu setup and optimized at this point?**
[/LIST]

Based on your feedback I'm looking at having the following partition scheme:
> [COLOR=#000000][FONT=tahoma]SSD - 120GB (Samsung 840 EVO):[/FONT][/COLOR]

[LIST]
[*][FONT=tahoma][C:] 80GB (NTFS) -> Windows system partition[/FONT]
[*][FONT=tahoma][sda2] 25GB (ext4) -> /[/FONT]
[*]*[FONT=tahoma][I][FONT=tahoma][sda3] 8GB (ext4) -> [/FONT]*/swap??? (or on HDD)[/FONT][/I]
[/LIST]

[COLOR=#000000][FONT=tahoma]HDD - 1TB (Western Digital Caviar Blue):[/FONT][/COLOR]

[LIST]
[*][sdb1] 300MB (what file system?) -> exi partition (for future)
[*][FONT=tahoma][sdb2] ~900GB (NTFS) -> NTFS Data partition (Windows and OS-shared data)[/FONT]
[*][FONT=tahoma][sdb3] ~100GB (ext4) -> Ubuntu-only data partition[/FONT]
[*]*[FONT=tahoma][sdb4] 8GB (ext4) -> /swap??? (or on SSD)[/FONT]*
[/LIST]
[I][FONT=tahoma]
(I have 8GB RAM)[/FONT][/I]



Questions about partitions...
[LIST=1]
[*]Do I need to do anything other than install from the UEFI Windows 7 USB to have gpt partitions on the SSD?
[*]Do I create a partition(s) for Ubuntu during the Windows Installer or just leave unallocated space for the future Ubuntu partitions?
[*]Where should I have my /swap partition?
[*]When and how do I partition the HDD? What will it take to make them gpt partitions?
[*]Does creating an efi partition at the beginning of the HDD require a special process? Or do you just create a partition with the desired size, label it as efi partition, and leave it for later? (no need for it now)
[/LIST]

---

### Post by mastablasta on 2014-04-04
i will just reply what i know since i am not familiar with UEFI or gpt.

> **ryan.crazyemu said:**
> Do I create a partition(s) for Ubuntu during the Windows Installer or just leave unallocated space for the future Ubuntu partitions?


Widnows can't create linux partitions. Linux can create widnows aprtition. leave it unalocated and partition that space with linux installer.
> 

Where should I have my /swap partition?

You can have it on SSD. you probably would use it much. if you want more space on SSD then move it to HDD. Also 4 GB might be enough for swap. someone else will maybe say more about this. 
> 

When and how do I partition the HDD? What will it take to make them gpt partitions? 

unless you plan to put swap on hdd then you can partition it later after the OS is installed.

i am not sure why do you think you would need an EFI parittion on HDD?

---

### Post by Double.J on 2014-04-04
Hi there,

so, some thoughts on swap:

Total swap must be equal to or greater than RAM for hibernation.
With 8GB of ram, you are unlikely to be doing a lot of swapping.
the ssd will be a lot faster than the hdd.
excessing writes to the ssd will shorten it's life.
you can have more than one swap partition.

so hibernate will wake a lot faster if it's all on the ssd, but you reduce precious SSD space. Also if you do find yourself using swap, then performance will be better. Now ssd life times are partly depend on writes. However you have to write 10s of gb a day for years on most drive to achieve this. It could, however be an issue if you are say a video editor that would have cause to hibernate the machine many times a day. The main argument against is using up too much space (8gb)

what you can do is put say 2gb on the ssd and 6/7gb on the hdd. You can add both swaps to the fstab and make the ssd partition the primary swap partition so that you use the ssd first and the hdd once that i full?

---

### Post by Double.J on 2014-04-04
Sorry I realised I should have put an example!

so the swap portion of your /etc/fstab usually looks a bit like this:
```
 #swap was on /dev/sdawhatever during installation
UUID= 81ah-81ah-81ah none      swap      sw       0  0
```
it might say defaults instead of swap, or use /dev/sdwhatever instead of UUID

The change is to add the second partition same as the first, and add the priority argument.
```
 #swap was on /dev/sdawhatever during installation
UUID= 81ah-81ah-81ah none      swap      sw,pri=1       0  0
UUID= 81ah-81ah-81ah-2 none      swap      sw,pri=2       0  0
```
the pri numbers can be anything, but the order of their value dictates which is written to first. If the numbers are the same, they are written to simultaneously.

Note that if it said defaults instead of sw, change it to sw,pri=

---

### Post by oldfred on 2014-04-04
With 8GB of RAM, I would not put swap on SSD and I would only put maybe 2GB on hard drive just to have a little. You will never use it. And with an SSD it will boot fast enought that hibernation will not be worth the hassle and barely quicker if at all.

My laptop with 1.5GB uses swap when I load more than one large program or a lot of programs. It then goes grey for a second and is really slow. My Desktop with 4GB of RAM never users swap but then I do not load a lot of apps at once. You really do not want swap used as it is a lot slower.

The efi partition is FAT32 formatted with the boot flag (if using gparted), but if just leaving space for possible future it does not matter. If using gdisk it is an ef02 partition. The efi definintion is a very long GUID or unique id and software adds that to partition with shorter boot flag or ef02 labels that are easier to add.

Both Windows & Ubuntu have to be booted in UEFI mode to install in UEFI mode. And if in UEFI mode both will create gpt partitioning. Your sdb drive if partitioned with gparted will have to be specified.
       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Windows will use entire SSD unless you partition in advance. But Windows in UEFI needs extra partitions, so probably better to let it create what it needs. Then use Windows partition tools to shrink Windows to make unallocated space for Ubuntu. Reboot into Windows so it can run chkdsk and its repairs to see its new size or the Ubuntu install may not see the Windows install.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by ryan.crazyemu on 2014-04-04
Thanks again for the responses. I think I'm getting a better idea of how to do this.

So to make sure I understand, here are the steps I should be following (_please correct me if I'm wrong_): 
[LIST=1]
[*]Make a bootable UEFI USB with a Windows 7 installation ISO using Rufus
[*]Go into BIOS to make sure USB is set to boot in UEFI mode.
[*]Install Windows from that bootable UEFI USB
[LIST=1]
[*]Let Windows partition the SSD how it wants and use the whole SSD for now. It will use gpt partitions since the installer booted in UEFI mode.
[/LIST]

[*]Use Windows partition tools to shrink Windows to make unallocated space for Ubuntu (one partition for /). Reboot Windows.
[*]Run gparted in windows to partition HDD. Make sure to select gpt over the msdos default.
[LIST=1]
[*]Create 300 MB FAT32 efi partition, make sure to set boot flag. Not mounting anything here now.
[*]Create two data partitions - 900GB for shared data (NTFS, no special settings) and 100GB for Ubuntu only data (ext4, no special settings)
[*]Create small /swap partition at the end for just in case (ext4, no special settings)
[/LIST]

[*]Make a bootable CD with the Ubuntu 12.04 ISO
[*]Go into BIOS to make sure CD is set to boot in UEFI mode.
[*]Boot from the CD to run the Ubuntu installer
[LIST=1]
[*]Use the 'Something else' installation type so I can specify partitions.
[LIST=1]
[*]I will have to set the /boot/efi mount point to the EFI partition. Use the EFI partition that already exists on SSD from Windows 7.
[*]Set up partitions
[LIST=1]
[*]Put / in the unallocated space on the SSD (made using Windows partition tools)
[*]Put /swap in the swap partition made using gparted on the HDD
[*]_What exactly will I do (what do I mount?) to set up the Ubuntu-only data partition (made using gparted)?_
[/LIST]
[/LIST]
[/LIST]
[/LIST]

Other questions:
[LIST]
[*]Will Windows 7 access the large NTFS data partition on HDD automatically after the above steps? Will Ubuntu?
[*]Should I worry about the where the Ubuntu boot loader goes? Is that unnecessary for me?
[*]Do I need to mess with the BIOS boot menu?
[*]What should I do to configure/optimize Ubuntu once installed?
[/LIST]


Thanks again, you are all most helpful :grin:

---

### Post by oldfred on 2014-04-04
Swap is unformatted, so do not format, just flag as swap.
If swap exists, the installer finds it and you do not have to specify it.
With Something else you can create partition for / or when partitioning rotating drive you can create partition on SSD for root also. You do not have to format as during install you will format it.
Ubuntu installer is now way oversize, so you have to use DVD. I prefer flash drives as install is quicker and then you can reuse.

But always have a working Ubuntu live installer of currently installed version or with Windows a repairCD or flash drive so you can make repairs.

Windows is good about finding other NTFS formatted partitions, so you immediately should see a d: "drive".

But Ubuntu is a bit more complex since it is multi-user and lets you name/label partitions with names that mean something not just d:. And you have to give yourself ownership & permissions. It will auto mount in Nautilus file manage a partition you click on with the label you have given it. But if permanent you want to make a permanent mount point and add an entry to fstab. We will do that after install is working.

I label all partitions, but may use a different name to mount in my install. I have many partitions mostly temp installs and label lets me know which is which. I have labeled my /mnt/data partition Data and in Linux case makes a difference so you have to be careful not to get confused.

After installing we can review ownership, permission and permanent mounts.

---

### Post by ryan.crazyemu on 2014-04-05
Ok! I *think* I have successfully installed both OS's and have the drives partitioned how we outlined. I can boot up both OS's, system settings look ok, connect to the internet, and so on. BUT when I turn on the computer, it just boots straight into Windows - no sort of boot menu appears. Right now I am going into the BIOS and using the boot menu in the BIOS to get to ubuntu. Also, the BIOS lists ubuntu twice (same drive listed in menu choices, character for character identical menu entries). So this is the first thing I want to get straightened out now that both OS's are installed, hopefully you guys can help.
 
(I also installed some hardware drivers in Windows and some Windows updates installed at this point. Haven't touched anything in ubuntu yet).

---

### Post by oldfred on 2014-04-05
I have seen several others with dual entries. Check that both work.

With UEFI you have to go into UEFI and choose which to boot by default. Move Ubuntu entry to top of boot order.

Some better UEFI have boot manager that can add, edit or delete entries. Otherwise you have to manually do it with efibootmgr.

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)
Script to semi-automate efibootmgr changes -  user slooksterpsv  in forums
[https://launchpad.net/~slooksterpsv/+archive/efibootorder](https://launchpad.net/~slooksterpsv/+archive/efibootorder)

---

### Post by ryan.crazyemu on 2014-04-05
*sudo efibootmgr -v* returns:

> BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0004
Boot0000* Windows Boot Manager    HD(1,800,32000,8a2dd663-f97a-44be-939e-b2384b25c73b)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu    HD(1,800,32000,8a2dd663-f97a-44be-939e-b2384b25c73b)File(\EFI\ubuntu\shimx64.efi)
Boot0004* ubuntu    HD(1,800,32000,8a2dd663-f97a-44be-939e-b2384b25c73b)File(\EFI\Ubuntu\grubx64.efi)

Which do I want to delete?

---

### Post by oldfred on 2014-04-06
One is shim and one is grub.
Shim is the secure boot or signed verison of grub.
Are you using or planning on using secure boot?
Do both entries work? I thought grub was going to use shim for all installs whether secure boot or not, just to have one version, but do not know for sure.

---

### Post by ryan.crazyemu on 2014-04-06
Both entries do work, yes.  I hadn't planned on using secure boot, but that's because I wasn't aware of it. Should I? What course of action should I take?

---

### Post by oldfred on 2014-04-06
Frankly I would just set one or the other as default and not worry about it. You should not normally be using UEFI or one time boot key if grub is working correctly.

I also would not use secure boot. That is a Windows Marketing tools more than anything. They have had so many secuity issues they had to do something. But Booting virus have been a minor issue in the past. If in the future it becomes an issue you can then change to secure boot.

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by ryan.crazyemu on 2014-04-07
Ok I'll make the grub have priority over the shim.  However, I am still wondering if there's a way to have a boot menu come up every time the machine starts up without having to go into the BIOS.  Right now if you just turn on the machine it just boots into whichever OS is set to default in the BIOS.  I'd like to be asked what I want to boot into automatically at startup without having to enter the BIOS.  Is there a way to accomplish this?

---

### Post by oldfred on 2014-04-07
If you have grub as default in UEFI, then you should get grub menu which offers to boot Ubuntu or Windows.
If you are not getting grub menu, run this. 

sudo update-grub

But grub does not show menu unless it sees more than one operating system. If Windows is hibernated (or fast boot on) or needs chkdsk, grub2's os-prober cannot mount the NTFS partition and may not add Windows. Or did you install Windows in BIOS mode. Then UEFI grub cannot boot Windows in BIOS mode.

---

### Post by ryan.crazyemu on 2014-04-09
Still not getting the grub menu :/ 
 
I ran sudo update-grub.  I also did 'sudo efibootmgr -o 0004, 0000, 0001' to set the grub Ubuntu to have priority. 

I checked in Windows Disk Management that there is the 100MB EFI partition in front of the Windows partition (which I understand indicates it installed in UEFI mode), and it's there. I am restarting or shutting down completely and starting back up so Windows is not hibernating. 

How can I diagnose this? thanks again for the help

---

### Post by oldfred on 2014-04-09
You showed a Windows efi boot file entry.
But if you have a 100MB NTFS Windows boot partition that is BIOS boot not UEFI.

       Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

And if Ubuntu is in UEFI mode, it will not see the Windows to add it to grub.
And if grub only has Ubuntu entry it will not show grub menu.

      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

