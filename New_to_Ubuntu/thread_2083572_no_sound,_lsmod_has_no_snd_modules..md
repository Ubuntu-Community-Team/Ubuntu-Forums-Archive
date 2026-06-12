---
title: "no sound, lsmod has no snd modules."
date: 2012-11-13
forum: New to Ubuntu
---

### Post by garrooo on 2012-11-13
I'm a new Lubuntu. I'm not sure if this is normal... Any comments to assist would be greatly appreciated.

No sound card is detected in my fresh installation of Lubuntu 12.10 (32-bit alternate disk image). (I've also tried Lubuntu 12.04, 32-bit alternate disk image, also without luck. This is my first Linux installation on a system and I am excited to try this out. Previously Knoppix 4.0.2 was able to use my sound card. So it seems unusual for a more modern version of linux to not support sound.)

Speakers are NOT muted.

-------

code:
aplay -l

response:
no soundcards found...

-------

code:
lspci

response:
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:00.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax Modem (rev 08)
01:01.0 Multimedia audio controller: Aureal Semiconductor Vortex 2 (rev fa)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I have 2 sound cards, 00:1f.5 is a built-in Intel audio controller, and 01:01.0 is a PCI sound card from Aureal.
At this time, I'm not picky about which one to use, as long as any one of them works.

Both sound cards should be supported by alsa according to
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)
[http://www.alsa-project.org/main/index.php/Matrix:Module-au8830](http://www.alsa-project.org/main/index.php/Matrix:Module-au8830)

-----

After reading various forums, I've acquired packages for puavcontrol and pulseaudio. Even pulseaudio does not detect any hardware input sound sources.

-----

code:
amixer
response:
amixer: No such file or directory

-----

code:
sudo modprobe soundcore
response:
FATAL: Could not load /lib/modules/3.2.23-std281-i586/modules.dep: No such file or directory


The kernel version returned by "uname -r" is 3.2.23-std281-i586.
I don't have a /lib/modules/3.2.23-std281-i586 directory.
But I do have /lib/modules/3.5.0-17-generic

code:
cd /lib/modules/3.5.0-17-generic/kernel/sound
modinfo soundcore.ko

response:
filename:       soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     D85A7B72DAA26F9E01F3856
depends:        
intree:         Y
vermagic:       3.5.0-17-generic SMP mod_unload modversions 686 
parm:           preclaim_oss:int

--------
Following another thread, I've tried enabling sound from User profile settings at:
Menu -> System Tools -> Users and Groups -> Advanced Settings -> Allow sound (checkbox), Allow video (checkbox)

--------

I'm not sure if there should be some sound module that should be enabled to allow sound to work.

code:
lsmod

response:
Module                  Size  Used by
raid10                 28750  0 
raid456                53398  0 
async_raid6_recov      12375  1 raid456
async_pq               12436  2 raid456,async_raid6_recov
raid6_pq               86658  2 async_raid6_recov,async_pq
async_xor              12391  3 raid456,async_raid6_recov,async_pq
xor                    20585  1 async_xor
async_memcpy           12364  2 raid456,async_raid6_recov
async_tx               12510  5 raid456,async_raid6_recov,async_pq,async_xor,async_memcpy
raid1                  28785  0 
raid0                  16462  0 
multipath              12366  0 
linear                 12366  0 
8139cp                 20597  0 
8139too                24693  0 
mii                    12598  2 8139cp,8139too

-----

Lastly, after trying all the above attempts, i have a dummy software output from PulseAudio, and no real sound.

code:
aplay -L

response
default
    Playback/recording through the PulseAudio sound server

-----

Has anyone else encountered this issue from a fresh installation of Lubuntu?

Thanks,
Gary

---

### Post by Rex Bouwense on 2012-11-13
It sounds like you have tried everything and have done your home work.  Here is one site that I have found generally works:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
You may have already been through many of the steps.

---

### Post by garrooo on 2012-11-13
The suggested sound troubleshooting page does not have a section for Lubuntu 12.10. So I'm beginning with Step 1 for Ubuntu 12.04.

I think I'm getting a bit closer to the problem....

------

Step 1 failed on the line:
sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2;

response:
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-image-3.2.23-std281-i586
E: Couldn't find any package by regex 'linux-image-3.2.23-std281-i586'

-------

According to wikipedia, Lubuntu 12.10 uses Linux kernel 3.5.5.
I have Windows ME on my primary IDE master drive (/dev/sda1) and installed Lubuntu on a primary IDE slave drive (/dev/sdb1). I was hesitant to install GRUB onto the master drive. (Attempts to install GRUB to /dev/fd0 failed horribly)

As a result, I've been booting into Lubuntu using a SysRescue Linux CD ([http://www.sysresccd.org/](http://www.sysresccd.org/)) that redirects to the Lubuntu configuration on my hard drive.

Unfortunately, SysRescue CD uses Linux kernel 3.2... 
I wonder if that is the reason why none of my USB devices are working....

-----

Rex, thanks for your reply.
I think my next step should be to reinstall GRUB properly, then reboot.

I hope this works....

Gary

---

### Post by garrooo on 2012-11-13
Solved :)

I have properly installed GRUB on my primary master hard disk.
By using GRUB to boot into Lubuntu (instead of SysRescue CD), the proper kernel (3.5.0.18-generic) is launched.

Now, snd_* and many more modules are listed when I execute 'lsmod'.

Sound is working now :)
This also fixed other problems that I had with a Wacom tablet not being detected.

Thanks Rex, to a newbie, it is very encouraging to know that there are helpers out there to assist and listen to various attempts.

Gary

---

### Post by Rex Bouwense on 2012-11-14
Glad to be of assistance Gary.  There are hundreds of people out there that jumped right into Linux (like me) and want to spread the word by helping others.  While we don't always have the complete answer, we can sometimes point you in the right direction.  Stick around and help someone.  It is heart warming.  Enjoy.:popcorn:

---

