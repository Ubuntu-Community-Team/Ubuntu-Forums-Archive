---
title: "Existing OS not recognised by live DVD and Scroll Arrows on Ubuntu"
date: 2020-10-19
forum: New to Ubuntu
---

### Post by gbest5089 on 2020-10-19
1. Wanting to install Ubuntu 20.04 on a "new" (refurbished) Lenovo PC with an existing Win 10 installation that I want to keep and be able to select.  Installation progresses initially but then tells me no OS has been detected.  It has worked out that there are 500MB of files on the 1TB hdd and might allow me to set up a partition in the remaining free space.  I am concerned that if I just go ahead on this basis, I won't get a startup menu allowing me to select Win 10 or Ubuntu. 
Is there a simple explanation or do I have a problem?   Advice muchly appreciated.
2.  I'm rather new at this, having played a little with Ubuntu several years ago, and, more recently have used Mint Cinnamon as a Win 7 replacement on an older 32-bit PC.  The Mint-killer (for me) is its lack of scroll bar stepping arrows, together with my inability to follow forum posts well enough to insert them as seems may be theoretically possible.  I am sincerely hoping that replacement will be possible in Ubuntu.
Looking forward to the normal helpful response, thank you.
Gordon

---

### Post by CelticWarrior on 2020-10-19
Any Windows 8 or newer as Fast Startup (=hibernation) enabled by default. For a dual-boot users must disable it and shutdown before booting the Ubuntu installation media.

And installation media must be booted in the same mode the original OS is installed, BIOS or UEFI.

And using a DVD in 2020 feels like a joke!

---

### Post by grahammechanical on 2020-10-19
This is the help document. Note the sections The case when Ubuntu must be installed in UEFI mode and General principles.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Using a DVD to install is acceptable but slower. If you have the drive and you have the discs then why buy a USB memory stick? Especially if the machine has USB 1 ports and not USB 2 or 3.

Regards

---

### Post by gbest5089 on 2020-10-22
Thanks CelticWarrior and GrahamMechanic,
I have now progressed with your help.  Must say it has turned into a much more complicated job than it has ever been before (with Win XP and Win 7) but that's progress, I guess. Have disabled RapidStart on Windows but Windows still not seen by the linux disc.  I see I might have to disable secure boot as well but have not yet managed to do that.  This whole learning process may have helped me in another area: I previously installed 32 bit Mint on an Atom-powered netbook (originally Win 7).  That installation has been somewhat unreliable and now I see that the UEFI installation I used was probably not compatible with the original BIOS.  I guess I'll get around to trying to fix that once I get this other one sorted.
Thanks again for your help
Gordon

---

### Post by CelticWarrior on 2020-10-22
Depending on the hardware you may need additional settings changes at UEFI. And the difficulty increases, I'm afraid.

Disabling Secure Boot is usually easy and the preinstalled Windows works either way. Some manufacturers make it harder by hiding the Secure Boot settings in something like "OS selection" where "Windows"=Secure Boot ON and "Other" (or "Android")=Secure Boot OFF. Occasionally other nomenclature is used.

For when the Ubuntu installer doesn't detect some drives when it should the culprit is typically some disk modes that aren'rt compatible with Linux - "RAID" or "Intel RST" -, RAID, namely with professional server controllers is perfectly supported but the RAID on firmware (UEFI) that many laptops use nowadays isn't. So, we need to change it to AHCI. There's no performance penalty, it's just one is supported and the other isn't. At this point we need to pay attention because AHCI support must be installed on Windows before changing the setting, otherwise Windows won't boot (it can be changed back, of course, but then you wpon't be able to install Ubuntu).

---

### Post by gbest5089 on 2020-10-23
Hi CW, 
Forgive the dumb question, but just wondering if it is it possible (and potentially easier?) to ignore the fact that the Ubuntu installer does not recognise windows and just install Ubuntu in the new partition (already created), then add a Grub menu that would (a) run on startup and (b) still allow selection of a windows or Ubuntu boot up?  If so, any recommendations for learning enough about grub to maker all that happen?   Seems like the menu might be pretty much already on the live disc somewhere; "just" a matter of finding it and presumably pointing it at the windows start point.
Hoping not to exasperate you too much,
Gordon

---

### Post by yancek on 2020-10-23
If your windows 10 was preinstalled, it is almost certainly a UEFI install and your best first option is to follow the instructions to the official Ubuntu documentation in post 3 above.
Can you boot windows and use the Disk Management tool to shrink your windows partition?  That would be the first step. There are a number of reasons why the Ubuntu installer will not recognize a windows OS some of which are described above.

It may be possible to do what you are suggesting in your last post but we don't really have enough information on your disk/partition setup to say.
One thing to note from the link in post 3, if you install Ubuntu in the older MBR method and windows is UEFI, Grub will not boot windows.  The reverse is also trure.

---

### Post by oldfred on 2020-10-23
You may also have UEFI setting for drives as Intel RST or RAID? That needs to be AHCI.
But Windows has to have the AHCI driver installer to work in AHCI mode.

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

Even if older system, there may be an update available to the UEFI. You need to install that also.

---

