---
title: "Dual booting with 2 HDD"
date: 2016-04-21
forum: New to Ubuntu
---

### Post by scaryred24 on 2016-04-21
I somewhat new to this so this is where I was coming from. I tried out Lubuntu 14.04 LTS last year on Virtual Box while mimicking what my PC of choice would be like running it and I ended up liking it. However with the complicated position I'm currently in my family members would flat out refuse to adapt to Lubuntu since my parents constantly uses a printer that would only work with Windows and my brother some some geeky stuff that also only works with Windows. So now since not only the latest LTS came out today but I just got my secondary HDD in the mail today too. So I would like to dual boot my older computer rig from 2007, but I am a little uneasy on going through with it.

Let me explain why. My PC of choice that I am currently going to follow through with this runs Windows XP but the place that I got it from refused to give me the boot disc without making me pay for it. They might of well stop supporting it since XP hasn't been widely adopted since 2014. So with that out of the way I have no way to back up my stuff when I finally do this or even do a fresh reinstall sine I run the risk of losing 9 years of personal documents. so I would like to do this without touching the Partition of XP as much as possible so I don't end up having to reinstall the whole thing without having to resort to some shady stuff. So I know the risks of Dual Booting from one HDD so I opted for two to reduce the risks as much as possible. I also want to make the boot order to go as Lubuntu as the master while the slave being as Windows XP so I only have to run that when I have to. It not only makes it a little more of a pain for me to adapt to Lubuntu but both my parents would rather prefer Windows as their choice of OS. They would also not bother with the boot order and would have Windows to be prioritized over everything and I don't want them to think that way since XP is pretty much dead.

So this may take a good couple of days to plan it out on what I need to do to get it where I want it to be. My goals are to have my PC of choice to dual boot, but would like to have Lubuntu to be the primary OS and XP as a backup. I also don't want to screw with the MBR on XP at all, however if I don't have much of a choice I would have to take a risk and do it so the less the better. And the last part of this is to maintain this as much as possible while minimizing the risk of possible data loss without having to go through much struggle sine I am currently on a limited budget right now. If it going to get technical and complicated, then I wouldn't mind going through that path just to achieve my goal. If at any time it would seems like I would need a walk though, I wouldn't mind that either since I am not that familiar with any Linux Distributions since I started with Android back in 2013 for casual use, and Ubuntu probably back to like last October so. So I can't say that I know it very well but have worked with it in the past just to get by.


This is my PC specs of the build I would like to do this on:

Operating System: Windows XP Home Edition 32-bit SP3
CPU: AMD Athlon 64 X2 4400+
RAM: 2x 1.00GB Single-Channel DDR2 860MHz
Motherboard: ASUSTeK Computer INC. M2N
Graphics: 320MB EVGA NVIDIA GeForce 8800 GTS
Storage: 149GB Western Digital WDC WD1600JS-61MHB1
Optical Drives: LITE-ON LTR-52327S
Audio: SoundMAX Integrated Digital HD Audio
Network: Nvidia Integrated chipset

And the HDD I'm going to install Lubuntu on (either 14.04 LTS or 16.04 LTS): [COLOR=#111111][FONT=Arial]Seagate ST3250310CS 250GB 7200RPM 8MB Cache SATA 3.5[/FONT][/COLOR]

---

### Post by oldfred on 2016-04-21
I now have new UEFI system(s), but my old system was XP on sda, and Ubuntu on sdb, sdc, sdd, even eventually a new SSD as sde. And flash drive as sdf was full install of Ubuntu.
Most were older smaller drives, original system from 2006 was two 160GB drives. I was going to install both XP & Ubuntu on same drive and use other drive as backup. But somehow made a mistake and it was the best mistake I have made (among many). Ubuntu ended up on sdb.

Does BIOS let you choose Boot drive. Newer PATA drives probably do. But I built system in 2006 with SATA drives which then cost about $10 more. If older PATA/IDE system, you may have jumpers on drive, then not sure if new drive would even be compatible.

Mixed SATA & PATA can have drive order issues. You really want to keep Windows as sda, and new Ubuntu drive as sdb. If only SATA be sure to plug drives in SATA port order with Windows in SATA0. Ubuntu as SATA1 and then DVD or other drive(s).

You may need nomodeset to boot with nVidia card. And that card will require you to install legacy (older) driver from Ubuntu repository. But need to check nVidia site on correct Legacy version as there are several.

If Windows on SATA drive, it may be easier just to unplug Windows drive, install Ubuntu and replug Windows back into SATA0.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 
   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by scaryred24 on 2016-04-21
> **oldfred said:**
> Does BIOS let you choose Boot drive. Newer PATA drives probably do. But I built system in 2006 with SATA drives which then cost about $10 more. If older PATA/IDE system, you may have jumpers on drive, then not sure if new drive would even be compatible.

My bios does support letting me chose the boot drive, but it is limited to the first 3 that I can set. I could just use a 16GB USB 2.0 external flash drive which should be more than sufficient for the job.

> **oldfred said:**
> Mixed SATA & PATA can have drive order issues. You really want to keep Windows as sda, and new Ubuntu drive as sdb. If only SATA be sure to plug drives in SATA port order with Windows in SATA0. Ubuntu as SATA1 and then DVD or other drive(s).

I sadly had to replace my busted DVD drive for a crappy CD drive back in 2009. The sacrifices I had to make when on a tight budget at the time. I now know that you can no longer use Lubuntu Alternate Boot image on a CD anymore except for 14.04 LTS so that's why I am opting into using a Flash Drive and yes my disc drive is set up in IDE or PATA if that is what you are referring to.

> **oldfred said:**
> You may need nomodeset to boot with nVidia card. And that card will require you to install legacy (older) driver from Ubuntu repository. But need to check nVidia site on correct Legacy version as there are several.

The only thing I can find that could go wrong is if anything within the Ubuntu family of Distros doesn't install at least anything with Nvidia GPU drivers, it will not connect online. I did test this out around the Holidays last year to see if it can connect online and it worked no problem. IF anything were to go wrong, I can always load up another flash drive with the correct drivers on my main PC I currently use which runs on Windows 7 Home Premium. I don't know how I can go about if I do end  up hitting this wall but I am certain that I may figure it out on my own, but I do not mind any advice that I can end up using if this ever happens so I can tackle this in more than one way if possible.

> **oldfred said:**
> If Windows on SATA drive, it may be easier just to unplug Windows drive, install Ubuntu and replug Windows back into SATA0.

That is kind of what I was suspecting to do to ensure that I don't end up screwing it up. I can get into my case and navigate the setup fairly well and I'm glad that I still have all of the origional documents for it.

> **oldfred said:**
> Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 
   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

I did come across some of these over the past 5-8 months when I was looking up all the possible directions that I can tackle this with.

I thank you for the kind advice. I'll try to get this at least setup ASAP since currently I don't have the sufficient work space nor the time to do so right now. I'll try to respond back if I made anymore progress or does that count as double posting?

---

### Post by oldfred on 2016-04-21
If video issues.
You need to press a key as soon as you see the accessibility icons (tiny person & keyboard) at bottom of screen then f6 to add nomodeset.

Then on first boot you manually edit grub's linux line:
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by scaryred24 on 2016-04-21
> **oldfred said:**
> If video issues.
You need to press a key as soon as you see the accessibility icons (tiny person & keyboard) at bottom of screen then f6 to add nomodeset.

Then on first boot you manually edit grub's linux line:
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Well not having a signal from the GPU wasn't actually the issue I might have. I apologize that I wasn't clear enough but the network card is integrated into the motherboard which was supplied by Nvidia. Ubuntu does a good job recreating the drivers needed for a video signal above 640x480 at 8bpp in a windows environment if it ever happens. the problem arises that it needs Nview for the integrated network chip to function. Without the needed drivers for the GPU to fully function, the resolution will be limited, the color range will locked down to something among the lines of CGA graphics and the network function wouldn't work.

---

### Post by oldfred on 2016-04-21
I do not follow network issues.
Probably better to post a thread with that & specific nVidia chip version. Many that know networking have various fixes. 
But I have not heard of nVidia for network connections.

Found this:
[http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

Do not know it that driver is still available for Ubuntu or not.

---

### Post by scaryred24 on 2016-04-21
> **oldfred said:**
> I do not follow network issues.
Probably better to post a thread with that & specific nVidia chip version. Many that know networking have various fixes. 
But I have not heard of nVidia for network connections.

Found this:
[http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

Do not know it that driver is still available for Ubuntu or not.
I'm quite sure that Ubuntu uses that from it's repositories. If not I wouldn't even have to bother with it since the Live CD should already includes the necessary drivers for it to work. I'll open up a thread there if I ever get to that point and have no internet.

---

### Post by scaryred24 on 2016-04-22
Alright then. I did it last night. Lubuntu 16.04 LTS is a total mess on my end, but I'll ultimately open up a tread for that later on to quite possibly report my concerns and feedback. Now I ended up hitting two problems. One is that My windows install is on a HDD that is a combination of SATA and a molex connection. I have never seen that combination before so I ended up opting to all SATA since I had some spare parts from other PC builds that I could salvage from. This problem leads to that boot order problem that you were referring to. The other problem was that I can not get Lubuntu to run Grub at all. I got it to work once but it didn't have my install of Windows XP listed there. It might get me to reinstall Lubuntu for scale back to 14.04 which I initially wanted to do, and possibly get grub up and running again. So Wondows is on SATA1 on my motherboard while Lubuntu is on SATA2. Is there any advice or possible ways that I can end up takling this without touching the Windows partition as much as possible?

---

### Post by oldfred on 2016-04-22
Does BIOS show both as bootable?
There were some old systems that had a main PATA drive and one SATA connection. And they only booted from PATA/IDE connection.

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

Found this:
[https://github.com/torvalds/linux/blob/master/drivers/net/ethernet/nvidia/Kconfig](https://github.com/torvalds/linux/blob/master/drivers/net/ethernet/nvidia/Kconfig)
Do not know if then kernel not including nVidia forcedeth driver unless complied in.

---

### Post by scaryred24 on 2016-04-22
> **oldfred said:**
> Does BIOS show both as bootable?
There were some old systems that had a main PATA drive and one SATA connection. And they only booted from PATA/IDE connection.

Yes they both show up as bootable drives. However I could only boot from one from the list at once. I have it setup to boot in this order currently: 3.5in Floppy 1.44mb, HDD (Windows XP), Cd-Rom. However in a different menu I can have the bios choose what HDD to boot from up to 4 different drives. If I end up switching that the boot priority will change accordingly to what HDD I selected from there. Also anything that isn't a HDD is configured with an PCI Express x1, PCI Express x16, IDE ribbon cables, and molex connectors.

> **oldfred said:**
> Found this:
[https://github.com/torvalds/linux/blob/master/drivers/net/ethernet/nvidia/Kconfig](https://github.com/torvalds/linux/blob/master/drivers/net/ethernet/nvidia/Kconfig)
Do not know if then kernel not including nVidia forcedeth driver unless complied in.

I would have to check that one out.

---

