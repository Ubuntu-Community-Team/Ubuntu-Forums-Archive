---
title: "Having trouble with UEFI, two drives, win7 and ubuntu 12.04"
date: 2015-06-26
forum: New to Ubuntu
---

### Post by rcollins0618 on 2015-06-26
I've tried BCDEdit (which worked on my laptop with only one drive just fine), but that gives me an error that says:
"Windows failed to start. " ... 
"File: \NST\AutoNeoGrub5.mbr"
"Status 0xc0000098"
I've searched that status, and options related to my problem and came up short.
I didn't want to try too many things that I didn't understand for fear of locking myself out of Windows or messing up the GPT.

I've also tried Boot-Repair according to the following guides:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

a little background:
My computer boots in UEFI mode. Windows 7 was installed first (came pre-installed, Dell/Alienware).
I have 2 hard drives. One is an SSD (windows is installed here), and the other is a 4TB HDD.
I resized the NTFS partition on the 4TB drive to make room for Ubuntu, and installed it from UEFI mode.
The partitions I'm using are a 200GB root partition and a 16GB swap partition. There is no boot partition, but there is 512MB set aside in case I need to make one.
I must use Ubuntu 12.04LTS for my work, and I can not uninstall windows or screw up what's already on either drive.

Rebooting and selecting the second UEFI option ("UEFI: SAMSUNG SSD SM841N 2.5 7mm 256GB" instead of "Windows Boot Manager" or the Legacy Boot options) very quickly scrolls "**error: efidisk read error.**" repeated at the bottom of the screen and then brings me to a Grub 1.99 command line. Here, I've experimentally found that if I type:
" **configfile (hd1,gpt1)/efi/ubuntu/grub.cfg** ", it will load the menu from which I can load Linux.
" **configfile (hd3,gpt3)/boot/grub/grub.cfg** " boots Ubuntu as well.

If I don't type that, but instead just type "set" at the grub> prompt, the following output is displayed:[INDENT]color_highlight=black/white
color_normal=white/black
feature_timeout_style=y
pager=
prefix=(hd1,gpt5)/EFI/ubuntu
root=hd1,gpt5
[/INDENT]

(hd1,gpt1) points to the standard 512MB EFI partition on the SSD.
(hd1,gpt5) points to the windows installation root directory (C:\).
(hd3,gpt3) points to my Ubuntu 12.04 root directory, which also includes the \boot\

" **cat (hd3,gpt3)/boot/grub/grub.cfg** " is (i think) the long generated, updated grub file that I get when I do the two grub commands. (update-grub and grub-install i think)
" **cat (hd1,gpt1)/efi/ubuntu/grub.cfg** " returns the following:[INDENT]search.fs_uuid 21a46813-570d-4608-a8af-871a4be83253 root
set prefix=($root)/boot/grub
configfile $prefix/grub.cfg
[/INDENT]

" **echo $root** " yeilds: " hd1,gpt5 "

" **cat (hd1,gpt5)/boot/grub/grub.cfg** " yeilds: " error: unknown filesystem " (probably because it's NTFS)

I tried copying the 3 files found in (hd1,gpt1)/efi/ubuntu/ to (hd1,gpt5)/efi/ubuntu/ , but that didn't resolve anything.

After writing all of this down, it looks like I have to change the default grub "**root**" and "**prefix**" to hd1,gpt1 instead of hd1,gpt5 , but given the multiple grub config files locations, and the grub files that say don't edit by hand, I really don't know what to do.

Any help would be very much appreciated.

Oh! I almost forgot. Here is my output from boot-repair (I made a boot-repair bootable thrumbdrive, and tried it like that).
[http://paste.ubuntu.com/11779045/](http://paste.ubuntu.com/11779045/)

Thanks,

Rich

---

### Post by rcollins0618 on 2015-06-26
Great Scott!

I made a few backups of the windows bcd with both "bcdedit \export" and with EasyBCD. Feeling (potentially) artificially safe, I went ahead and ran " bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi " in windows 7.

Seemingly both problems are fixed simultaneously. 
Starting the computer loads GRUB.
AND
the GRUB menu loads.

Could anyone tell me what lined up for this to happen? If not, I'm alright with not knowing. Just wondering if anyone else out there happens upon this and is still lost or it doesn't work for them.

Thanks,

Rich

(oh, and i also ran a grub-mkimage before those other two grub commands. I don't even know the difference between them).

---

### Post by oldfred on 2015-06-26
I have yet to find a way to install Ubuntu in UEFI boot mode to a second drive and have it boot from that drive without manual copying of files. It always defaults to install to the ESP - efi system partition on sda. It only worked if I disconnect sda and only have sdb connected when installing.

The system boots from the ESP on sda and the ubuntu folder in the efi partition has the tiny grub.cfg that has a configfile entry to the grub.cfg inside your install.

Your neogrub error is from your Neosmart install. I do not recommend that with UEFI as it really is another menu & you have UEFI and grub as menus already. It may be useful as one of several Windows repair tools you should have.

Your efi is showing only two efi boot options, SSD & flash drive (memorex). And then BIOS boot options for hard drive, flash drive & CD/DVD. I would have thought it would have found the /EFI/Boot/bootx64 as a UEFI boot entry.

One of the main work arounds for systems that do not directly boot Ubuntu/grub is to copy grub into /EFI/Boot/ and rename it to bootx64.efi. Then boot an UEFI hard drive (or SSD) entry. You may have to manually create that UEFI entry with efibootmgr if not automatically added as BIOS entry will not work. Details on manually mounting partitions and copying files are in link in my signature. Even though using a grubx64.efi in /EFI/Boot it still finds (must be hard coded) the grub.cfg in /EFI/ubuntu. I have tried creating different folders for my different versions of Ubuntu with different configfiles for each install. But the only grub.cfg used has been the one in /EFI/ubuntu.

 sudo efibootmgr -c -L "EFI Hard drive" -l "\EFI\Boot\bootx64.efi"
sudo efibootmgr -v

 
       Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

