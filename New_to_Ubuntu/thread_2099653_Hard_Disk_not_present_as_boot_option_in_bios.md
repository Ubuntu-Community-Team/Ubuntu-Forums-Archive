---
title: "Hard Disk not present as boot option in bios"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by StevenBlack on 2012-12-30
Please, I know this is a common error, but I`ve been working on it for 25hours, I`m desperate! I have an exam in 3 days and I need my computer! 
I tried installing Linux Mint and Ubuntu and everytime I finish i get the error reboot and select proper boot device. I`ve searched for every solution I could find but none seems to work. Just please bear with me! I have an Asus ATTVM, 64-bit Intel i7 processor. I had installed windows 8, had it for almost 2 weeks, than it just stopped booting and giving me the BSOD. Intel Rapid Storage technology could have something to do with it. tried recovering with windows 8 windows 7 and windows xp disk but they just tell me that the disks, partitions are blocked. Or that they`re GPT and not MBR. I installed Linux Mint, and everything went fine but when I restart it gives me that error. In bios I can-t see and add my hardrive as an option, just dvd and usb. I tried repairing the boot with boot-repair, and everything seemed to go right [http://paste2.org/p/2666886](http://paste2.org/p/2666886) but it still doesn-t work In bios it sais Windows boot manager (driver not present). I tried assigning the boot flag wit gparted but it doesn`t work. I`m not interested to going back to windows, Linux Mint seems perfect for me, but I can`t get it to boot and I haven`t slept in a long time.
I'm sure the hard disk is fine I can access it with a LiveCd and manage data and everything

If I were to format and install, how could i do so? what should i use, ntfs?

---

### Post by Horbo on 2012-12-30
For booting from devices that your BIOS doesn't want to let you use, Plop is the tool you need (not sure your problem is that simple though): [http://www.plop.at/](http://www.plop.at/)

BTW, try breaking up your text to make posts readable - some people get turned off by walls of text! :p

---

### Post by Wim Sturkenboom on 2012-12-30
If the BIOS does not see the drive, something is broken. Linux bypasses the BIOS info and hence can install. But the BIOS needs to see the drive to be able to boot from it.

Because you're under some pressure, I suggest to use a liveCD/liveUSB for now or to make a persistent install of a distro on a pen-drive; you should be able to access your internal disk from that.

Good luck with the exam

---

### Post by audiomick on 2012-12-30
> **Wim Sturkenboom said:**
> 
Because you're under some pressure, I suggest to use a liveCD/liveUSB for now or to make a persistent install of a distro on a pen-drive; you should be able to access your internal disk from that.

Good luck with the exam

I think this is good advice. Get a USB happening, and use that until after your exam.

When the pressure is off a bit, have a look at this for some info on the Intel Rapid Storage Technology.

[http://ubuntuforums.org/showpost.php?p=12410218&postcount=2]("http://ubuntuforums.org/showpost.php?p=12410218&postcount=2")

---

### Post by oldfred on 2012-12-31
You have gpt partitioning and Windows only boots from gpt with UEFI. But with UEFI the first partition must be the efi partition and it looks like you overwrote it to NTFS not FAT32? Change back to FAT32, it still shows as efi partition so it has correct gpt code or boot flag from gparted.

Then you install Ubuntu in BIOS mode. Ubuntu works with gpt partitioned drives in either UEFI or BIOS mode, but installs based on how you boot installer. Only the new 64 bit 12.10 works with new Windows 8 pre-installed with secure boot. Ubuntu 12.04 will work with UEFI if no secure boot,  but 12.10 does have more updates.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

You may be able to get Windows working again by creating efi partition and copying efi boot files into it.
       
 Windows UEFI install should  have backup of bootmgrw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

     You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

