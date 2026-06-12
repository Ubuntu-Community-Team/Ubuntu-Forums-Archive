---
title: "Would it Be Safe to Use Ubuntu Alongside Windows on My Gaming PC?"
date: 2015-07-17
forum: New to Ubuntu
---

### Post by tassadar4 on 2015-07-17
I want to use Linux as my main day to day OS as I really dislike the direction that Apple is taking OS X which has been my current OS of choice since it's release.  I have some past experience with Ubuntu but I am not highly skilled.  I have always ran it off an external drive or usb stick etc for fear of breaking something.

I do have a PC that I use for gaming; I will try to list the specs below:

[FONT=Arial]
[B]Gigabyte Z97X-SOC Force Intel Z97 (Socket 1150) DDR3 ATX

[/B][/FONT][B]Intel Core i7 4790K (Quad Core 4GHz, Socket H3 LGA-1150) [FONT=Arial]@ 4.9 GHz Overclocked

[/FONT]Nvidia Gtx 980 GPU x 2 SLI[FONT=Arial]
[/FONT][FONT=Arial]
16GB RAM (2x8GB) DDR3 
[/FONT][FONT=Arial]
Samsung 1TB SSD 840 EVO SATA 6Gb/s SSD  x 2 (Raid 0) (running Windows 8.1)[/FONT]
[/B]                    

The system is overclocked and water-cooled; I didn't build this myself I had it made for me as I have MS and I am no longer have the dexterity required sadly.  

I know it would be possible to run Ubuntu off a USB stick or external hard drive but would you think it's a good idea?  I do have the money to build another computer just for linux but I lack space.  Would I run into problems installing Ubuntu on this machine because of the overlock etc?  I don't plan on installing it onto the internal drives so I think I would avoid problems with the raid (hopefully).

Thanks.

T.

---

### Post by sandyd on 2015-07-17
> **tassadar4 said:**
> I want to use Linux as my main day to day OS as I really dislike the direction that Apple is taking OS X which has been my current OS of choice since it's release.  I have some past experience with Ubuntu but I am not highly skilled.  I have always ran it off an external drive or usb stick etc for fear of breaking something.

I do have a PC that I use for gaming; I will try to list the specs below:

[FONT=Arial]
[B]Gigabyte Z97X-SOC Force Intel Z97 (Socket 1150) DDR3 ATX

[/B][/FONT][B]Intel Core i7 4790K (Quad Core 4GHz, Socket H3 LGA-1150) [FONT=Arial]@ 4.9 GHz Overclocked

[/FONT]Nvidia Gtx 980 GPU x 2 SLI[FONT=Arial]
[/FONT][FONT=Arial]
16GB RAM (2x8GB) DDR3 
[/FONT][FONT=Arial]
Samsung 1TB SSD 840 EVO SATA 6Gb/s SSD  x 2 (Raid 0) (running Windows 8.1)[/FONT]
[/B]                    

The system is overclocked and water-cooled; I didn't build this myself I had it made for me as I have MS and I am no longer have the dexterity required sadly.  

I know it would be possible to run Ubuntu off a USB stick or external hard drive but would you think it's a good idea?  I do have the money to build another computer just for linux but I lack space.  Would I run into problems installing Ubuntu on this machine because of the overlock etc?  I don't plan on installing it onto the internal drives so I think I would avoid problems with the raid (hopefully).

Thanks.

T.
Should be fine, 
USB only has a limited number of read/write cycles before they die, so it's not a good idea to run it on USB. Instead, try with an external drive. An external drive connected via eSATA would be best, and would be a bit faster than connecting through USB.

If you want to test if it can be installed, just boot using the live DVD/USB. If it runs properly there, it should run properly when installed to the external drive.

---

### Post by oldfred on 2015-07-17
If overclock is stable then it should be ok.

But Gigabyte boards seem to need a IOMMU setting changed in UEFI.
And the nVidia 980 is new and needs latest drivers. Normally we suggest to just install from Ubuntu repositories, but they are not new enough. And often directly installing from nVidia leads to other issues, so use a ppa or repository that already had the newest nVidia.

       Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[URL="http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1"]http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1

      [/URL]
 The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)
    [URL="http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1"]
[/URL]

---

### Post by oldfred on 2015-07-17
If overclock is stable then it should be ok. You will need newest verison of Ubuntu to have newest kernel & drivers. And that may not be quite new enough, but you can add ppa to make it easy to be newer.

But Gigabyte boards seem to need a IOMMU setting changed in UEFI.
And the nVidia 980 is new and needs latest drivers. Normally we suggest to just install from Ubuntu repositories, but they are not new enough. And often directly installing from nVidia leads to other issues, so use a ppa or repository that already had the newest nVidia.

       Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[URL="http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1"]http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1

      [/URL]The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)
    [URL="http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1"]
      [/URL] [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
15.04 now uses mdadm to support intel fakeraids was dmraid
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

    Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

    [URL="http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1"]
[/URL]

---

### Post by Geoffrey_Arndt on 2015-07-17
_In addition to above_, there is always the option to get a PC with Ubuntu pre-installed.   Can be customized to a great degree, and no install, no risk to user.   Takes about 10 minutes (or less) to setup.

Here's a link with all the main distributors:   [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

I've had a great experience thus far with my System76 Galago UltraPro laptop.   If I really need Windows (I don't), I can always install Windows via Oracle's Virtual Box (or other VM, like VMware Player).

---

### Post by toxx on 2015-07-17
You definitely don't want to run off of live USB all the time. That is reserved for installing Ubuntu, or partition management / other diagnostics mostly. Like others said, it will crash pretty regularly after a few hours use.

Initially I was dual booting Win7 (for gaming) with Ubuntu 14.04 LTS on a 250g drive, so you should be fine since you have way more space. The only reason I ended up moving Ubuntu to a different disk and resizing the Win7 install was a lack of space.
The others will know more about potential issues with overclocking, but I will say that if you're new to Linux, back up the files you care about on your Linux partition regularly, cause there's a good chance that you'll have to re-install it to get around some nonsensical issue at some point.

GL

---

### Post by earruda on 2015-07-20
It should be ok to run Linux and Windows on the same machine. I did it myself for a long time and never had problems. They had their own separate partitions and I even managed files and folders in Windows from Linux. Never had problems.

---

### Post by mastablasta on 2015-07-21
possible points of issues are:
> **tassadar4 said:**
> [B][FONT=Arial]
[/FONT]Nvidia Gtx 980 GPU x 2 SLI[FONT=Arial]
[/FONT][/B][B][FONT=Arial]

Will sli work?
[/FONT]
> [FONT=Arial]Samsung 1TB SSD 840 EVO SATA 6Gb/s SSD  x 2 (Raid 0) (running Windows 8.1)[/FONT]
[/B]
If oyu plan to add it on this disk it could cause problems. not sure. also raid 0 - quite useless - I hope you have backup available or that perhaps you don't care what is on it?! one disk goes, you will loose all.

---

