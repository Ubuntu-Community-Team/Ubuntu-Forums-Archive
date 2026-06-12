---
title: "Slow boot and System Program Problem"
date: 2019-08-21
forum: New to Ubuntu
---

### Post by eloi67 on 2019-08-21
Hello, 

I'm pretty new to Ubuntu although I'm making some progress. 

Let me briefly introduce you to the history of my issue:

I have a brand new computer on which I installed Ubuntu 19 from the Ubuntu website (iso burned on a USB flash drive). It's important to mention that I set it up to dual boot with the built in windows 10.

Everything was going perfectly well until I said yes to a window proposing a BIOS firmware update and I pressed on yes. The next day, when I booted my PC, the BIOS updated and grub didn't appear and it instead booted to windows. I thought it just changed the boot order but no, it simply deleted the Ubuntu entry from the boot option in the BIOS ! I then made a thorough search on Google on how to fix the issue and nothing worked ! Running boot-repair from a flash drive didn't help, I even tried to manually installed grub, but it couldn't find my Ubuntu install... 

I then saved all the files from the install (that I could access from a bootable flash drive with ubuntu on it) and used the reinstall ubuntu option from that flash-drive. The new ubuntu 19 was really buggy, taking forever to boot, (even though before it took 3sec), and freezing when I tried to shutdown or access parameters. Long story short, after numerous installs and reinstalls, I decided to completely format my SSD and install Ubuntu 18.04 on it (and I will later install windows). 

This is the version that I am using now. It is way more stable, and I'm able to work on it, even though it's definitely not the perfect install I had when I first installed ubuntu. 

First of all it takes at least 20 to 30 seconds to boot, which is in contrast to the 3 second needed previously (see my specs below, this is a work computer). 

Also, everytime I boot in, there is the error message "System Program Problem" on a popup that reappears even if I delete the crash files in the var folder. 

I ran boot-repair which didn't help, and there might be something wrong with the Bios since windows boot is still an option in the Bios even though I wiped out the drive before installing Ubuntu 18.04 and didn't reinstall windows yet !


I would like to clean this install to have a faster boot, not having the error message, and honestly mainly to start on this new computer without a sketchy Ubuntu install. 

Could you help me with that ? 

Since this install is somehow working, I would like to avoid having to reinstall everything again, which is really time consuming (and I have work to do on that machine ! xD )

Thank you very much, 

Eloi


Here are some infos you might find usefull, tell me what else you need from me : 


this is what boot-repair gives me:

[http://paste.ubuntu.com/p/8S4m2FHDXw/](http://paste.ubuntu.com/p/8S4m2FHDXw/)



My PC is a lenovo Thinkpad P52, here are the specs:

Intel Xeon E-2176M Processor (12MB Cache, up to 4.40GHz), 6 cores, 12 threads
15.6" FHD (1920x1080), IPS, No Touch
64GB (32+32) DDR4 2400MHz SoDIMM
NVIDIA Quadro P2000 4GB
Hardware dTPM2.0 Enabled
1TB Solid State Drive, PCIe, Opal 2.0, TLC
Intel Dual Band Wireless-AC 9560 2x2 AC, Bluetooth Version 5.0 vPro

---

### Post by michaelharden1a on 2019-09-22
It seems you are trying to dual boot windows 10 with Ubuntu? And forgive me, you removed windows 10 and the bios still has windows listed and you want to at some point reinstall windows 10?  If I have this straight, then the reason why bios is reading windows is because of the hidden windows partition used by bios to reinstall windows, if you don’t want to install windows this way use Ubuntu disk management program like disk, to remove the partition.  This should remove the entry from the bios but it in turn will force you to install windows from a disk.

---

### Post by Autodave on 2019-09-22
Your 20-30 second boot time does not seem excessive at all.  I have a faster machine than you do and I take 21 seconds to boot.  Why you only had 3 second boots is beyond my pay scale.

Understand that Windows does not turn off: it merely hibernates.  That is why it seems so quick to "power up".  It isn't booting up. it is just coming out of hibernation.

You really need to install Windows first.  Installing it after Ubuntu is installed will not be easy, if at all possible.  And stick with the LTS releases like 18.04.

The system program fault may be nothing at all.  I had that same message on this machine for over a week, but with the latest update, it has disappeared.

Someone else will surely respond to this post as well, but if it were my machine, I would get Win10 back on and fully updated.  Then, make sure that *fastboot* is disabled in the BIOS and get 18.04 installed again.  Then report back with any issues.

---

