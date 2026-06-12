---
title: "Unable to Boot 12.04 from USB"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by TheDailyToker on 2013-04-09
Hello everybody,

I apologize if I am posting this in the wrong area - I am brand new to Ubuntu, Linux and this forum.

I have been booting from a USB onto a Dell laptop without any issues - it seems to be rock solid and I have successfully booted into it many times. The problem occurs when I try to boot from USB on my Dell XPS. I am able to get as far as the main menu, where it asks you whether you'd like to boot or install from USB. When I attempt to boot from usb, I get a black screen for about 10 seconds, and then my PC starts its regular boot cycle all over. I don't even have an opportunity to do anything.

The only thing I could find that might be causing the issue is the the fact that the XPS has dual ATI Radeon HD 4800's. What really confuses me is that I was able to boot Ubuntu 12.10 from a USB on this PC before and battled the wacky video behavior, but at least I was able to get in and attempt to remedy the problem (not that I have any idea what I am doing). 

All that I have tried was so far has been downloading the video drivers to the USB from the Dell laptop, but it always gets hung up when it has to build packages(?). I'm not even sure if that would work, but I really don't know what else to try.

Any help would be greatly appreciated!

---

### Post by AndyOpie150 on 2013-04-10
What utility did you use to make the Ubuntu 12.10 bootable?
Did You check the md5 sum of the downloaded .iso before installing to the flash drive (USB device)?

---

### Post by gnugen on 2013-04-10
Did you disable Secureboot in your BIOS or UEFI if you have another OS installed on an efi partition? Otherwise try downloading the .iso again and check the md5 sum.

Quick link to download again:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by fantab on 2013-04-10
> **TheDailyToker said:**
> Hello everybody,

I apologize if I am posting this in the wrong area - I am brand new to Ubuntu, Linux and this forum.

I have been booting from a USB onto a Dell laptop without any issues - it seems to be rock solid and I have successfully booted into it many times. The problem occurs when I try to boot from USB on my Dell XPS. I am able to get as far as the main menu, where it asks you whether you'd like to boot or install from USB. When I attempt to boot from usb, I get a black screen for about 10 seconds, and then my PC starts its regular boot cycle all over. I don't even have an opportunity to do anything.

The only thing I could find that might be causing the issue is the the fact that the XPS has dual ATI Radeon HD 4800's. What really confuses me is that I was able to boot Ubuntu 12.10 from a USB on this PC before and battled the wacky video behavior, but at least I was able to get in and attempt to remedy the problem (not that I have any idea what I am doing). 

All that I have tried was so far has been downloading the video drivers to the USB from the Dell laptop, but it always gets hung up when it has to build packages(?). I'm not even sure if that would work, but I really don't know what else to try.

Any help would be greatly appreciated!

Since you are able to boot the USB on "Dell laptop" then I suspect its the graphics ATI RADEON HD 4800. Try the '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")' option. [More info]("http://askubuntu.com/questions/207175/what-does-nomodeset-do"). For [ATI RADEON]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200").

---

### Post by TheDailyToker on 2013-04-10
Thank you everybody for your responses. 

I used the Universal USB installer from [pendrivelinux]("http://pendrivelinux.com") for the installation of both 12.04 and 12.10. I ran a checksum like you guys suggested and the hash value was not corrupted. 

I also tried to add "nomodeset" but it did not make any difference. A bunch of script rolls then my PC reboots. I wasn't able to add nomodeset through GRUB as most tutorials I found suggested. Instead, I had to hit tab at the Ubuntu menu to edit "Run from USB" on the menu and add it at the end of the value listed there, which was not the same as what it appears to be in GRUB.

I'm really not sure what to do; it seems like most people who have the graphics issue are at least able to get in one way or another and work from there. The XPS isn't cutting me much slack.

---

### Post by Bashing-om on 2013-04-10
TheDailyToker; Hi !

Let's see if we can get "nomodeset" option set for you in the kernel boot line of grub.
What results:
Boot the installUSB, as soon as the purple splash screen appears, depress the shift key -> language screen, escape key to accept the default -> boot options screen:
At the boot options screen hit the f6 key -> other options;  arrow down to the preset option(s); Highlight the "nomodeset" option;
space or enter to accept and then the escape key to exit; 
Enter key to continue the boot process to the GUI desk top.

If "nomodeset" option does not work, try the other presets.

Advise on status, and if successful advise is pending to make to make it permanent.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by oldfred on 2013-04-11
If UEFI, you get a grub menu, like first boot after install and have to use e on grub menu and replace splash quiet with nomodeset or other video setting.

 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

### Post by TheDailyToker on 2013-04-12
Thank you very much for these suggestions! Oldfred, you'll have to forgive my ignorance, I am brand new to all of this. From what I can tell, the menu I am taken to is not GRUB.
 I am given six options - run from USB, install on hard disk, test memory, boot from first hard disk, advanced options (which contains nothing) and help. It gives me the option to hit tab to modify a menu entry. This menu is also a lot more attractive than what I remember GRUB to be.
 
Unfortunately, Bashing-om, I am not even able to reach the purple splash screen. As soon as the USB boots, I am taken to a Ubuntu "Installer Boot Menu".  When I hit tab, the value ends with "splash --". I have added "quiet" before it, "nomodeset" after it, replaced "splash" with every possible combination of the commands. I have tried running from USB and installing from USB. Each time, I am greeted with a black screen, then something about "/casper..............." comes up, then a ton of script rolls and my PC reboots again... It won't even entertain the idea. 

When I was playing with 12.10, I was able to boot into some form of GRUB on this PC, and I remember hitting 'e' and being able to modify the entries there. What is going on? :confused:

---

### Post by oldfred on 2013-04-12
I do not have UEFI, but that seems a bit more like the syslinux version of boot, which means you are booting in BIOS mode not UEFI?
From your UEFI/BIOS you should have two choices to boot flash drive. One efi and the other BIOS/Legacy/CSM or something other than UEFI.

---

### Post by TheDailyToker on 2013-04-13
I am booting in BIOS. I scoured the options in BIOS and did not see any other way to boot the flash drive - just USB and USB-FDD. I am starting to lose hope :(. Is Ubuntu simply not compatible with certain PC's? I downloaded the .iso again and am going to re-install 12.04 using UNetBootin. I don't think it will make a difference, but it's worth a shot. I can't seem to find anybody else who is getting the same type of install from USB menu as me, maybe it had something to do with the .iso to USB installer I used originally.

---

### Post by TheDailyToker on 2013-04-13
Well, UNetBootin gave me a different start menu, but the same results.

---

### Post by oldfred on 2013-04-13
Most systems do not have a flash drive under USB, but under choices for hard drives. Have you looked under hard drive boot choices. You also should have a one time boot key that also gives those choices as well as UEFI/BIOS boot order.

---

### Post by TheDailyToker on 2013-04-13
I am using Phoenix - AwardBIOS. My only drive boot choices are diskette drive, hard drive, optical drive, USB-FDD, USB-ZIP, USB-CDROM, USB Device and Integrated NIC.

Interestingly enough, I have been continuing to try to use "nomodeset" on every different combination of boot options and once I actually reached a line to where it says "Kernel panic - not syncing: Attempted to kill init!" It hung up from here and I had to restart manually. Not much for progress, but at least it's something different.

---

### Post by oldfred on 2013-04-13
Do you also have a one time boot key. It is f12 on my system, but it varies.

Under hard drive (+) do you get a second menu?

---

### Post by TheDailyToker on 2013-04-13
On my menu, hard drive isn't expandable. [IMG]http://postimg.org/image/fqm571jpv/[/IMG]
I am not sure if I have a one time boot key, F12 doesn't seem to do anything but I haven't tried any other keys yet. I thought this all might have something to do with RAID, but I have tried everything with it enabled and disabled.

---

### Post by TheDailyToker on 2013-04-13
Ahh sorry for the weird photo. Came out wrong.

---

### Post by oldfred on 2013-04-13
The flash drive only appears if plugged in while booting and it is bootable. Non-bootable flash drives do not appear (I think - as every flash drive I have is bootable now).

---

### Post by TheDailyToker on 2013-04-16
The flash drive appears from my simplified boot menu - not going into BIOS. It boots as it normally would, so I know it's accessible. It also runs flawlessly on my laptop. I'm worried that this video card issue is going to keep me from enjoying Ubuntu :(.

---

### Post by oldfred on 2013-04-16
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by TheDailyToker on 2013-04-17
Oldfred - I appreciate all of your time and help with this issue. I will let you know if I have any success with these.

---

### Post by C.S.Cameron on 2013-04-17
For me 12.04.2 seems to work better on a flash drive than 12.04.

---

### Post by TheDailyToker on 2013-04-18
My goodness, I wasn't even aware of it's existence! This gives me a flicker of hope. I'll have to give it a shot tomorrow. Thanks very much for your input.

---

### Post by TheDailyToker on 2013-04-20
Well, same story with 12.04.2. I don't know what the deal is. I decided to try with 13.04 beta 2 and it boots up and runs with no problem. I don't generally like running betas, but at least I'm able to work it. It doesn't seem to have a problem with my video cards, which I don't understand, but I'm just going to go with it for now and see if it has any problems. Thank you everybody for your help.

---

### Post by fantab on 2013-04-20
13.04 has been quite stable since ALPHA. I haven't had any issues with it. Anyways, its due for RELEASE shortly. So you will be OK with it.

---

### Post by oldfred on 2013-04-21
Someone with a Dell was discussing sputnik and I did not know what it was. But I guess there is a ppa with all the fixes needed for Dell.

And this says all those fixes are now in 13.04. So you can still use 12.04 and the ppa or 13.04 with it included but no long term support.

 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by TheDailyToker on 2013-04-21
Yeah it seems to be pretty solid, I was expecting some bugginess but nothing so far. I think I'm going to try to get 12.04.2 working with the ppa. I like the idea of long term support. I'm going to enjoy a working distro for a few hours, then I'll give 12.04.2 a shot. If all goes well, I'll be partitioning and installing today :D. Thanks everybody for the help. If I can get 12.04.2 up and running I'll make sure to mark the thread as solved.

---

### Post by TheDailyToker on 2013-04-28
Well, no luck with 12.04.2 at all. I gave up; Raring Ringtail seems to be running splendidly as a virtual machine. Not thrilled about not having LTS, but would rather be running something than nothing. Currently partitioning drive for installation. Thank you everybody for your input.

---

