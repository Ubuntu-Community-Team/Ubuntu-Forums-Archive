---
title: "What is Error 17?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Wudugast on 2008-10-25
I just installed something in Windows Vista from the Ubuntu Live CD that said it would help with booting from CD after a restart. I want to use the Ubuntu Live CD to install the program again.

I used to dual boot Ubuntu and Windows from two different HDs, but I had to format my Ubuntu drive and only have Windows now.

After I installed the part of the live CD that said it would help with installing after a reboot, I can't get past the grub loading stage of the computer booting up. It says GRUB Error 17, and I can't even get to windows.

I have tried messing around with the boot priorities in my BIOS but with no luck. How do I fix this?

I have tried loading to the BIOS and putting the live CD in there, and I have tried booting with it in from the very beginning, and I have tried booting without it. I get the same error every time.

---

### Post by Yashiro on 2008-10-25
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

or

[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by eolson on 2008-10-25
Everybody who fiddles with their system needs a copy of Supergrub.  Makes life a whole lot simpler.

---

### Post by Wudugast on 2008-10-25
I just saw the Supergrub thing. I'll check it out before I go further.


About the Windows Recovery Mode: That doesn't work. 

It acts like it's trying to load windows, then gives me a blue screen that says:

"A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps:

Check to be sure you have adequate disk space. If a driver is identified in the Stop message, disable the driver or check with the manufacturer for driver updates. Try changing video adapters.

Check with your hardware vendor for any BIOS updates. Disable BIOS memory options such as caching or shadowing. If you need to use Safe Mode to remove or disable components, restart your computer, press f8 to select Advance Startup Options, and then select safe mode.

Technical information: STOP: 0x0000007E (0xFFFFFFFFC0000005, 0xFFFFF8000985E251, 0xFFFFF98000A05B98, 0xFFFFF98000A05570) "

Now, I can't do any of these things because I can't get into Safe Mode or Recovery Mode to actually do them.

Isn't this a problem with the Ubuntu Live CD anyhow? I installed software from it that was supposed to make my computer boot from CD, but it did this to my computer.

---

### Post by Duck2006 on 2008-10-25
Taken from the grub manual,

> 
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by Yashiro on 2008-10-25
I don't see how it can blue screen and complain about drivers if you are booting from the CD correctly.
> 
6.	In the System Recovery Options dialog box, click Command Prompt.
7.	Type Bootrec.exe, and then press ENTER.

**Note To start the computer from the Windows Vista DVD, the computer must be configured to start from the DVD drive.** For more information about how to configure the computer to start from the DVD drive, see the documentation that is included with the computer or contact the computer manufacturer.

Bootrec.exe options
The Bootrec.exe tool supports the following options. Use the option that is appropriate for your situation.

Note If rebuilding the BCD does not resolve the startup issue, you can export and delete the BCD, and then run this option again. By doing this, you make sure that the BCD is completely rebuilt. To do this, type the following commands at the Windows RE command prompt:
&#8226;	bcdedit /export C:\BCD_Backup
&#8226;	c:
&#8226;	cd boot
&#8226;	attrib bcd -s -h -r
&#8226;	ren c:\boot\bcd bcd.old
&#8226;	bootrec /RebuildBcd

**/FixMbr**
The /FixMbr option writes a Windows Vista-compatible MBR to the system partition. This option does not overwrite the existing partition table. Use this option when you must resolve MBR corruption issues, or when you have to remove non-standard code from the MBR.

**/FixBoot**
The /FixBoot option writes a new boot sector to the system partition by using a boot sector that is compatible with Windows Vista. Use this option if one of the following conditions is true:
&#8226;	The boot sector has been replaced with a non-standard Windows Vista boot sector.
&#8226;	The boot sector is damaged.
&#8226;	An earlier Windows operating system has been installed after Windows Vista was installed. In this scenario, the computer starts by using Windows NT Loader (NTLDR) instead of Windows Boot Manager (Bootmgr.exe).
/ScanOs
The /ScanOs option scans all disks for installations that are compatible with Windows Vista. Additionally, this option displays the entries that are currently not in the BCD store. Use this option when there are Windows Vista installations that the Boot Manager menu does not list.
/RebuildBcd
The /RebuildBcd option scans all disks for installations that are compatible with Windows Vista. Additionally, this option lets you select the installations that you want to add to the BCD store. Use this option when you must completely rebuild the BCD.

---

### Post by caljohnsmith on 2008-10-25
From your Live CD, open a terminal (applications > accessories > terminal) and please post the output of:
```
sudo fdisk -lu
```
So we can get a better idea of your HDD setup.

---

### Post by Wudugast on 2008-10-26
I couldn't even get to the computer recovery screen. It BSODed before it could get there.

Anyhow, I went to Circuit City a few hours ago, bought an HD cradle, retrieved my files using my fiancee's laptop, and formatted my two HDs.

That seems to have fixed the problem. I needed to get rid of the grub. Now that it's gone, it can't give me errors!

Anyhow, I'm reinstalling Windows Vista and then I'll do Ubuntu.

Thanks, everyone!

:)

---

