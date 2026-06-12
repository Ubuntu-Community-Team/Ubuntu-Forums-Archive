---
title: "Partition Madness"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by Iamcmac08 on 2013-12-25
Very new to Ubuntu and Linux in general.. I'm attempting to dual boot  Windows 8 and Ubuntu. I don't know a lot about partioning but I know  there are way too many partitions and I can't boot properly. I installed gparted  because I knew I'd have to make changes but I wasn't sure what. Also  installed boot-repair and ran a boot-info report. I would really appreciate any help, getting frustrated at this point.

Link to boot-info:
[https://www.dropbox.com/s/c0g3r3yg8zi08j3/Boot-Info_1.txt](https://www.dropbox.com/s/c0g3r3yg8zi08j3/Boot-Info_1.txt)

---

### Post by mikewhatever on 2013-12-25
Can you attach the boot-info.txt to the original post. DropBox gives me a file full of html code - probably wants a cookie or something.

---

### Post by Iamcmac08 on 2013-12-25
Try this link.. the file is too large to upload.

[http://paste.ubuntu.com/6635030/](http://paste.ubuntu.com/6635030/)

---

### Post by grahammechanical on 2013-12-25
It seems to me that this an example of Windows 8 partition madness. Ubuntu has created its standard two partitions -sda10, ext4 for Ubuntu 12.04.3 LTS and sda6, the swap partition.

How many installs of Windows 8 do you have in this machine?

This is relevant

> [COLOR=#666666]===================[/COLOR] blkid:
/dev/sda1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"WINRE_DRV"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"BCD60593D6054F58"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda2: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"SYSTEM_DRV"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"A005-DE7F"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR]
/dev/sda3: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"LRS_ESP"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"1435-D5CF"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR]
/dev/sda5: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Windows8_OS"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"8448075648074680"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda6: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"c87882db-0293-4c2a-8a31-eb63668e66da"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/sda7: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"94DCE6ACDCE687B6"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda8: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"LENOVO"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"DAB83FFAB83FD3AB"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda9: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"PBR_DRV"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"A64A3B8E4A3B5A6F"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda10: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"d726539a-5207-471f-8889-ef2217a258fb"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ext4"[/COLOR]
[COLOR=#BB4444]
[/COLOR]


/dev/sda10 and /dev/sda6 are the two Ubuntu parititons. The others, I guess, are related to Windows 8 and Lenvo in some way. I am also guessing that /dev/sda7 is possibly a NTFS partition that is intended for common data storage that is accessible to both Windows and Ubuntu [edit: I am wrong on that]. Perhaps it is not madness after all. As this shows

> Partition    Start Sector    End Sector  [COLOR=#008800]*# of Sectors System*[/COLOR]
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     4,630,527     2,048,000 -
/dev/sda4       4,630,528     4,892,671       262,144 Microsoft Reserved Partition [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda5       4,892,672   433,196,533   428,303,862 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]
/dev/sda6     888,991,744   897,101,823     8,110,080 Swap partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]
/dev/sda7     897,101,824   897,818,623       716,800 Windows Recovery Environment [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda8     897,818,624   950,247,423    52,428,800 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]
/dev/sda9     950,247,424   976,773,119    26,525,696 Windows Recovery Environment [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda10    433,197,056   888,991,743   455,794,688 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]

Now this is where is gets confusing (well it confuses me) compare these two statements

> /dev/sda5: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Windows8_OS"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"8448075648074680"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
>  [COLOR=#000000]/dev/sda5       4,892,672   433,196,533   428,303,862 Data partition [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]Windows/Linux[/COLOR][COLOR=#666666])[/COLOR]

So, what exactly is sda5 being used for? You also seem to have two partitions set aside for "Windows Recovery Environment (Windows)" - sda7 and sda9 . No. Make that 3 partitons there is also sda1 listed as "Windows Recovery Environment (Windows)" Is this a result of multiple re-installs of Windows?

---

### Post by Iamcmac08 on 2013-12-25
Yes that is correct. I system restored thinking it would solve my partition problem so I could "start over". The partitions were still existing but erased my Ubuntu installation. I then went through windows disk manager and shrank the windows partition and deleted the existing Ubuntu partition. I reinstalled Ubuntu and that's where I am now.

---

### Post by oldfred on 2013-12-25
Windows normally creates a lot of partitions. Windows recovery, vendor recovery, efi, reserved (some unformatted space for DRM, serial numbers etc), and the main install. Some vendors put additional efi files into another FAT partition not set as efi  for maintenance files, others have too many maintenance files in the main efi partition. And some vendors seem to split or have more than one vendor recovery.

It looks like you tried to install wubi. Wubi does not work with any gpt partitioned  system or all UEFI boot systems. It is being discontinued.

Very new systems work best with 13.10 or wait for 12.04.4. Intel offered many improvements that are in newest kernel, support files & video which are in 13.10 and later releases.

         Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some other Lenovo installs.

 Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

---

