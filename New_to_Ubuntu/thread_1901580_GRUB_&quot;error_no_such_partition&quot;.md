---
title: "GRUB &quot;error: no such partition&quot;"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by jonahhill on 2011-12-28
So I installed Ubuntu a while ago alongside Windows in a dual boot but didn't like it so I never used it. I needed space because my computer was filling up and there were 160GB of free space on the Linux boot. So I used a Windows Partition program to delete 2 partitions Linux had and clear them and it took like 2 hours. But now when I boot my computer I just get that.

I searched for the problem and lots of people fixed it but they were trying to use Linux: I'm trying to get rid of Linux and start using Windows again. Does anyone know how to do this? I obviously did something wrong but I have no idea what or how to fix it. When I googled the error all I got was Linux pages so that's why I'm posting it here. :P:(:confused:

Also my CD drive doesn't work at all. But I have 2 USB drives and a 1TB hard drive I can connect to it in case I have to download something. I just want Windows back because all my data is there but I emptied everything that was on Linux already..

---

### Post by jonahhill on 2011-12-28
OK so I downloaded the Windows 7 recovery disc from a torrent and have a USB but how do I make it bootable? :/

---

### Post by jonahhill on 2011-12-28
Update: found a program that's supposed to make it bootable, but when I try to boot from the USB I get:

"NTLDR is missing"

??? crap what have i done

---

### Post by wildmanne39 on 2011-12-28
Hi, please give people time to come online that know how to help you.

There are some very good with this problem and I am sure as soon as one of them sees your thread they will reply.
Thanks

---

### Post by ACupOfCoffee on 2011-12-28
Okay, what you did was delete your boot partition. Boot to an Ubuntu CD and extend your NTFS partition to cover the space taken up by the partitions you just deleted. Shut down and reboot to your Windows DVD. Select the option to repair your computer. Cancel the automated fix and run a command prompt. Run the following two commands
```
bootrec /fixmbr
bootrec /fixboot
```You should be good to go.

---

### Post by jonahhill on 2011-12-28
> **ACupOfCoffee said:**
> Okay, what you did was delete your boot partition. Boot to an Ubuntu CD and extend your NTFS partition to cover the space taken up by the partitions you just deleted. Shut down and reboot to your Windows DVD. Select the option to repair your computer. Cancel the automated fix and run a command prompt. Run the following two commands
```
bootrec /fixmbr
bootrec /fixboot
```You should be good to go.

Thank you so much. I tried downloading GParted [http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/) here and tried to boot from USB using PowerISO to burn it (this worked earlier) but I get

[B]GRUB "error: no such partition"

[/B]again**. **Do you know how to get past that? Booting from USB worked when I had the Windows Repair ISO earlier and copied it in the same exact manner.

I tried formatting the USB stick to FAT, FAT32 and NTFS but exFAT didn't work that's the only one I haven't tried. I tried Tuxboot too.

---

### Post by oldfred on 2011-12-29
You have deleted the partition with the grub2 files. Grub in the MBR just jumps to the grub files & the menu to show you what you can boot. 

The Windows boot loader in the MBR just jumps to the Windows NTFS partition - PBR (active partition or boot flag) and uses the code in the PBR to boot. It has either bootmgr for Vista or 7 or ntldr for XP. So bootmgr missing is a incorrect NTFS partition boot sector.

But you can easily add a Windows work alike boot loader to the MBR from an Ubuntu liveCD. Then you can create repairCD and USBs and/or replace the work alike with a Windows boot loader. The lilo boot loader does not have to be replaced with Windows if you do not want to, but make a Windows repair CD.

Restore basic windows boot loader - universe enabled
newest versions of Ubuntu may not have synaptic, not sure if you can direclty install from Software Center or have to install synaptic first.
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by jonahhill on 2011-12-29
Thank you so much, oldfred!

I got it to work, and it's pretty much what you said. I followed the instructions here:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

So basically, if you have this problem, download PowerISO, format a USB drive, click Create Bootable USB drive, select the Windows Recovery Disc to it (you can download it online), boot from USB, click command prompt, and do what it says there.

For me, bootsect wasn't there, so I typed in "Bootrec.exe /FixBoot" and then "Bootrec.exe /FixMbr". Then I restart my computer and it worked.

Thanks again everyone!

---

