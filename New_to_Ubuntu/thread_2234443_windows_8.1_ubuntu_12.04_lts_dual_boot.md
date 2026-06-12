---
title: "windows 8.1/ ubuntu 12.04 lts dual boot"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by mystmaiden on 2014-07-14
For the first time in 15 years, we just bought a new computer (rather than ones I have cobbled together with bits and pieces, used parts, etc and I want to set up windows 8.1 with ubuntu 12.04 LTS  (using a cd or dvd). Its worked beautifully for me with windows 7 but I seem to remember hearing of specific issues with 8.1 (which I can not find now naturally). Is the installation as easy as before and does windows 8.1 behave nicely with sharing files between the two? 

i'm so ready to get back to ubuntu after one day of windows only, lol.

thanks,

mystmaiden

---

### Post by oldfred on 2014-07-14
Major new complexities mostly caused by Windows adding secure boot, converting to always on hibernation and other issues depending on how vendor has configured system.

Most of the better links are in the link in my signature.

Backups vital, best to use Windows to shrink the NTFS partition and reboot immediately to let it run chkdsk and make whatever repairs it wants. 
You must have fast boot (hibernation) off, and often better to have secure boot off.

What brand computer?
Some like HP and Sony have modified UEFI to only boot Windows. There are several work arounds to make it think it boots Windows but really boots grub.

I do not think I have added these yet to link below:
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Winodws disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by mystmaiden on 2014-07-14
Thank you for the reply, oldfred. This is an hp (unfortunately from the sounds of it) making me wish I had found one with windows 7 on it. I'll read through the links you posted. I did notice one thing already I disliked about windowas 8.1 - it seems to be using my microsoft account password to boot up - I find that way unacceptable.

thanks again

mystmaiden

---

### Post by oldfred on 2014-07-14
Vendors often have similar UEFI across models with just differences for options. 
Some other HP systems.

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
HP Touchsmart 15
[http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041)

---

### Post by mystmaiden on 2014-07-15
Once again, thanks for the great information. I have been reading through the links and I have to admit that a lot of the info is just plain over my head. I'm considering ordering a windows 7 disc and just wiping windows 8.1 - I only use windows for a couple of art programs. This being a new computer and an hp, will win 7 easily dual boot with ubuntu as it has on all my older computers or will it too run into the same difficulties as windows 8.1? Also will the hp load just ubuntu if I should decide to abandon windows altogether?
Just trying to get a handle on my options here... this is all pretty daunting.

---

### Post by oldfred on 2014-07-15
If you just install Windows 7 from a DVD, it defaults to BIOS boot mode. That converts gpt partitioned drive to MBR(msdos), but Windows does not do a complete conversion. You have to use fixparts to remove the backup gpt partition table or Linux will see both MBR & gpt and not know what to do.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You can convert a Windows 7 DVD to a flash drive and do updates to make it UEFI boot capable installer. 
      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Windows only boots from a gpt partitioned drive with UEFI.
Both Windows and Ubuntu only boot from a MBR partitioned drive with BIOS/CSM/Legacy boot mode.

Windows 7 does not use secure boot and does not have auto hibernation or fast boot. But you still should not hibernate Windows if dual booting.

Best to do full backups whatever you decide to do:

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

There was some discussion where Microsoft did not want newer hardware to have drivers back ported to Windows 7 or you could only use Windows 8 and not revert. So far have not seen any issues, but if you add hardware down the road it may be an issue.

You should be able to install just Ubuntu in either UEFI mode, but will need workarounds or in BIOS boot mode.
      CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by mastablasta on 2014-07-16
i would stay on Windows 8.1. it's rigid, but you can still modify it so it works with ubuntu and have a descent desktop ocmputer experience. oh and use 14.04 LTS instead of 12.04 LTS - for better hardware support on newer PC.

if UEFI is not locked to Windows you should be able to dualboot. if UEFI is locked to booting Windows i am not sure it will boot Windows 7.

while some HP laptops are locked to Windows, others actually come preloaded with Linux.

---

### Post by mystmaiden on 2014-07-23
Again, thanks for all the replies. After  a lot of trial and error, I got secure boot disabled, tried to use a dvd several times and legacy option. I did determine that this model simply does not boot from a disc. Finally found one usb drive I had linux 12.04 on and it installed fine. I ran grub repair with the hard coded advanced option checked and everything worked fine, ubuntu booted, windows booted. I realized though that for this newer machine, I really did need the 64 bit 14.04 lts , so I redid the usb stick I had to use 14.04. It installed fine, I ran boot repair with just the recommended options(no joy) . Alas, I screwed something up along the way because I get post and what looks to be a command line but nothing boots. Ran boot repair again with the hard coded option checked but still no luck.

here is the boot repair url [http://paste.ubuntu.com/7844201](http://paste.ubuntu.com/7844201)

---

### Post by oldfred on 2014-07-23
You must not have read the WARNING in the link in my signature on reinstall.
You overwrote Windows.

And much better to only have a smaller / (root) partition of 25GB on TB sized drives. Use rest of drive for /home or data partitions.

Did you intend to overwrite Windows?
Did you make a full backup of Windows?

---

### Post by mystmaiden on 2014-07-23
I did not intend to over write windows entirely. I don't have a cloned disc of windows but do have a recovery usb I made with the recovery partition on it, Not sure if that's enough to restore windows. If I don't have windows the world won't come to end providing that I can boot ubuntu... question is will this hard coded machine boot ubuntu without windows present. something tells me it won't

---

### Post by oldfred on 2014-07-23
We can create the Microsoft folder in the efi partition and name either grub or shim's efi files to have the Microsoft efi boot file.
UEFI will think it is booting Windows but really boots grub.

Typical boot folders. You may only have /efi/ubuntu
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

But you can create both /efi/Boot & /efi/Microsoft and then /efi/Microsoft/Boot as new folders. Copy grubx64.efi & shimx64.efi from /efi/ubuntu/grub into each folder.
In /efi/boot rename grubx64 to bootx64.efi, if file already exists you may not have to change it but changing this is better than changing Windows efi file if actually dual booting Windows.
In /efi/Microsoft/Boot change grubx64.efi to bootmfgw.efi.

---

### Post by mystmaiden on 2014-07-24
Thank you for your help oldfred, I'm sorry I blew it so badly after you gave good info. I know it must be frustrating when people miss a warning you have given like I did. The good news is, if you have a recovery usb with the recovery partition on it, it is possible to reinstall windows - at least it finally worked for me (but its incredibly slow!!) I'll start over fresh with an install of 14.04 LTS. Just to be sure - Is it okay to choose the alongside windows 8.1 or should I choose the something else option? Windows is currently the only os on the machine

---

### Post by oldfred on 2014-07-24
Glad you had a backup that worked. :)

At this point with Ubuntu and how it likes to over install things, I really suggest using Something Else. Its just that that is more complicated as you do have to understand a bit about partitions and have at least a / (root) partition formatted ext4. Better to add swap and /home or data partitions. And if dual booting a NTFS shared data partition makes it easier & safer to share data between systems.

Use Windows to shrink the Windows NTFS partition & reboot immediately so it can run chkdsk and make repairs.
Make sure fast boot or always on hibernation is off. Not just a standard shutdown.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by mystmaiden on 2014-07-24
Thanks :) I think that I'm in over my head with the partitioning you mentioned above. I've been dual booting for a few years but have always gone with what Ubuntu offered. My computer has 8 gigs of ram and about 880 gigs of space unused some of which will be needed for windows.  Would I put the shared NTFS space at the very end of the drive?

---

### Post by oldfred on 2014-07-24
Shared space can be anywhere on drive. Both Linux & Windows will recognize it. But with Linux you have to modify fstab to permanently mount it. Of course you can just click on it with Nautilus and it will mount with defaults.

Examples so you can see screens before doing it.
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Winodws disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Other something else installs:
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by mystmaiden on 2014-07-25
EDIT - founs the swap option was  looking on the wrong line sorry

---

### Post by mystmaiden on 2014-07-25
All installed now. I ran boot repair and under 'recommended repair  - it booted properly once but now it goes straight to windows. Here is the log from boot repair  [http://paste.ubuntu.com/7861215](http://paste.ubuntu.com/7861215)'

---

### Post by oldfred on 2014-07-25
Some systems will only boot Windows, and Windows 8 will keep making itself first in UEFI boot order.
Can you choose ubuntu entry from UEFI or from one time boot key, often f12 but varies by vendor.
>  BootOrder: 0000,0001,0002,0009,0003,0004,0005,0006,0007
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0003* ATAPI CD-ROM Drive
Boot0004* CD/DVD Drive
Boot0005* USB Floppy/CD
Boot0006* Hard Drive
Boot0007* Realtek PXE B03 D00
Boot0009* UEFI: SanDisk
Boot0000* ubuntu.

    

With your HP you should rename bootx64.efi and make it grubx64.efi and boot hard drive.
       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
            HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

    
       Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

---

### Post by mystmaiden on 2014-07-26
This has about got me completely whipped.

The UEFI boot list comes up with f9. When I choose ubuntu from it - it returns 'no boot device found.' If I go in and change the boot order to put ubuntu above windows, it works but only once.

I tried 
```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```

(both with and without the quotes ) - no joy there.

Can the solution using the DEB packages be used from live ubuntu?

thanks -
 mystmaiden

---

### Post by oldfred on 2014-07-26
I still think it is the HP UEFI and its desire to only boot Windows.

Several threads had how others with HP renamed boot files to make it work for them.

Most did this:

  Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

---

### Post by mystmaiden on 2014-07-27
I've been very nervous about attempting this file renaming operation. If I could just boot puppy and pop in there and change them back in the event of a mistake I wouldn't be, but that doesn't seem to be the case any more. What's the best way to back them up beforehand? I looked at file history in windows but it seems to be just for personal files.

---

### Post by oldfred on 2014-07-27
The efi partition is not large & you should just back it up anyway. With the efi partition there are no hidden sectors that are needed to boot, it all is just the files in the efi partition and can just be copied back.

I did not think Puppy worked with UEFI, so it may only boot if you change settings in UEFI/BIOS to boot in BIOS mode not UEFI mode.

---

### Post by mystmaiden on 2014-07-27
just in case someone else is curious - I was able to get puppy booted from a usb (no cd/dvd worked) but the windows drives seemed to be locked, you can see some windows files but I've been unable to interact with them as yet. Puppy works fine otherwise once secure boot and fast boot disabled. Its just not helpful in this instance, maybe there is a workaround but I have been too busy with ubuntu to check it out.

But back to my troubles. How specifically to back up the files in that partition? Copy them to a separate usb drive or use something in windows to back them up? Everything I know about windows would fit in the back end of an ant and I don't want to reinstall windows again if I can avoid it after my last goof up. i haven't used windows with any regularity since early xp days. I only keep it for two art programs

---

### Post by oldfred on 2014-07-27
I shut down XP as the last Windows I ran, do any details on Windows that I post if from others.

I would just use whatever backup tool you like to copy the entire efi partition onto another drive, flash drive or DVD.
I regularly use all of those for some of my data. I prefer rsync for copying to another drive. But have just used Nautilus to copy copy folders to a flash drive. And I use k3b to backup as much as will fit on my DVD about every quarter as my data does not change a lot.

---

### Post by mystmaiden on 2014-07-27
I found windows/Boot and copied the whole file to a usb drive. from  there I went to /Boot/EFI  - here's where it gets confusing if I am in  the right place. There are numerous files named just a few letters  starting with b and going to z. Each contains a bootmgfw.efi.mui, a  bootmgr.efi.mui some also contain an memtest file. At the very bottom of  the list are boot.stl. bootmgfw.efi, bootmgr.efi.mui, memtest.efi (without folders).

---

### Post by oldfred on 2014-07-27
I think Windows has all the languages in the efi partition. Those probably are those. But entire partition at top level should be easy to copy.

Typical folders in /efi for booting.
       /EFI/Boot
/EFI/Microsoft
/EFI/ubuntu

So at /EFI you should be able to copy entire partition.

---

### Post by mystmaiden on 2014-07-28
I checked this morning, there are no other /EFI folders that I could find. Just the one I mentioned which is Windows/Boot/EFI so I don't have any of the folders you mentioned. Not sure what to make of that. Do you suppose going through setup is the only option I have once I've booted windows and then want to boot ubuntu?

---

### Post by oldfred on 2014-07-28
Someone posted this for HP, does it work the same for your system?
 1) press esc key while booting to access start up menu 2) press F9 for boot devices menu.

---

### Post by mystmaiden on 2014-07-28
I just checked, once windows has been booted, I still have to go back in and change the boot order to get to ubuntu. Is it hard on the machine to have to change the boot order so often?

---

### Post by oldfred on 2014-07-28
Should be no different than any other change.
How are you changing boot order? 
Or are you just selected Ubuntu from one time boot key?

---

### Post by mystmaiden on 2014-07-28
let's see if I can explain this clearly... once I set ubuntu above windows in setup (press F10, go to 'storage' and then 'boot order' in bios) I can boot ubuntu over and over from the normal purple boot screen but if I choose windows on that list I can not use ubuntu until I go back into bios and move ubuntu up the list again.

---

### Post by oldfred on 2014-07-28
Windows & some UEFI modify boot order, so Windows is first.

That is where the rename of bootx64.efi to boot grub may work as that is just the hard drive. Or other renames.

Each of these have been reported as work arounds, but some work better on some systems. Try a1 first, then perhaps c: or d:.

 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
**a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
**a2:**(this is the same as what Boot-Repair does in B:. 
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmfgw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmfgw.efi entry which is now just grub, so it will not work.

   Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by oldfred on 2014-07-28
This user has Windows 7 but used choice c: or the bcdedit.

[http://ubuntuforums.org/showthread.php?t=2236311](http://ubuntuforums.org/showthread.php?t=2236311)

---

### Post by mystmaiden on 2014-07-28
Thanks so much, oldfred , for working so hard at trying to get this going. As I mentioned before, I tried the bcdedit option but it had no effect. Nor am I comfortable trying to rename files that don't exist on this system, the only thing I haven't tried was rfind or refind (spelling?) I may try it later. For right now I'm going to stop here. 

Again, thanks so much for all the help. You've been amazing

---

### Post by mystmaiden on 2014-07-29
Oldfred, I found out quite by accident late last evening that the files I was claiming do not exist on my machine are definitely there so I can't have been looking in the right folders at the onset. I was fiddling about with Puppy linux and clicked on the wrong drive - lo and behold - there it was in all its glory. I also believe I was wrong about not being able to fix them from puppy any more. I looked up this morning information about changing those files from inside windows and there are some pretty complicated steps for that, so if possible I will simply rename and move them around with puppy later today  and see if it works. At any rate, you were right all along and I was both lost and dead wrong.

---

### Post by oldfred on 2014-07-29
Now you are learning your way around. 
Next you will be back helping the kids with their computers. :)

My 2yr old grandson is already using iPad to play games.

---

