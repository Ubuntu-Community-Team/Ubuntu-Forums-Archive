---
title: "grub rescue"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by omniyo on 2012-10-28
Hello,

I'm desperate. I have windows 7 home premium installed on my notebook and I decided to install ubuntu as usual. Nevertheless, I had several problems with the graphic card while installing and I got some problems and I couldnt run ubuntu properly, so I decided to uninstall ubuntu by formatting the partition and joining it to my data partition (where it originally came from). Afterthat, I cannot enter into any OS. Not even from the BIOS. But the partitions are there. There is no way, I have tried a Windows DVD to repair boot, but no repair option is offered just installation, also I tried "lilo" as this post said:

[http://ubuntuforums.org/showthread.php?t=1359802](http://ubuntuforums.org/showthread.php?t=1359802)

I tried Super Grub Disk with no luck. Even Boot-Repair from a live-CD where I could just obtain a report:

[http://paste.ubuntu.com/1314101/](http://paste.ubuntu.com/1314101/)

What can i do? I just want to have my windows boot as usual and then i will try again the linux installation. But I need to come back to my windows boot.

I don't know what else can I do.

Thanks in advance, and sorry for my english (desperation -> master level).

EDIT: what i obtain when I boot is:

error: no such partition.
grub rescue> _

---

### Post by critin on 2012-10-28
>  Even Boot-Repair from a live-CD where I could just obtain a report:

It didn't let you run the repair option, only the report?  There is no MBR.  Did you explore boot repair, there used to be an option to repair MBR.  I haven't looked at it in a long while, so don't really know where to find the options.  Click on the radio boxes--explore it.

Deleting the partition deleted grub.  The Win dvd isn't offering to repair it either.  If it was me I'd just reinstall Windows  and read up on installing ubuntu before trying it again.  

Is this a new computer?  Which version of ubuntu?  12.10?

---

### Post by oldfred on 2012-10-28
You have a new UEFI system, so ignore any instructions on MBR, msdos partitions or installing grub to the MBR. With UEFI you install grub to the efi partition and use grub2's grub-efi not grub-pc (for BIOS systems). 

From the UEFI menu on your system can you not choose the Windows boot loader?

Typically this is the Windows efi boot files.
/EFI/Microsoft/Boot/bootmgfw.efi 
/EFI/Microsoft/Boot/bootmgr.efi

---

### Post by omniyo on 2012-10-29
Thanks for replying.
critin:
- Yes, I could only run the report not the repair option.
- It is a new computer (asus ux32vd) and the ubuntu version I deleted was 12.10. I don't want to reinstall Windows because i'll lost my license key. What is more, when I ran the windows DVD in order to fix the boot (didnt offer that repair option), it didn't let me choose installing windows on the same partition it already exists.

oldfred:
- I don't know how to access to the uefi menu. How? I haven't seen anything about it. The only options I currently know how to access is the BIOS and the grub prompt.
- Both options appear on the report that I attached from boot-repair. But no idea how to access/fix it.

An "ls" in the grub rescue prompt get this:
(hd0) (hd1) (hd1, gpt5) (hd1, gpt4) (hd1, gpt3) (hd1, gpt2) (hd1,gpt1) (hd2) (hd2,gpt2) (hd2,gpt1)

please help.

---

### Post by oldfred on 2012-10-29
New UEFI systems are a combined BIOS/UEFI. You should have specific UEFI menu settings. One user posted his "BIOS" screen and the UEFI entry was only one line but then that opened a lot of additional settings.

One user posted this on how he was able to change name in UEFI boot menu.

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


---

### Post by YannBuntu on 2012-10-30
hello

> **omniyo said:**
> Boot-Repair from a live-CD where I could just obtain a report:

[http://paste.ubuntu.com/1314101/](http://paste.ubuntu.com/1314101/)

- you have an UEFI Windows and an invisible Ubuntu partition (sdb1 probably). There is nothing Boot-Repair can fix in this situation, and that's why it doesn't show any "Recommended repair" button.
- I would recommend you try to fix your sdb partition table via TestDisk, then run Boot-Repair again.

---

### Post by oldfred on 2012-10-30
The protective MBR is incorrect even though the actual gpt is ok.


/dev/sdb1 ends after the last sector of /dev/sdb 

Not sure if fixparts works as it usually is to remove extraneous gpt data.

You may need to use gdisk and see it it will fix MBR, although it normally fixes gpt.

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by omniyo on 2012-10-30
I finally managed to install ubuntu again and once the grub was updated, I ran boot-repair. Then, a UEFI Windows option appeared and I could enter into windows. 

Below this option I have Windows Loader and Windows Recovery. 
The first give me: "error: invalid EFI file path", the second give me: "error: unknown commmand 'drivemap' error: "invalid EFI file path". 

Now, I ask about this not for the loader because I can boot windows from the uefi option but the recovery that I'd like to be able to run if necessary. How can I enable this link?

Can I do it in any option in the BIOS as you said?
(I attach some scrrenshots)

Thanks in advance

---

### Post by oldfred on 2012-10-30
Post a link to a  new copy of BootInfo from Boot-Repair.

Usually the efi boot entries that Boot-Repair adds for Windows work. Or two of the three work.

---

### Post by omniyo on 2012-10-30
[http://paste.ubuntu.com/1318928/]("http://paste.ubuntu.com/1318928/")

---

### Post by oldfred on 2012-10-30
You still have the error on sdb.

Is this an Intel SRT system? Perhaps that is why Windows is complaining as it cannot mount sdb because of error?

---

### Post by omniyo on 2012-10-31
Do you mean HDD + SDD with SRT? Yes.
SDD is for cache.

---

### Post by oldfred on 2012-10-31
That usually is some sort of Intel RAID and that just may be why the script cannot see it as it does not have the RAID drivers in a default Desktop install or LiveCD.

The grub2 boot stanzas are the old style BIOS/MBR type and do not work with UEFI. Boot-Repair adds a correct entry for Windows. 

From your UEFI menu can you get another efi entry to your recovery partition? Or how does Windows get to that when you do not have Ubuntu? Then we can create a correct chain load entry if we know which efi file it uses. If you have to boot or press f8 or other key then grub will not have a separate entry.

---

### Post by omniyo on 2012-10-31
My UEFI menu: is it the part of the BIOS that I attached in the pics previously?
When I didn't have Ubuntu I could get recovery by pressing F9 but now... it doesn't work.

I'm completely noob about this topics but i'll try to give some ideas:

None of the paths that I have in the boot-repair report has something to do?
 - /EFI/Microsoft/Boot/bootmgfw.efi
 - /EFI/Microsoft/Boot/bootmgr.efi 
 - /EFI/Microsoft/Boot/bootx64.efi

I think two of them are for windows loader and one should be for the recovery, aren't them?

What is more, in the report we have:

GUID Partition Table detected.
**/dev/sda5**     924,344,320   976,773,119    52,428,800 Windows Recovery Environment (Windows)

sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.

Is it useful?

Has the solution something to do with this page?:
[https://wiki.archlinux.org/index.php/GRUB2#Chainload_Microsoft_Windows_x86_64_UEFI-GPT](https://wiki.archlinux.org/index.php/GRUB2#Chainload_Microsoft_Windows_x86_64_UEFI-GPT)

concretely where it says "Multiboot in UEFI".

---

### Post by oldfred on 2012-10-31
By pressing f9 you are interrupting the the standard Windows boot and jumping to the recovery boot.

I know those with BIOS/MBR and wanting to use f8 to get to Windows repair reported that they had to hit the key just about at the same time as the enter on the grub menu for Windows. It seems to be quicker from grub to Windows than from MBR to Windows. It may be the same with UEFI? You might just try several times and try to be real quick.  

Not sure if there is any way like in Ubuntu to add kernel parameters to change from a standard boot to something else.

---

### Post by omniyo on 2012-10-31
No effect at pressing f8/f9 key after several repetitions

any idea yet?

---

### Post by oldfred on 2012-10-31
This is for Windows 8 and UEFI, does Windows 7 offer anything.
[http://pureinfotech.com/2012/05/24/access-windows-8-boot-options-menu-all-you-need-to-know/](http://pureinfotech.com/2012/05/24/access-windows-8-boot-options-menu-all-you-need-to-know/)

You might try Supergrub as it will boot anything that is bootable.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)


But why do you want to get to recovery partition. You should use it just once to make a set of recovery DVDs and throw them away. (just kidding), but you would only ever want to use them if you want to sell computer and buyer only wants Windows.

Then do a backup as that is a better way to recover.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by omniyo on 2012-11-01
I want to have access to start from the begining and install ubuntu UEFI way: 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And also just in case I have any warranty problem. Better to give them the PC with just windows installed.

---

