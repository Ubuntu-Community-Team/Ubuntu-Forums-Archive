---
title: "brown blank box surrounded by black after install"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by fhedman on 2013-01-17
Hello have been trying to install Ubuntu 12.10 x86 desktop on my older laptop. I have tried installing from DVD and from flash drive,same thing happens from either,install is fine everything works after initial reboot,remove disk or flash drive then I get a small orange box nothing else. I have reinstalled 4 times now 2 each on cd then flash drive same thing happens. At the brown screen I get nothing its just a small brownish box surrounded by a black screen,ctrl+alt+f1,f2,etc.. does nothing. After bios splash screen I hit the shift key and see loading grub for a split second then it goes to same screen.One thing to note when it first loads I hear a sound like you get when you disconnect a flash drive in windows.The live cd or flash drive runs fine no problems. Any help would be much appreciated thanks .

Laptop had xp home but I wiped it during installation,no devices connected except a pcimca wifi card,tried removing that but it changes nothing

Computer specs:
Processors Intel Celeron4 Processor running at 2.0GHz
Chipset Intel 845GL 
Memory Standard: 512MB PC2100 DDR SDRAM
Display 14.1" XGA TFT with 1024 x 768 at 16.7 million colours (32-bit colour depth)
15" XGA TFT with 1024 x 768 at 16.7 million colours (32-bit colour depth)
Maximum External Resolution (CRT)1400 x 1050 (SXGA+) at 60Hz
Video Video type –Direct AGP integrated graphics
Video memory –up to 32MB (with 128MB of system memory) or 64MB (with 256MB or more system memory)
Audio Audio type –SoundBlaster
emulation AC97
Audio controller –Sigmatel 9750, two integrated stereo speakers
Hard Disk Drives 30GB EIDE/ATA-100 hard drives or high-speed 40GB 5400 RPM EIDE/ATA-100 hard drive
PC Card Slot One Type I or one Type II; CardBus support
Batteries. 12-cell 94Whr SMART Lithium-ion
Keyboard. 86-key Europe; key travel: 3mm; key spacing: 19mm
Pointing Device Integrated touch pad
Power Supply.90 watts AC adapter

---

### Post by ibjsb4 on 2013-01-17
Have you tried nomodeset?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by fhedman on 2013-01-17
Hey thanks do I have to reinstall again with that option?

---

### Post by audiomick on 2013-01-17
No. You just have to edit the grub menu.

---

### Post by ibjsb4 on 2013-01-17
> **fhedman said:**
> Hey thanks do I have to reinstall again with that option?

No, reinstall not necessary.  In the above link go to:

[SIZE=2]"How to temporarily set kernel boot options on an installed OS (not wubi)[/SIZE]"

This will allow you to try it before you make it permanent.

Read that, if this does not make sense to you please post back with any questions.

---

### Post by fhedman on 2013-01-17
Hey thanks again guys I tried to boot off the flash drive with the nomodeset enable and it wouldnt boot,so I set the nomodeset in grub by adding the line at the end of the linux /boot and got the same brown box with black screen,so I tried installing linux mint 14 cinnamon same thing happens why does it run perfect from live cd? maybe this computer just cant run linux its a dell inspiron 1100

---

### Post by sandyd on 2013-01-17
> **fhedman said:**
> Hello have been trying to install Ubuntu 12.10 x86 desktop on my older laptop. I have tried installing from DVD and from flash drive,same thing happens from either,install is fine everything works after initial reboot,remove disk or flash drive then I get a small orange box nothing else. I have reinstalled 4 times now 2 each on cd then flash drive same thing happens. At the brown screen I get nothing its just a small brownish box surrounded by a black screen,ctrl+alt+f1,f2,etc.. does nothing. After bios splash screen I hit the shift key and see loading grub for a split second then it goes to same screen.One thing to note when it first loads I hear a sound like you get when you disconnect a flash drive in windows.The live cd or flash drive runs fine no problems. Any help would be much appreciated thanks .

Laptop had xp home but I wiped it during installation,no devices connected except a pcimca wifi card,tried removing that but it changes nothing

Computer specs:
Processors Intel Celeron4 Processor running at 2.0GHz
Chipset Intel 845GL 
**Memory Standard: 512MB PC2100 DDR SDRAM**
Display 14.1" XGA TFT with 1024 x 768 at 16.7 million colours (32-bit colour depth)
15" XGA TFT with 1024 x 768 at 16.7 million colours (32-bit colour depth)
Maximum External Resolution (CRT)1400 x 1050 (SXGA+) at 60Hz
Video Video type –Direct AGP integrated graphics
Video memory –up to 32MB (with 128MB of system memory) or 64MB (with 256MB or more system memory)
Audio Audio type –SoundBlaster
emulation AC97
Audio controller –Sigmatel 9750, two integrated stereo speakers
Hard Disk Drives 30GB EIDE/ATA-100 hard drives or high-speed 40GB 5400 RPM EIDE/ATA-100 hard drive
PC Card Slot One Type I or one Type II; CardBus support
Batteries. 12-cell 94Whr SMART Lithium-ion
Keyboard. 86-key Europe; key travel: 3mm; key spacing: 19mm
Pointing Device Integrated touch pad
Power Supply.90 watts AC adapter
I believe that you do not have enough memory to run the default Ubuntu setup.

I advise you try something lighter like LXDE, OpenBox, Puppy, .etc .etc

---

### Post by ibjsb4 on 2013-01-17
Xubuntu 12.04 is also a good choice.

[http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/)

[http://www.dedoimedo.com/computers/xubuntu-pangolin.html](http://www.dedoimedo.com/computers/xubuntu-pangolin.html)

---

### Post by fhedman on 2013-02-13
Finally got this fixed. I installed Lubuntu and had the same problem added  i915.modeset=0 did not help,so I reinstalled xp,upgraded bios in the dell and set the video memory to 8mb still did not help,it just would not load,ttys worked fine no desktop.I tried with i915modeset=1 no help.tried adding an xorg.conf file from another post that a guy did for 12.04 did not work.Finally got it with this I found on another forum i915.blacklist=1. It has worked fine now for a week. Thanks a million for all the help guys.

---

