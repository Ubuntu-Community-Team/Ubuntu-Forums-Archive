---
title: "Another Grub 2.0 doesn't detect Windows 8.1 (with Ubuntu PAstebin Readout)"
date: 2015-11-11
forum: New to Ubuntu
---

### Post by PMackie1 on 2015-11-11
Hello Everyone,

I've struggled to get Grub installed to manage my dual boot, but now my windows isn't showing up. I've tried booting thru all different OS's via BIOS. Still nothing.

Tried to add Manual entries in Grub. Nada! Via this guide: 
[http://askubuntu.com/questions/485278/windows-8-1-not-appearing-in-grub2-after-installing-ubuntu-14-04](http://askubuntu.com/questions/485278/windows-8-1-not-appearing-in-grub2-after-installing-ubuntu-14-04)




Tried boot repair and it will give you a readbout of what's here but I'm at a loss. [URL="http://paste.ubuntu.com/13232637/"]UBUNTU PASTEBIN

[/URL]Believe me, I googled and terminaled until i didn't know what to do anymore. I hate to ask for help, but HELP!

Thanks in advance!

[URL="http://paste.ubuntu.com/13232637/"]
[/URL]

---

### Post by oldfred on 2015-11-11
UEFI & BIOS boot are not compatible. 
You can only change boot modes from UEFI/BIOS and may have to turn on/off UEFI or CSM/BIOS/Legacy boot mode.
Or once you start booting you can only from grub boot installs in same boot mode as grub/Ubuntu is installed.

Windows on sda is MBR(msdos) partitioned and only can boot in BIOS mode. You have a Windows BIOS boot loader in sda, so from UEFI you should be able to choose that in BIOS mode.

You have Ubuntu on sdb, gpt partitioned and booting in UEFI mode.
Your UEFI does show a Windows entry, Did you have Windows in UEFI mode before?

Windows only boots in UEFI from a gpt partitioned drive. Or UEFI always must be gpt for Windows.
Windows only boot in BIOS mode from MBR partitioned drives.

For both Windows & Ubuntu how you boot installer, is then how it installs. And general better but not required to have all systems in same boot mode. If not same you just need to use UEFI as boot manager. Some may let you use one time boot key like f10 or f12 to choose which system to boot.

---

### Post by PMackie1 on 2015-11-11
Ok basically, it's all BIOS or all UEFI?

If I follow you though I can create a UEFI partition on my windows SD using Gparted?

I cannot really answer your question in regards to the Windows in UEFI because I truly don't know. I didn't really take notes as I slapped this frankenstein together.

 I will say this experience has been nice for me learning terminal though :)

---

### Post by oldfred on 2015-11-12
You do not have to be all one or other, but then have to use UEFI as boot manager.
Once started booting in one mode you cannot change.

And how you boot install media is how it installs.
 
But Windows will only boot in UEFI mode from a gpt partitioned drive. And not sure you can even convert Windows. There are tools to convert a drive from MBR to gpt, but then not sure if you can reinstall the Windows boot loader and have it work.

Ubuntu if on gpt partitioned drive can be converted back and forth from UEFI to BIOS if correct partitions are on drive. Ubuntu needs the ESP - efi system partition for UEFI boot. For BIOS on gpt,  Ubuntu needs a tiny 1 or 2MB unformatted partition with the bios_grub flag.

Several years ago with my old BIOS system, I started converting new or totally reformatted drives to gpt and included the ESP even if not then used. My XP was still on a MBR partitioned drive, until I retired XP as not used anymore. But it took me several years before that one application I use in Windows was either good enough in Ubuntu or I realized I did not need all its features.

---

