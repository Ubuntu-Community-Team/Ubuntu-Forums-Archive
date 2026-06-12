---
title: "Another network thread..."
date: 2008-10-20
forum: New to Ubuntu
---

### Post by A1len on 2008-10-20
Hey guys. I can't seem to get my nic card working in Ubuntu.

It's an abit 802.11bg

This is what I get for sudo lshw -c network:


Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)





And for lspi:

allen@allen-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)





I don't know if ndiswrapper would be right for this occasion. And I don't know how to install it or anything. I have it on Ubuntu already, just don't know how to use it at all. I'm brand new to all this stuff.

Anyway, if anyone could give me any help it'd be greatly appreciated.

Thanks.

---

### Post by northern lights on 2008-10-20
> **A1len said:**
> Hey guys. I can't seem to get my nic card working in Ubuntu.

It's an abit 802.11bg

This is what I get for sudo lshw [COLOR="Red"]-c[/COLOR] network:


Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	[COLOR="Red"]-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'[/COLOR]
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
For the lshw output to yield useful information (i.e. things other than how to use it itself) the option should either be "-class" or "-C" (capital C). Please repost the output of```
sudo lshw -C network
```
Thank you.

---

### Post by A1len on 2008-10-20
Oh, sorry about that. I thought that information was pretty useless too, but then I don't really know anything yet.


Here you go:

 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0



Thanks a lot.

---

### Post by Bucky Ball on 2008-10-20
Madwifi looks like the way to go and you can check out the first post by reasoner on this thread to get it going. You are going to need to connect with an ethernet cable to get on line to do it though:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=902860](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=902860)

---

### Post by A1len on 2008-10-20
I can't do ethernet due to a broken ethernet cord, a house arrest cuff, and a mother who is unwilling to get me anything. Is there any other way?

The way that I've been downloading onto Ubutnu thus far is by creating a blank partition, downloading via windows vista and sticking them in the blank partition, and then getting them in Ubutnu. I already did the same with madwifi, and was afraid that  they were the answer because I need a program that gets what I need from their .tar files... can I do this any other way?

Thanks.

---

### Post by A1len on 2008-10-20
Nevermind. GOT IT! 

Thanks for your help.

---

### Post by nothingspecial on 2008-10-20
> **A1len said:**
> I already did the same with madwifi, and was afraid that  they were the answer because I need a program that gets what I need from their .tar files... can I do this any other way?

Thanks.

build-essential which I assuming you are referring to (from another thread) is available on your install cd.

System > Administration > Software sources and check the cd box.

---

### Post by Bucky Ball on 2008-10-20
> **A1len said:**
> Nevermind. GOT IT! 

Thanks for your help.

You're welcome. Possibly a brief overview of how so others might benefit from your discoveries ... :)

---

### Post by A1len on 2008-10-20
It was a long process. I had to reinstall though, so I'll document everything that I do *this* time and post it on this thread. It'll be helpful to anyone who:

1. Is trying and set up their recognised NIC on Ubuntu installed *without* the CD AND
2. doesn't have an internet connection of any sort with Ubuntu AND
3. is dual-booting Vista and Ubuntu on the SAME partition; Vista needs to be connected to the internet.

Hopefully I'll find the time to do it again tonight.

---

### Post by Bucky Ball on 2008-10-20
> **A1len said:**
> 
3. is dual-booting Vista and Ubuntu on the SAME partition; Vista needs to be connected to the internet.

Hopefully I'll find the time to do it again tonight.

All looks good but hold on a sec. #3 has me a bit confused. You are booting both OSs from the same partition? Are you trying to do all this on a wubi install? Ubuntu and Windoze are not on separate partitions? Can you post the result of:

```
sudo fdisk -l
```... please?

If Vista is connected to the internet and you are trying to setup a connection through Ubuntu at the same time, you are gonna run into all sorts of problems. One is that the card may vanish because it is being used already. Driver conflicts. Ubuntu can get online through the Vista connection running a Wubi install? I am not sure.

What exactly are you attempting, A1|en? How have you installed Ubuntu?

---

### Post by A1len on 2008-10-21
Well, haphazardly in all honesty. It turns out that repeating it was a little harder than I thought it would be. As a result I have decided to install the Beta for 8.10.

I mounted Wubi using InfraRecorder for the install; I was using a walkthrough as I am a first time user of Linux or anything besides Windows. In InfraRecorder my commands were Action -> Burn Image. I made some Vista discs to back my system up (by the way, HP wasn't willing to send me Vista discs for free, even in the light of me never getting installation discs AND having a software warranty), which I didn't label right away. As a result I actually put in a full DVD-R thinking as I've never used InfraRecorder that it was making me an install disc. In the end Ubuntu ended up on the same partition as Windows. I was going to attemp this again, but numerous people in the IRC strongly advised me against it. 

I got the card to work by putting the necessary madwifi tools on the partition that was meant for Ubuntu in the first place. I didn't unpack anything in Vista, I did all that in Ubuntu; I'm guessing that this was key. So, basically, what I did was download the files in Vista that were for Ubuntu, sent them to my blank _**FAT 32**_ partition (I later formatted it to FAT32 to keep backup files in; I thought I was gonna crash my system), rebooted, ran Ubuntu, unpacked, Ddsabled the recognised but unworking NIC, applied Madwifi via running install.sy,turned the NIC back on and after the following reboot it picked up my wireless network.

A lot of wasted effort to avoid reinstallation on my part. I'm told that I'm lucky I didn't send my machine on a crash-trip from hell. So this time I'm gonna pay much closer attention.

I decided on the Beta because I read that a lot of hardware incompatibility from 8.04 has been worked out. As I can't right now use my ethernet connection, I'm hoping that I'll be able to hop on the net easier. If not... perhaps I'll shrink down vista a gig or two and see if the same tactic will work :) Once it gets on the web, I read that all of the known bugs are able to be worked out.

---

### Post by Bucky Ball on 2008-10-21
Well done. Sounds like you have worked things out pretty well. You are gonna lose some speed with a Wubi install. Installing to a separate hard drive/partition is definitely the best option. Bugs will be sorted more readily (if they are fixable) and downloading things directly through Ubuntu and into the system is definately the way.

That was a pretty neat trick the way you had things running and yea, suprised things didn't collapse! lol But that's what it's all about, ya live and learn.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

When they get to the partitioning section, they take guided I think. You can go manual and just avoid the partition marked NTFS. That is, of course, your Windoze install. You can make whatever partitions then according to disk space available so I usually sit down with the beverage of choice, a pencil and a piece of paper about then.

/
/boot
/home
/pics
/vid
/music
/swap

... not necessarily all on the same disk. Good luck with the install and that sounds like HP.

---

### Post by A1len on 2008-10-21
Hey Bucky:

8.10's giving me the same sudo lshw -C network output as did 8.04:

*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix cap_list
configuration: latency=0

Do you think that I can use that same MadWifi .sy install? It was meant for 8.04, but I think that since the outputs are exactly the same, I can just use the same fix. I wanted to know what you thought before I botched it up. I couldn't find anything about it in any faq's. I'm thinking that since I don't have ethernet, I may keep a gig of harddrive space to format into FAT32 and send it over that way again, or perhaps I can save the .tar package to a DVD and get it in Ubuntu that way?

---

### Post by Bucky Ball on 2008-10-21
The FAT32 drive space is a good idea for swapping data unless you have a USB dongle. I have an 11Gb fat partition for the very purpose of sharing data between the two OSs. I would say the madwifi fix would probably work as it did before, unless you can dig up any new drivers for this particular card that are now included in the 8.10 kernel.  

[http://ubuntuforums.org/showthread.php?t=816780&highlight=AR242x+madwifi](http://ubuntuforums.org/showthread.php?t=816780&highlight=AR242x+madwifi)

 If you have 64bit this link seems to be a winner for that card using madwifi. We can safely say that ndiswrapper is not the way to go after what I have dug up on the net.  :)


ps: out of curiosity, when you go to System->Administration->Hardware Drivers, is there anything in there?

---

### Post by A1len on 2008-10-21
It's 4 in the morning here in California and I have literally been in the NZ IRC for Ubuntu all night troubleshooting this. 

The installer for 8.10 wouldn't let me create a root file in 'manual partitioning', and after troubleshooting the good out of my life, I found that I could use the Automatic (it's almost ambiguous, making it look like the auto-partitioning would install Ubuntu into my ntsf 'free space'. After reading some faq's and realizing that the installer refers to the unallocated space as 'empty space' I figured that I could go automatic). When I finally went automatic it told me that it wanted 200andsomething gigs and would resize my disk. So now, in finality, I'm downloading 8.04 and am gonna run that until the release, or maybe even longer... because my experience installing thus has been bollucks. 

But, the system did acknowledge that I had an Atheros AR242x, which is the chipset of the Abit AirPace 801.11bg, which I use. Back in the Wubi install it recognised the chipset as the same thing. 

And, you probably already know this, but along the lines of me tinkering with the Ubuntu 8.10 boot CD, I discovered that I can bypass Vista's partition allowance and shrink it as much as I want. Of course, it goes nuts when you reload it, but I didn't hit physical memory so it didn't lose anything. That was a pretty cool discovery :)

8.04, here I come!

---

