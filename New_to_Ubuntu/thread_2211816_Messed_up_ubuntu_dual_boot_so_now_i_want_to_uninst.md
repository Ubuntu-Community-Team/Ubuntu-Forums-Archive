---
title: "Messed up ubuntu dual boot so now i want to uninstall it."
date: 2014-03-17
forum: New to Ubuntu
---

### Post by mona_de_mnaco on 2014-03-17
Hi there, i'm looking for a way to uninstall ubuntu 12.04 64-bit from my Toshiba Satellite C845-Sp4330KL, i have no experience using linux.

Initially my pc came with windows 8 but i installed windows 7 in it, and after a while i decided to try linux, but i messed up the installation (i'm sure i partitioned it correctly but i'm not sure if i installed it correctly because it never showed the "install alongside windows 7" page) and now it won't let me access windows 7. It doesn't even show a GRUB or anything like that, it just goes straight to ubuntu (i also installed KDE as an interface(?) ).

I'm done trying to save my GRUB and now i just want to uninstall ubuntu and reinstall windows 7 (i already have the w7 image) but i'm not sure if the tutorial for "uninstalling ubuntu dual boot" will work for me or not and i desperately need windows 7 for my college classes, so if anyone could tell me what i can do i'd really appreciate it (:

Thanks for your help~

---

### Post by slooksterpsv on 2014-03-17
Do you know if your system uses EFI? If so download my app from my ppa and see if you can rearrange the boot order to boot into Windows.

Easiest option - backup what data you need. Pop in the Windows 7 DVD, have it delete all partitions, install Windows 7.

The difficult answer:
What kind of Windows 7 image? If it's an ISO great! =D If not, how did you make the image.
If it's an ISO burn it to a DVD or rip it to USB Thumb drive (I don't remember how to do this, I think I had to dd it, google it).

If you want to boot back into Windows 7 without destroying anything first, you may want to run bootrepair and post the results here of what bootrepair says. 

Where did grub install to?

---

### Post by mona_de_mnaco on 2014-03-17
hi, thanks for the quick reply
i don't know if my system uses EFI and yes, i already put it in a thumb drive, so it's ready to go. But that's my main concern, if i pop it and delete all partitions and install windows 7, will it be as if i had never installed ubuntu or will it leave ghost files or something behind? At this point i just want windows 7, to be honest.

I've been reading about it and apparently it has something to do with my laptop having GPT partition style, does that change anything?

---

### Post by slooksterpsv on 2014-03-18
Yes, you can still get into your Windows 7 partition then - EFI and Windows 8 are synonymous.

EFI requires an EFI Partition on the drive and you probably have these as well - Windows, Recovery, Tools, and a special Drive windows makes + others.

GPT allows for more than 4 partitions - which is why GPT is amazing. MBR only allowed for 4 partitions.

So yes you are more than likely running EFI - which my app will get you back into Windows without data loss. Otherwise you can reformat and reinstall like nothing was ever on the drive (you'll get just the basic apps like notepad, calculatore, internet explorer, etc. nothing that came with the computer though)

---

### Post by mona_de_mnaco on 2014-03-18
ok, so i downloaded your app following the minitutorial, and then i restarted my computer and nothing visible changed, it still booted into ubuntu. Is that normal with your app? or am i not accesing it? 
thanks

---

### Post by fantab on 2014-03-18
Boot with Ubuntu DVD/USB and 'Try Ubuntu (without installing)'. From the desktop open Terminal [ctrl+alt+T], run the following command and post its output here:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by oldfred on 2014-03-18
Windows does not see nor like Linux partitions. but if you delete those it will install.

But if system was Windows 8, then it was UEFI with gpt partitioning. Windows will only install to gpt partitioned drive in UEFI mode. So the Windows 7 DVD will not install in UEFI mode. But we have seen may with Windows 7 in BIOS mode and it converts drive (incorrectly) to MBR(msdos). It leave backup gpt partition table. With only Windows that does not seem to matter, but Linux then sees both MBR & gpt and will not install.

How you boot install media is how it installs, so to install in BIOS mode you must boot in BIOS, or to install in UEFI you must boot in UEFI mode.

 You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

   Convert Windows BIOS to UEFI - Also command line install of files to efi partition
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

   Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by mona_de_mnaco on 2014-03-18
hi fantab, here's the output. thanks (:

```

[COLOR=#444444][FONT=Calibri]ubuntu@ubuntu:~$ sudo parted -l[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Model: ATA TOSHIBA MK5075GS (scsi)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk /dev/sda: 500GB[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Partition Table: gpt[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Number  Start   End     Size    File system     Name  Flags[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri] 1      1049kB  50,0GB  50,0GB  ext4[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri] 2      50,0GB  100GB   50,0GB  ext4[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri] 3      100GB   150GB   50,0GB  linux-swap(v1)[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]Model: Philips USB Flash Drive (scsi)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk /dev/sdb: 4010MB[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Partition Table: msdos[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Number  Start   End     Size    Type     File system  Flags[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri] 1      65,5kB  4010MB  4010MB  primary  fat32        boot, lba[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]Disk /dev/sda: 500.1 GB, 500107862016 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk identifier: 0xfafe7ef6[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda1               1   976773167   488386583+  ee  GPT[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Disk /dev/sdb: 4009 MB, 4009754624 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk identifier: 0x00000000[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sdb1   *         128     7831551     3915712    c  W95 FAT32 (LBA)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ubuntu@ubuntu:~$ 
[/FONT][/COLOR]
```[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]

---

### Post by slooksterpsv on 2014-03-18
Sorry I've been away from the comp, if you run the app (it will be located under system or you can open a terminal and type in efibootorder) you can have it pull your EFI data from NVRAM, and then you can see what your current boot order is, you can move it up and down to change what boots first if it shows anything.

---

### Post by fantab on 2014-03-18
```
[COLOR=#444444][FONT=Calibri]$ sudo parted -l[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Model: ATA TOSHIBA MK5075GS (scsi)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk /dev/sda: 500GB[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Partition Table: gpt[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Number  Start   End     Size    File system     Name  Flags[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri] 1      1049kB  50,0GB  50,0GB  ext4[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri] 2      50,0GB  100GB   50,0GB  ext4[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri] 3      100GB   150GB   50,0GB  linux-swap(v1)[/FONT][/COLOR]
```

The output does not show any Windows/NTFS Partitions, looks like you have **erased Windows** installation from the HDD.
Neither is there any ESP (EFI System Partition), when the partition table is GPT. Either there has to be an ESP on UEFI boot or there should be a 10-20MiB partition with 'bios_grub' flag 
if you want to boot Linux in Legacy/CSM/MBR mode. Windows WILL NOT boot from GPT Disk without ESP.

---

### Post by mona_de_mnaco on 2014-03-20
Thanks to everyone for their input. I finally decided not to lose any more time and i plugged in my usb with the image of Windows 7, as i was installing it, it sent an alarm that it couldn't install itself because of the GPT so i formatted the disk using windows console (the same way one preps a usb before putting the windows image on it) and everything went smoothly after that. 

I plan on giving ubuntu another try but later, see you then
Thanks from Chile c:

---

### Post by fantab on 2014-03-21
If you are re-installing Win7 then follow this tutorial to install it in UEFI:
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

---

