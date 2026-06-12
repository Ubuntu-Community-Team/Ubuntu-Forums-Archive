---
title: "Dual Boot issues"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by Broly Ultimatrix on 2012-12-03
Hello and thanks for reading,

I have recently tasted the sweetness of Linux and my sweet tooth enjoyed it so. Much research and many live cd's /installs later and I find that Ubuntu(Kubuntu to be specific) is so far my favourite though my dream it to build an OS from scratch using Arch though that's still a lot of time and experience away.

My problem right now comes with trying to dual boot windows 7 and Kubuntu 12.04.1 LTS amd64. I have backed EVERYTHING up to two separate hard drives (because it's just that much data) and did a fresh install of windows 7 (which I'm willing to do again) After installing windows 7 and booting to said OS I checked the partitions and saw two, a small 100mb system requirement partition and my massive windows 7 partition (I have a 1.5 tb HDD) I then installed a fresh iso of kubuntu 12.04.1 LTS AMD64 and the LinuxLive USB Creator program. I created a liveboot image on a 4 gig flashdrive booted to it and when I installed the KubuntuI told it to install alongside windows 7 and to leave 200gb for the windows partition. Later i would have resized the Kubuntu partition to 200gb as well leaving the rest to make a ntfs partition to hold all my documents, pictures, videos and downloads or what have you. Before I would resize anything I tried to boot to the kubuntu to ensure it worked. I downloaded easyBCD because it seemed to be the best software to dualboot based on my internet research and created a Grub2 linux entry. after that I checked the settings and they were as follows.

---------------------------------------------------------------------------------------------------------------------------------

There are a total of 2 entries listed in the bootloader.

Default: Windows 7
Timeout: 30 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Windows 7
BCD ID: {Current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Kubuntu 12.04
BCD ID: {1f1b1751-3db9-11e2-a185-fed371bf17b8}
Drive: C:\
Bootloader Path: \NST\AutoNeoGrub0.mbr

---------------------------------------------------------------------------------------------------------------------------------

When I restart and click on Windows 7 then it boot's to 7 just fine but when I click on Kubuntu 12.04 I get a weird grub4dos 0.4.5 c command line interface. I'm going to do some research and see what the actual bootloader path is for kubuntu 12.04 and try and set entry 2 to that but any other insite would be muchappreciated. My main computer and currently the most powerful one in the house has been out of commission for far to long and I would like to have my dualboot set up. Thank you for your time.

---

### Post by oldfred on 2012-12-04
Not many here know EasyBCD.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

    
EasyBCD does not work with the new UEFI/gpt configurations, but it seems like you have BIOS/MBR(msdos).

EasyBCD actually uses grub4dos to chain load to the real grub install. Most suggest just using grub2 in the MBR, but a few do use EasyBCD and make it work. Some claim hibernation then works, but any hibernation in dual boot has risks as if you write into the hibernated system you can damage it and will lose what you copy into it.

Also grub2 is too large to install correctly to a PBR - partition boot sector. It normally has code to search for the rest of grub in the /boot folder, but when stuffed into a PBR it uses block lists or hard coded addresses to know where to jump to to continue booting. Then any major grub updates or even an agressive fsck may move a grub file and break the blocklist lookup. Then you have to reinstall grub2 to the PBR. Just have a working liveCD and know how to reinstall grub to a PBR when necessary.

---

### Post by Nightcreeper on 2012-12-04
Why use the EBCD? I just use a seperate partion for linux and let the installer load grub on the default boot device, though recently, I have been doing it so I boot directly from a secondary SSD with two versions of Linux (mint13 and Ubuntu 12.10) by hitting the boot menu for my motherboard. Have you installed Kubuntu by itself to see if it is an issue with a driver or installation, rather than grub? I have ran into that before and had to use "startx" on the distro I was using at the time.

---

### Post by Broly Ultimatrix on 2012-12-04
I had dual booted Windows 7 pre existing and Ubuntu 12.10 and 12.04 before and it worked fine I'll reinstall with just Kubuntu later and see if it works.

---

### Post by Broly Ultimatrix on 2012-12-04
Installed Kubuntu as only OS on hard drive and it booted fine. Posting this message from Kubuntu. Even installed All the updates. Didn't use the Proprietary AMD/ATI driver  (it's always a pain for me to enable and doesn't really work). I used the "spci | grep -i pci || lspci" command in the ~:bash terminal and it yeilded the following results

terin@terin-A75MG:~$ spci | grep -i pci || lspci
No command 'spci' found, did you mean:
 Command 'sci' from package 'scheme2c' (universe)
 Command 'spc' from package 'supercat' (universe)
 Command 's2ci' from package 'scheme2c' (universe)
 Command 'xpci' from package 'xdiagnose' (main)
 Command 'lspci' from package 'pciutils' (main)
spci: command not found
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6550D]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6                                                
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5                                                
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7                                                
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)          

Doesn't look to me like there are any problems though I'm not to familier with terminal commands being a li-noob and stuff so if theres a better command or anything else you guys want me to run while it's in for diagnostic perposes I can do that. Also a guide to properly (and more guarenteedly to work) dualbooting windows 7 and kubuntu I'll do just about anything for it to work :P

---

### Post by oldfred on 2012-12-04
Is Windows still installed or just Kubuntu?

Often best to install Windows first or at least allocate the first primary partition to it. But Windows will install to any primary partition (sda1 thru sda4) formated as NTFS with the boot flag. Windows will overwrite the grub2 boot loader in the MBR, so you will have to reinstall that if installing Windows second.

       [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
    
       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

