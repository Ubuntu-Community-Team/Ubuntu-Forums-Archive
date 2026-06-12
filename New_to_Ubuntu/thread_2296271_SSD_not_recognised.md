---
title: "SSD not recognised"
date: 2015-09-24
forum: New to Ubuntu
---

### Post by nginmu on 2015-09-24
I have an old Lenovo ThinkCentre 3000 J100 desktop PC circa 2006. Flat on desktop type rather than tower.

Motherboard is 8S661FXMTIU rev 1.0 - seems to be very distinct from the Gigabyte 8S661FXM-775 which I thought it was initially.

2 Gb RAM, Celeron processor, AGP video card, CD ROM.

BIOS updated to latest available from Lenovo's legacy support site, brand new CR2032 BIOS battery metered at 3 point something volts. when I updated the BIOS using the supplied tool there were various options for updating different areas of the BIOS and clearing DMI etc, I took all options.

Trying to get Lubuntu (very recent download) to install on this SSD: [http://www.ebay.co.uk/itm/361157046352](http://www.ebay.co.uk/itm/361157046352)

The SSD is happily recognised by the BIOS and by MS-DOS 6.22. Booting MS-DOS 6.22 from a USB stick, I can fdisk and format in DOS and create files on the SSD which comes up as C:\ drive, albeit formatted as a small size.

But, Lubuntu cannot see the drive at all!

Neither during installation nor when falling back to the live CD. I tried several linux partitioning commands in the terminal 'sudo gparted' etc but these seemed to just confirm the situation that Lubuntu simply was unaware of the SSD.

Tried it in both SATA ports with several different cables, no difference :-(

I've tried the two different options in the BIOS 'IDE' and 'RAID', there is no option for AHCI.

I am at a loss, is there anyone with any guidance?

---

### Post by mörgæs on 2015-09-25
Hi, welcome to the fora.
Which versions of Lubuntu have you tried?

---

### Post by nginmu on 2015-09-25
Hi, 15.04 desktop CD (Intel x86) from [http://lubuntu.net/](http://lubuntu.net/)

I tried Ubuntu 14.04 32-bit as well with similar results (PC ran quite slow though which is why I switched to Lubuntu)

---

### Post by mörgæs on 2015-09-25
Does a live boot of Lubuntu 15.10 (beta) see the drive?

---

### Post by nginmu on 2015-09-25
Thanks, I'll try that as soon as I have an opportunity - work is calling right now :-(

For info my current configuration is:

WDC WD800JD-08LSA0 (09.01D09) SATA 'traditional mechanical' HDD on SATA0
The SSD, partitioned & formatted to maximum size under MS-DOS 6.22, on SATA1
BIOS SATA setting set to 'RAID', but RAID not set up in the RAID configurator that comes up immediately following 'discovering IDE devices' on boot
2Gb RAM
Video card: PNY GeForce 6200 DDR2 256MB AGP DVI VGA TV Out G606200A8E24L/0TE G606200A8D24LPB

With the above, Lubuntu 15.04 desktop CD installed to the traditional HDD just fine, the HDD comes up as sda - but SSD still invisible. 

Not sure of the exact size but MS-DOS 6.22 didn't see the whole 64Gb of the SSD, it only partitioned and formatted a fraction of the available capacity but I'm guessing this is just an expected limitation of that old OS?

Soon as work finishes I'll try Lubuntu 15.10 (beta) from hxxp://cdimage.ubuntu.com/lubuntu/releases/wily/beta-1/lubuntu-15.10-beta1-desktop-i386.iso

Managed to squeeze it in before work - but no luck. Under preferences/disks in 15.10 beta live cd, I can see:

- the 80Gb mechanical HDD /dev/sda1
- The PATA IDE CDROM (master on PATA IDE slot #1) /dev/sr0
- '1.1Gb block device /dev/zram0'
- '708Mb loop device /cdrom/casper/filesystem.squashfs'

---

### Post by mörgæs on 2015-09-25
Does beta 2 behave better?

---

### Post by oldfred on 2015-09-25
I am not sure I would use a SSD on a system that does not have AHCI.
It is my understanding that trim does not work unless you have AHCI. And while it may be fast at first but once all sectors are used, then it will slow a lot as it really needs to be trimmed.

But you need to have IDE mode not RAID.

---

### Post by nginmu on 2015-09-25
Downloading hxxp://cdimage.ubuntu.com/lubuntu/releases/wily/beta-2/lubuntu-15.10-beta2-desktop-i386.iso to give it a try.

I read a comment somewhere that stated that enabling RAID, enabled AHCI as a side effect. ( link - [http://forum.crucial.com/t5/Crucial-SSDs/Why-do-i-need-AHCI-with-a-SSD-Drive-Guide-Here-Crucial-AHCI-vs/td-p/57078](http://forum.crucial.com/t5/Crucial-SSDs/Why-do-i-need-AHCI-with-a-SSD-Drive-Guide-Here-Crucial-AHCI-vs/td-p/57078) )  That's why I've been trying the RAID option in the BIOS. I have also been trying the IDE option as well, but unfortunately that setting doesn't seem to result in success either.

I'm looking around at other motherboards that can make use of the other hardware I've got, maybe I can pick up something on ebay that has AHCI. If anyone has any particular suggestions or reccommendations what to search for, I'd be glad to hear. 

I have these bits..

 An Intel Pentium D 920 2.8GHz/4M/800 processor
A Celeron processor that came with the existing motherboard (the existing board won't take the Pentium D)
The IDE CDROM, 8x AGP video card, SSD & traditional HDD referred to earlier

I'll persevere with the existing motherboard for now, I hate being beaten, but if it's easier to buy a slightly better mobo that's an open option..

If I bought a PCI SATA card, could that itself provide AHCI?

Running beta 2 now (live CD) but still no SSD visible using either IDE or RAID setting in BIOS.

Incidentally though, beta 2 has fixed one thing that was wrong - my Belkin USB bluetooth dongle F8T017 now works flawlessly whereas on 15.04 it was horribly broken :-)

Is this controller card likely to be supported by Lubuntu (and make my SSD visible, bootable and TRIMmable?):

Promise Technology SATA300 TX4302 Controller card:

[http://www.ebay.co.uk/itm/161687737358](http://www.ebay.co.uk/itm/161687737358)
[http://www.xander.com.hk/product/product_manual/prod_manual_192.pdf](http://www.xander.com.hk/product/product_manual/prod_manual_192.pdf)

There's some reference to it here from a long time ago;

[http://ubuntuforums.org/showthread.php?t=875011](http://ubuntuforums.org/showthread.php?t=875011)

---

### Post by nginmu on 2015-10-03
Just for completeness. Recieved TX4302 SATA card, plugged it into PCI slot. Rebooted & the TX4302's own bios appeared on the bootup screen immediately following the mobo's. It found the SSD instantly. With mobo's boot order set to CD first, was able to install lubuntu 15.10 beta 2 no problem to the SSD. Machine now, post installation, boots fine from SSD. The mobo's BIOS seems to talk to the TX4302 card for booting purposes no prob.

Still not sure whether the TX4302 does TRIM, and if it does, how to set it up properly but I guess that's another chapter

Bluetooth's gone AWOL again, but I have an allegedly linux-compatible USB dongle on the way. ORICO BTA-402 with CSR8510 Chipset.[URL="http://www.ebay.co.uk/itm/291476517684?_trksid=p2057872.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT"]
[/URL]

---

### Post by mörgæs on 2015-10-04
Progress :-) 

If you want you could discuss the Bluetooth bug in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427") and / or report it in Launchpad.

---

### Post by tgalati4 on 2015-10-04
IBM (and I presume Lenovo as well) tend to "whitelist" their hardware on enterprise-class machines.  Is it possible that the SSD was not on the BIOS list of "approved" hard disks and therefore was ignored?  This forces the IT manager to buy IBM/Lenovo-branded parts, as 3rd party parts fail to be recognized.  This might explain why a simple installation has become so difficult.  I would try some older, spinning drives (not Lenovo-branded) and see if they are recognized.  

It could be the version of AHCI supported.  It's possible that the RAID mode does not support AHCI completely, or you need 2 disks to really create a RAID.  Try putting a second, identical SSD in the machine and see if you can configure it as hardware/fakeRAID.

Sometimes simple things are really impossible to accomplish.  Sometimes really difficult problems are easy to solve.  Linux gives you difficult problems that are impossible to solve.

---

