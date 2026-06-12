---
title: "Install problems 12.10 (UEFI?)"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by mkilvert on 2013-04-08
I am getting totally frustrated with this installing of Ubuntu 12.10 !!

I have brought a new desktop (details below) with No Operating system with the intention of putting on Ubuntu 12.10 after getting fed up and bored with Windows.

Now, it will just not install at all, I have done some (well, a lot) of reading and it turns out the computer (i think) has UEFI bios, so this complicates things?! Nowhere in the bios can I find anything to switch off secure booting.

 I have tried installing from a DVD and a USB with no luck. I

f I boot from USB I get the Ubuntu logo on a purple background but does not proceed, if I boot from UEFI DVD drive I get the 4 options screen but if I select "try unbuntu" or "install Ubuntu" either way it just stops at the red/orange screen and does not proceed any further.

Any ideas? If there is a Linux/Ubuntu guru in Shropshire by any chance?

I have also tried to install 12.04 LTS with no luck either!!


New Desktop is;
Processor
[LIST]
[*]AMD A4-3300 2.5Ghz Dual Core APU
[*]Cache: 1MB
[/LIST]
Memory
[LIST]
[*]4GB DDR3 1333Mhz RAM
[*]Supports up to 16GB
[*]2 x DIMM sockets (1free)
[/LIST]
Hard Drive
[LIST]
[*]320GB SATA 2.5” HDD
[/LIST]
Chipset
[LIST]
[*]AMD A55
[/LIST]
Graphics
[LIST]
[*]AMD Radeon HD 6410D Graphics,
[/LIST]

---

### Post by tripp98 on 2013-04-08
Havent tried it myself but here is the link to follow.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mkilvert on 2013-04-09
Hi thanks, already seen this and I get stuck at point 2!!! I can not find a fastboot option in bios!!

---

### Post by ppjdee on 2013-04-09
You could see what mobo you have, and try a google search about it.

---

### Post by grahammechanical on 2013-04-09
Here is something that you could try:

1) Put the DVD/USB in and boot into it. At the first purple screen (with the keyboard & man icon) press Enter
2) At the next screen Press Enter to select English as the default install language.
3) At the TRY - INSTALL Screen Press F6
4) From the drop down menu select nomodeset and Press Enter and then Esc.
5) Now you should be back at the TRY - INSTALL screen with Try Ubuntu highlighted. Press Enter to load the live session.

See if that works. You may need to try some of those other F6 options, even a combination of them. Can someone purchase your motherboard with Windows 8 pre-installed. It is machines with Windows 8 pre-installed that have motherboards with UEFI, Secure Boot and Fast boot. If your motherboard is not certified for Windows 8 then it may not be a UEFI, Secure boot, and all that stuff motherboard.

Regards.

---

### Post by oldfred on 2013-04-09
I never have had consistent or good explanation of fast boot. It seems to be more a Windows setting, but may be in UEFI or seem to be. It is so the UEFI is by-passed on booting to make Windows load quicker. 
My BIOS takes 10 to 12 seconds to load. I think with fastboot UEFI then does not re-verify hardware on boot, and if Windows does not boot, makes it difficult or impossible on some systems to get into UEFI to repair system. 

With Ubuntu live USB flash you should have two boot options from UEFI menu. One will be UEFI and the other something else labeled BIOS/Legacy/CSM.

If drive is blank you can install in either UEFI or BIOS mode. But Windows will only boot from gpt partitioned drives with UEFI.
Ubuntu will boot from gpt partition drives in either UEFI or BIOS mode if you have correct partitions for it.
I would suggest gpt partitioning and your choice on BIOS which is well known or UEFI as it is the future, but not many know it.
But either way I would leave space or have the efi partition first. It is not large, and would not be used with BIOS, but would let you convert to UEFI. The efi partition should be first partition on drive and it would be difficult to add later if you install now in BIOS but want UEFI later.

If you did not have Windows 8 pre-installed you may not have secure boot setting in UEFI. I expect all systems may have it in the future. But you will have UEFI as default or BIOS as default. Some early UEFI implementations just looked for efi partition and if not found booted in BIOS mode.

---

### Post by mkilvert on 2013-04-10
Thank you for your replies, I am working 12 hour shifts at moment so won't have chance to try them until Friday so will let you know what happens then!!!

---

### Post by mkilvert on 2013-04-12
Grahammechanical - following your great advice and selecting NOMODESET I am now installing Ubuntu 12.10!!!!!

Just doing a reboot and it seems to have "locked up" on a black screen saying "The system is going down for a reboot NOW! modem-manager[1589]: <info> Caught signal 15, shutting down..."

but has been on this screen for some 10 mins or more now!!!!

Manually switched computer off and restarted, now locked up at a black screen (but sometimes purple blank screen)

Any more ideas?

---

### Post by oldfred on 2013-04-12
Often a video setting or maybe other boot parameters. I have nVidia and have to use nomodeset, which I think now works for many systems. And you may need some settings in UEFI/BIOS as defaults are not always best.

 Some other settings:
[URL="http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/"]http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/
[/URL]        

[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]
     How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

---

### Post by mkilvert on 2013-04-13
Well someone pm-ed me and suggested I tried 13.04 which has worked (first time)!!!!  Thanks for all your replies and suggestions. I still have no idea why 12.10 wouldn't work though.

---

### Post by oldfred on 2013-04-13
UEFI boot and kernel support for new hardware is changing quickly. So with new hardware, newer versions may work better.

---

