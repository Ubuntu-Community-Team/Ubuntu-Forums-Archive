---
title: "Trying to &quot;try, not install&quot; Ubuntu 14.04"
date: 2016-01-19
forum: New to Ubuntu
---

### Post by Harold_Driscoll on 2016-01-19
I downloaded it, burned the ISO to a DVD. Boots from the DVD, asks if I want to try or install, I click on try and after a couple seconds the screen goes black and I can't do anything but restart the computer. While doing this it changes from my center display to the right one then back to the center display.

I'm thinking it has something to do with my hardware. I'm also using an external USB DVD drive to boot from. I never installed an internal optical drive when I built the computer.

My hardware:
EVGA X99 Classified
Intel i7-5960X
64GB DDR4
EVGA GTX980 x 3
Samsung 1TB SSD
Dell E2715 27" display x 3

---

### Post by mastablasta on 2016-01-19
only one display probably works in try it mode. on install you will add NVidia drivers which should solve the issue.

so try it with only one display first.

also you may need to use nomodeset boot option: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

furthermore try it by default will use opensource NVidia drives which are reverse engineered and do not support all the card's features (so on certain chips it might all look like "Windows safe mode"). to get all the features of GPU you need the proprietary drivers which have to be installed and then the PC has to be rebooted for them to load. 

to get around this issue on live session you can put the image to USB (use unetbootin, linuxliveUSB or Yumi USB installer) and add 1 or 2 GB persistency to the image. this will allow you to install NVidia drivers and keep them on OS reboot into new live session.

I have no experience with multiple GPU setups and with NVidia cards. all I know is their Opensoruce driver is nowhere near as good as AMD, but their closed source proprietary driver is better than AMD close source drivers.

---

### Post by Harold_Driscoll on 2016-01-19
I'll try it again. I'll document what happens, it never gets that far as to have me select nomodeset.

---

### Post by Bucky Ball on 2016-01-19
Welcome. Yes it does. Boot from the install media, when you see the purple screen with the logo down the bottom, hit a key (or might be F6). This will take you to another options screen. Hit F6 there and you will see more options pop up. Choose nomodeset and proceed to 'Try Ubuntu'.

---

### Post by Harold_Driscoll on 2016-01-19
Oh, OK. I saw what looked like a keyboard and a person next to it. That's when I press F6?
I'll try it again.

---

### Post by Harold_Driscoll on 2016-01-19
Chose nomodeset and I was able to get to the desktop. I went into settings, clicked display, closed settings and lost all of my desktop icons but two, the settings window was only showing 1/4 of it. I couldn't click on anything or use the keyboard so I shut the computer off with the power button. Could it be running slow because it's an external DVD drive? Should I try booting from a thumb drive instead?

---

### Post by oldfred on 2016-01-19
Flash drive is quicker in loading, especially if USB3 in USB3 port. But once loaded just about everything is in RAM so no difference in speed.

You have a very new system, so probably want UEFI, not BIOS. If getting purple accessibility screen then that is a BIOS boot. You get grub menu and have to manually edit linux line to add nomodeset if in UEFI boot mode.

Some systems also need nomodeset & additional boot parameters. Or if booting with Intel internal video, you need a different boot parameter. Some have had to boot with Intel and then install nVidia driver, to get nVidia to work.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

      
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Lots more UEFI info & links in link below in my signature.

---

### Post by Harold_Driscoll on 2016-01-22
I went to the book store and bought Ubuntu Unleashed 2016 Edition (comes with 15.10 and 16.04). I'll install (dual boot) Ubuntu and see if I can't fix the problem I'm having. 
I think the problem is with me having multiple video cards, the motherboard doesn't have on board video.

---

### Post by Bucky Ball on 2016-01-22
I don't advise installing 16.04 LTS. It is not released until April. Pretty weird distributing a testing version in a magazine ...

---

### Post by Harold_Driscoll on 2016-01-22
Only 15.10 is on the DVD, you get one free chapter of the new book once 16.04 is released.
I thought 16.04 was on the DVD but it's not.

---

### Post by Bucky Ball on 2016-01-22
Good. I'd leave it alone for the moment. Not a great place to start.

---

### Post by Harold_Driscoll on 2016-01-23
I got 15.10 to install. Some graphical errors during install. Installed Linux drivers from NVidia.
Can't get multiple displays to work. The computer sees all three cards and all three displays.

---

### Post by oldfred on 2016-01-23
If you have issues with three monitors that is another question.
Best to start a new thread with that in the title.
Only a few users have more than on monitor. But I have seen some threads where users have many.

---

