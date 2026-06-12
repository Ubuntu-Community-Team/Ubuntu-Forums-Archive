---
title: "USB device detection"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by JHawk56 on 2012-12-10
I'm fairly computer savvy having built numerous Windows PCs, but I'm new to Linux. I'm having trouble with a Linksys MA101 Rev B USB wireless network interface.

After various web searches it seems I may or may not have to install a driver, but before I even get to that, I want to know how to tell if Ubuntu is recognizing that I have a USB device attached at all. I'm used to Windows, which normally shows that it detects an unknown USB device, even if it doesn't have a driver. I don't know what behavior to expect from Linux. 

I have installed Ubuntu on 2 computers (12.04 LTS on one, 12.10 on the other), both via the Windows installer. Both PCs have SiS USB controllers (one USB 1.x and the other 2.0). I don't see the MA101 in network settings, but I don't know if that just means there is no usable driver, or if the device is not being detected all. Would appreciate any and all help!

---

### Post by DuckHook on 2012-12-10
> **JHawk56 said:**
> ...I want to know how to tell if Ubuntu is recognizing that I have a USB device attached at all

Do:

```
lsusb
```Your device should show on one of the lines. If more info desired, then note the vendor\product code (the part in hex of the form "xxxx\xxxx") and then do:

```
lsusb -vd xxxx:xxxx
```lsusb is reasonably well-explained (not always the case with Linux commands) on its *man* page:

```
man lsusb
```

---

### Post by Bucky Ball on 2012-12-10
Well, sounds like you have a Wubi install and not a full Ubuntu install to a separate partition. This is not a dual-boot, it is Ubuntu installed in Windows. 

It appears most users here are not that familiar with Wubi and its problems as it is intended for trying Ubuntu before installing and not a permanent solution.

---

### Post by JHawk56 on 2012-12-10
> **duckhook said:**
> do:

```
lsusb
```
OK, my Netgear (not Linksys as I said above) MA101 was detected. Thanks.

> **Bucky Ball said:**
> Well, sounds like you have a Wubi install and not a full Ubuntu install to a separate partition. This is not a dual-boot, it is Ubuntu installed in Windows. 

It appears most users here are not that familiar with Wubi and its problems as it is intended for trying Ubuntu before installing and not a permanent solution.
Thanks. It is dual boot via Guru, and not really installed in Windows. What makes it different from a normal disk installation is that it is installed in a folder in an NTFS partition. In my case, that partition is not the Windows partition.

I would encourage experienced Ubuntu users to assist Wubi users, with the exception of the installation process itself, and add a caveat about not being familiar with Wubi if they want to be careful.

---

### Post by squakie on 2012-12-10
Wasn't aware you could install ubuntu to an ntsf partition.  If the file system is just a file/folder on a ntsf partition that would most probably still be a wubi install, no matter how it was done.

---

### Post by JHawk56 on 2012-12-10
No question it's a Wubi install. The online Windows Installer downloads wubi.exe. As to NTFS, that's one of the the main reasons for Wubi, to avoid the need for and risk of repartitioning. (Although in my case I did reallocate space among my NTSB partitions to make room for the Ubuntu file before the download. MY reasons for going with Wubi were that I don't have a DVD burner and I can't boot from a USB stick.)

But we're going OT... :)

---

### Post by squakie on 2012-12-10
Please post back the output of lsusb.  That way we can see the manufacturer and product id's so we can determine the chipset.  Are you running 32-bit Ubuntu or 64-bit?  Please also post back the output of:

ifconfig

iwconfig

---

### Post by Bucky Ball on 2012-12-10
... and, with the dongle plugged in:

sudo lshw -C network

---

### Post by DuckHook on 2012-12-10
> **Bucky Ball said:**
> It appears most users here are not that familiar with Wubi and its problems as it is intended for trying Ubuntu before installing and not a permanent solution.

+1 Bucky Ball. Certainly applies to me.

> **JHawk56 said:**
> I would encourage experienced Ubuntu users to assist Wubi users, with the exception of the installation process itself, and add a caveat about not being familiar with Wubi if they want to be careful.

...problem is that OSes are such finicky things that the cautious amongst us are guarded for fear of screwing up your system. Also, no experience with nonstandard bootloaders, filesystems, etc. which, by definition, are going to be different (after all, these are Windows and not Linux components), so no knowledge to afford any help.

Re: your wireless usb problem:

I now understand why you posted here. A google/forum search turned up almost nothing useful except the following:

1. the chipset is an atmel_at76c503 or similar (do not merely assume my detective work is correct. You must be sure by following commands from @squakie and @Bucky Ball)

2. support for this chipset has been dropped from kernel at some point in the past.

3. most previous posters could not force an older driver to work in their newer installations. We can still try (personally, I'm cussedly stubborn about trying to make old HW work with Linux), but you may be better off just buying a new USB wireless stick that is supported by the kernel. They are so cheap these days that it may not be worth your time and trouble to wrestle with this one.

If intent on forging ahead, will need the info already requested.

Please post results between the [CODE][\CODE] markers (where \ is replaced with /) for easy readability.

Also, do you still have your Windows drivers? Might have to resort to *ndiswrapper* despite my absolutely hating that kludge.

P.S. relevant results of google search are [COLOR=Red][here]("http://ubuntuforums.org/showthread.php?t=1530642")[/COLOR], [COLOR=Red][here]("http://ubuntuforums.org/showthread.php?t=1530642")[/COLOR] and [COLOR=Red][here]("http://ubuntuforums.org/showthread.php?t=1280956&page=3")[/COLOR].

---

### Post by JHawk56 on 2012-12-10
> **DuckHook said:**
> Re: your wireless usb problem:

I now understand why you posted here. A google/forum search turned up almost nothing useful except the following:

1. the chipset is an atmel_at76c503 or similar (do not merely assume my detective work is correct. You must be sure by following commands from @squakie and @Bucky Ball)

2. support for this chipset has been dropped from kernel at some point in the past.

3. most previous posters could not force an older driver to work in their newer installations. We can still try (personally, I'm cussedly stubborn about trying to make old HW work with Linux), but you may be better off just buying a new USB wireless stick that is supported by the kernel. They are so cheap these days that it may not be worth your time and trouble to wrestle with this one.

If intent on forging ahead, will need the info already requested.

Please post results between the [CODE][\CODE] markers (where \ is replaced with /) for easy readability.

Also, do you still have your Windows drivers? Might have to resort to *ndiswrapper* despite my absolutely hating that kludge.

P.S. relevant results of google search are [COLOR=Red][here]("http://ubuntuforums.org/showthread.php?t=1530642")[/COLOR], [COLOR=Red][here]("http://ubuntuforums.org/showthread.php?t=1530642")[/COLOR] and [COLOR=Red][here]("http://ubuntuforums.org/showthread.php?t=1280956&page=3")[/COLOR].

Yes, I did considerable web searching myself before even choosing a distro, so I knew I might be up against a challenge. The only real encouragement came from [COLOR=Red][here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB")[/COLOR], which says it works out-of-the-box, but in light of everything else I read, I was skeptical.

After my last post and with the help of the wireless troubleshooter in Ubuntu, the article [COLOR=Red][here]("http://atmelwlandriver.sourceforge.net/howto/howto.html")[/COLOR], a look at the Windows driver, and the labeling on the device, I am certain I have the Atmel chip and the RFMD radio. The vid/pid is 0864:4102. The SourceForge article linked above has compilation instructions, but I'd be happy if I could find a pre-compiled download.

I will run/re-run all the commands recommended by all the posters here in case hey reveal anything else helpful, when I am back in Ubuntu. I am posting from Windows now and need to stay there for a few hours. Thanks

---

### Post by DuckHook on 2012-12-10
> **JHawk56 said:**
> ...I'd be happy if I could find a pre-compiled download.

It may not need to come to that, although some Linux users do revert to kernels that run without problems rather than keep trying to push against a rope. In Linux, the equivalent of "drivers" is modules, and we can try a few different ones. No need to hurry. Get back with info when convenient.

---

### Post by squakie on 2012-12-10
the first link bombed on me with some sort of server error, so I'll have to check it again later.  Your second link, however, is from 2003.  I wouldn't put much hope in that unless you can find updated info, instructions, source, etc., that applies to the new kernels.

---

### Post by JHawk56 on 2012-12-11
These were run on the PC that has Ubuntu 12.10
```
lsusb
Bus 002 Device 002: ID 0864:4102 NetGear, Inc. MA101 802.11b Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsusb -vd 0864:4102

Bus 002 Device 002: ID 0864:4102 NetGear, Inc. MA101 802.11b Adapter
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          254 Application Specific Interface
  bDeviceSubClass         1 Device Firmware Update
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0864 NetGear, Inc.
  idProduct          0x4102 MA101 802.11b Adapter
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      0 
      iInterface              0 
      Device Firmware Upgrade Interface Descriptor:
        bLength                             7
        bDescriptorType                    33
        bmAttributes                        1
          Will Not Detach
          Manifestation Intolerant
          Upload Unsupported
          Download Supported
        wDetachTimeout                   1299 milliseconds
        wTransferSize                    1024 bytes
```
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:d0:09:d7:66:35  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63424 (63.4 KB)  TX bytes:63424 (63.4 KB)
```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 90
       serial: 00:d0:09:d7:66:35
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
       resources: irq:22 ioport:d400(size=256) memory:cfffd000-cfffdfff memory:cffc0000-cffdffff
```
Note that the SiS 900 PCI wired network interface (00:d0:09:d7:66:35) was not attached to a network when these commands were run.

@squakie: It's 32-bit Ubuntu.

---

### Post by squakie on 2012-12-11
That is an old wireless b adapter, and it's going to be difficult at best to get it working.  However,  I have an old Trendnet USB wireless adapter that uses the RTL 8187B chipset (Trendnet TEW-424UB).  I plugged it in my 12.10 desktop, did a modprobe to load rtl8187, and it works.  It's also wireless G, so while not nearly as fast as N, it should be considerably faster than B.  If you are in the U.S. I can mail this to you (it would be by the cheapest way available) for nothing and you can have it to use.  I have no need for it now, so rather than it just sitting in a desk drawer gathering dust and taking up space, I'd prefer to just play it forward.  User lkraemer did this with me and a modem I needed, and I've been trying to do it since with any hardware pieces I have that I'm not using (including a 2gb pc3 10600 sodimm and a 1gb pc3 1600 sodimm if anyone needs them and are in the continental US, as well as 2 2gb pc3 10666 desktop dimms if anyone needs them).

So if you're in the U.S. (I just can't ship outside the U.S. - too much of a hassle), PM me and include your address (for obvious security reasons, DO NOT post it here in the public forum) and I'll send it off to you.  (I would assume jhawk would be Kansas, but it could also be something with your name, so I don't want to assume ;) )

---

### Post by JHawk56 on 2012-12-11
> **squakie said:**
> ...I have an old Trendnet USB wireless adapter...I can mail this to youI'll take you up on that; thanks! I'm broke and any money I can save is a plus. It will be nice to have 11g. I had a PCI 11g NIC but it somehow got lost when I moved. We 'puter nuts help each other in numerous ways, and I'm glad to help you "pay if forward." I gave away a perfectly working and reasonably modern printer recently; I guess this is my reward.

PM on the way. ):P

---

### Post by Bucky Ball on 2012-12-11
Good news. Nice gestures people. ;)

---

### Post by JHawk56 on 2012-12-11
I've marked this "solved" since the issue with the MA101 is now moot. Although the problem was not seen to conclusion (because I'll be using a different network interface), I did learn a number of things about Ubuntu along the way, and I thank everyone who contributed.

---

### Post by squakie on 2012-12-11
Yeah, I'm on disability myself so I know the feeling.  About 3 years ago I was in desperate need of an external modem since we only had DSL then and I had to use dial-up since no connection to the DSL from down here, but I couldn't even afford a used one on EBay.  User lkraemer here was so kind and sent me one, so I've just been trying to follow his lead and play it forward!  I hope Larry is an inspiration for others here to do the same thing!

I sent it out today - I would hope it would be there by Saturday.  I remember using it in Windows XP and an older release of Ubuntu, so I tried with Ubuntu 12.10 last night to be sure it would still work - it did.  I don't know if there is a driver for it for Windows 7 or Windows 8, so you may want to keep the other one around in case you need to use it for Windows.

You'll need to:

sudo modprobe rtl8187 <press enter>

to enable the driver.

You should also edit the /etc/modules file and add a new line at the bottom that simply says:

rtl8187

You'll need to do that via sudo gedit or gksudo - either one works fine for that file.

Have a good one! ;)

And BTW - everyone should give a BIG thank you to lkraemer and follow his lead.

I do have 1 2gb and 1 1gb PC3 10600 sodimms for a laptop, and 2 2gb OCZ Gold series  PC3 10666 dimms for a desktop.  These are also free to anyone in need in the U.S..  Please, truely be in need and not just in want.

---

### Post by JHawk56 on 2012-12-12
@squakie:

Financial realities have kept me in AMD Socket A (Athlon XP), a rapidly aging platform, and one reason for my interest in Linux is to keep my machines viable for a while longer. I use XP so the Trendnet unit will do double duty, and I'll keep the MA101 on another machine that I have to keep on Windows for the time being.

I'll let you know by PM when the Trendnet gets here, and start new thread if I have any problems. Thanks again.

---

### Post by squakie on 2012-12-12
> **JHawk56 said:**
> @squakie:

Financial realities have kept me in AMD Socket A (Athlon XP), a rapidly aging platform, and one reason for my interest in Linux is to keep my machines viable for a while longer. I use XP so the Trendnet unit will do double duty, and I'll keep the MA101 on another machine that I have to keep on Windows for the time being.

I'll let you know by PM when the Trendnet gets here, and start new thread if I have any problems. Thanks again.

You may need to download a driver for it for Windows.  I'll take a look here in the "junk" boxes and see if I have a copy of it somewhere.

---

### Post by DuckHook on 2012-12-12
> **JHawk56 said:**
> ...AMD Socket A (Athlon XP), a rapidly aging platform, and one reason for my interest in Linux is to keep my machines viable for a while longer.

If you don't mind my prying, what are your computer specs and what flavour of *buntu are you running? I ask only because there are other flavours and even other distros that may serve you well. For one thing, if either your CPU or motherboard does not support PAE, then don't upgrade to 12.10, as it will only run on PAE-capable systems. Lubuntu 12.04 ran like a charm on an old laptop until I made the mistake of upgrading to 12.10. Now it is wonky even after I've pinned the kernel to disallow further kernel upgrades. If you are happy with the way things are, no need to reply.

---

### Post by JHawk56 on 2012-12-12
> **squakie said:**
> You may need to download a driver for it for Windows.  I'll take a look here in the "junk" boxes and see if I have a copy of it somewhere.Don't dig just yet, thanks. Appears to be downloadable from Trendnet.

> **DuckHook said:**
> If you don't mind my prying, what are your computer specs and what flavour of *buntu are you running? I ask only because there are other flavours and even other distros that may serve you well. For one thing, if either your CPU or motherboard does not support PAE, then don't upgrade to 12.10, as it will only run on PAE-capable systems. Lubuntu 12.04 ran like a charm on an old laptop until I made the mistake of upgrading to 12.10. Now it is wonky even after I've pinned the kernel to disallow further kernel upgrades. If you are happy with the way things are, no need to reply.

Ubuntu 12.10 runs fine (a bit slow) but in case any ideas jump out at you:

ECS K7S5A v3.1 mobo
Athlon XP mobile 2400+ CPU, PAE-compatible
512MB DDR, expandable to 1GB
ABIT Radeon 9550-128CDT AGP card, 128MB

I'm also running Ubuntu 12.04 on:

PCCHIPS M847LU mobo
Athlon XP 2500+
512MB DDR, expandable to 2GB
Xabre 200 video, 64MB

Both overclock nicely, although in the first case some Windows-based software is needed to get the maximum.

I also have, but have never tested, an ABIT NF-7 mobo that will take the above components and has the advantage of being able to handle up to 3GB RAM and SATA drives.

---

### Post by DuckHook on 2012-12-14
All of these units have limited memory, and I don't know if it is worth your while to increase it. The lightest weight *buntu distro is lubuntu. I have it installed on my ancient laptops, and it runs very nicely. Almost makes my creaky equipment feel like new again. There are other distros that are even leaner and many Linuxers swear by them. A recent review is [here]("http://www.tuxradar.com/content/whats-best-lightweight-linux-distro").

---

### Post by Bucky Ball on 2012-12-14
Duckhook is correct, although unfortunate he/she always ends up in the rough ... 

I'd go the minimal install if you want to go completely lean, and add only the apps you use:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

... but now we are getting off topic ... ;)

---

### Post by venik212 on 2012-12-14
I also have a similar problem: A parallel printer (HP LaserJet4100) with a USB-to-parallel adapter (since Ubuntu no longer seem to support parallel devices).  Using hp-setup I get: no usb devices discovered.
lsusb produces:
Bus 003 Device 005: ID 1a86:7584 QinHeng Electronics CH340S
which menas that the system sees the parallel-2-usb adapter, but somehow CUPS, hplip or *add printer* fails to detect it.
What do I do?

---

### Post by JHawk56 on 2012-12-14
> **Bucky Ball said:**
> I'd go the minimal install if you want to go completely lean, and add only the apps you use:

[URL]https://help.ubuntu.com/community/Installation/MinimalCD
> **DuckHook said:**
> All of these units have limited memory, and I don't know if it is worth your while to increase it. The lightest weight *buntu distro is lubuntu. I have it installed on my ancient laptops, and it runs very nicely. Almost makes my creaky equipment feel like new again. There are other distros that are even leaner and many Linuxers swear by them.
The thing about adding memory is it's usually the most effective improvement you can make, and in my case about the only one without a complete platform change. I did research various alternative distros, especially lubuntu and Puppy; went with a full Ubuntu distro because I figured it had the best chance of working with all my hardware out-of-the-box, and would have great community support. That second factor is proving to be particularly true. And on that note...
> **squakie said:**
> I have an old Trendnet USB wireless adapter...I can mail this to you...for nothing and you can have it to use.
It arrived today! Will try it out tonight. Thanks again!

---

### Post by squakie on 2012-12-14
> **venik212 said:**
> I also have a similar problem: A parallel printer (HP LaserJet4100) with a USB-to-parallel adapter (since Ubuntu no longer seem to support parallel devices).  Using hp-setup I get: no usb devices discovered.
lsusb produces:
Bus 003 Device 005: ID 1a86:7584 QinHeng Electronics CH340S
which menas that the system sees the parallel-2-usb adapter, but somehow CUPS, hplip or *add printer* fails to detect it.
What do I do?

A lot of those USB to parallel adapters are hybrids and require a driver to even work as a parallel port in Windows.  The ones I have tried in the past I was never able to get working with Ubuntu.  As far as I know Ubuntu supports parallel printers, but there are some packages or modules you may have to install/load.  I would first try to modprobe parport, then if needed perhaps any of these modules: printconf/libieee1284/libhpmud0.  The module parport is needed in order to reference parallel ports as far as I know.  That particular adapter just might not work - I'll try to look it up.

EDIT:  Just found something else to try * I WOULD TRY THIS FIRST * :

 sudo modprobe -r usblp

If that works we can make it permanent.

---

### Post by squakie on 2012-12-14
> **JHawk56 said:**
> The thing about adding memory is it's usually the most effective improvement you can make, and in my case about the only one without a complete platform change. I did research various alternative distros, especially lubuntu and Puppy; went with a full Ubuntu distro because I figured it had the best chance of working with all my hardware out-of-the-box, and would have great community support. That second factor is proving to be particularly true. And on that note...

It arrived today! Will try it out tonight. Thanks again!

Hey - if you need memory, and if it would work:

1 - 2gb PC3-10600 for laptop
1 -1gb PC3-10600 for laptop

2 - OCZ Gold Series 2gb each PC3-10666 for desktop

Any of the above are free - if you need it and it will work, I'll send you whatever you need.  This goes for anyone else out there as well.

---

### Post by DuckHook on 2012-12-14
> **Bucky Ball said:**
> ...he/she always ends up in the rough ... ;)

<sigh> try "the trees". Displaying my rank ignorance on these forums isn't the only thing reminding me to be humble.:redface:

---

### Post by Bucky Ball on 2012-12-14
Lol. No reference to your Ubuntu prowess, Duckhook. You're very helpful. Referring only to golf. ;)

---

### Post by DuckHook on 2012-12-14
Ya know? The help thing is based purely on a lifetime of rank stupidity and having just enough sense to warn others not to repeat that same stupidity. When it comes to quickness and facility of mind, these young'uns run rings around me without breaking a sweat. Lest I be accused of false modesty: I don't twitter, don't blog, don't chat, don't facebook. Pretty sad, aye?

Re: golf. Awful pastime isn't it? Recommended only for those who get their kicks out of self-inflicted pain and humiliation.

To make some show of being on topic...

@JHawk56

I bought memory for my ancient laptops some months ago. They are so ancient that they go back to DDR1. Not even DDR2 which are also obsolete. Cost me $30/GB. Three modules were $90. They're so expensive because I don't think anyone makes them anymore so anything on the market now comes out of the deep freezer. Just saw a Dell XPS dual core machine w/ 2GB on e-bay for $100. It's almost guaranteed to have a working WIFI chip fully supported in the latest Linux kernel, so your problem is solved there. Of course, it's your choice, but seems to me that it makes more sense to update machines and throw the old ones in the river (don't *do* that, but you know what I mean). Ubuntu 12.04 will run nicely for the next five years on an XPS, whereas you won't be able to run more than two major apps on your current dinosaurs at any one time, and by the time you add up the cost of beefing up the memory, you may be better off with something newer at equivalent cost. Donate the old ones to charity, or run them with a minimal install as routers, servers or tinker-boxes. I use one of mine for a plant stand.

---

### Post by squakie on 2012-12-15
> **DuckHook said:**
> Ya know? The help thing is based purely on a lifetime of rank stupidity and having just enough sense to warn others not to repeat that same stupidity. When it comes to quickness and facility of mind, these young'uns run rings around me without breaking a sweat. Lest I be accused of false modesty: I don't twitter, don't blog, don't chat, don't facebook. Pretty sad, aye?

Re: golf. Awful pastime isn't it? Recommended only for those who get their kicks out of self-inflicted pain and humiliation.

To make some show of being on topic...

@JHawk56

I bought memory for my ancient laptops some months ago. They are so ancient that they go back to DDR1. Not even DDR2 which are also obsolete. Cost me $30/GB. Three modules were $90. They're so expensive because I don't think anyone makes them anymore so anything on the market now comes out of the deep freezer. Just saw a Dell XPS dual core machine w/ 2GB on e-bay for $100. It's almost guaranteed to have a working WIFI chip fully supported in the latest Linux kernel, so your problem is solved there. Of course, it's your choice, but seems to me that it makes more sense to update machines and throw the old ones in the river (don't *do* that, but you know what I mean). Ubuntu 12.04 will run nicely for the next five years on an XPS, whereas you won't be able to run more than two major apps on your current dinosaurs at any one time, and by the time you add up the cost of beefing up the memory, you may be better off with something newer at equivalent cost. Donate the old ones to charity, or run them with a minimal install as routers, servers or tinker-boxes. I use one of mine for a plant stand.

Love the golf game sides.  I'll tell you a "funny" story.  While I was working IT at Todd Pacific Shipyards in San Pedro, CA., in the 1980's, we had an annual golf outing.  I told them to put me in the last 4 some, since I was a TERRIBLE gold player.  Well, even with my handicap (biggest in the outing) I still shot over 200.  I get to work on Monday and the administrative assistant in our section had called everyone together and was making a big deal out of me winning a prize for highest score with handicap.  I quietly explained that this wasn't good - the idea in golf being to shoot a low score.  She quietly said "uh, I'll bet this isn't good, huh?".  Everyone got a good laugh out of it - me, I could never figure out how I could try so hard and something and be just plain terrible at it.  Switch my golf score with my bowling score and I'd have looked good in both games! ;)  I guess not having to "endure" those anymore is the 1 blessing with my disabled back.

BTW - I've got an old Dell 1501 with working wireless in Ubuntu 12.10 - 2gb memory, I think it's some sort of dual-core Sempron.  If you want, it can't be free, but I'd be willing to part with it for $100 also if you'll pay the shipping.

---

### Post by JHawk56 on 2012-12-16
> **squakie said:**
> You'll need to:

sudo modprobe rtl8187 <press enter>

to enable the driver.

You should also edit the /etc/modules file and add a new line at the bottom that simply says:

rtl8187

You'll need to do that via sudo gedit or gksudo - either one works fine for that file.I booted to Ubuntu 12.04 with the Trendnet wireless dongle attached and am up and running without entering any commands. The information in Network Connections looks perfect. I'm using Ubuntu and Firefox to post this. In light of that, is there anything to gain by entering those commands? Or should I leave well enough alone?

---

### Post by DuckHook on 2012-12-16
> **JHawk56 said:**
> ...should I leave well enough alone?

Listen to your instincts. When something works in the crazy world of hardware, kiss it, rub it and make an offering to the gods. It is also permissible to cackle maniacally.

---

### Post by JHawk56 on 2012-12-16
> **DuckHook said:**
>  It is also permissible to cackle maniacally.Duck, you are not only a Linux guru but a mindreader. I was just considering posting to Facebook* "I am up and running on Linux, muahahahahaaaaa!"

* No, I am not one of those young-uns you mentioned, but I play one on the Interweb.

Thanks, everyone!

---

### Post by squakie on 2012-12-16
Nope- no need!  If it works, it works!

Glad it is working for you.  Just remember that if someday in the future if you are able to, play it forward.  ;)

BTW - only a 'frady cat WOULDN'T post that to Facebook! ;)


P.S. - Anybody want the memory I have?  Just trying to give it away and still no takers.

---

### Post by JHawk56 on 2012-12-16
I'd jump all over the memory offer except I'm stuck with DDR1 slots and the aforementioned limits.

I appreciate the various comments about buying a used computer, and agree that's my best option if I can scrape together a few bucks. Right now my upgrade budget is $0. Best I can do with that (non)budget is see if the NF-7 mobo works and fill all 3 slots with sticks I already have, for a great big total of 768MB. Still, a 50% increase.

I'm working on the Dell 1501 idea, though... ;)

---

### Post by JHawk56 on 2012-12-16
> **DuckHook said:**
> Just saw a Dell XPS dual core machine w/ 2GB on e-bay for $100. It's almost guaranteed to have a working WIFI chip fully supported in the latest Linux kernel, so your problem is solved thereDo you have a link?

---

### Post by DuckHook on 2012-12-16
[Here]("http://www.ebay.ca/itm/Dell-XPS-M1710-17-Notebook-1-83-ghz-3gb-Ram-Windows-7-Ultimate-Laptop-Intel-/140897579923?pt=Laptops_Nov05&hash=item20ce267393") and [here]("http://www.ebay.ca/itm/Dell-XPS-M1330-13-3-Notebook-/181046057853?pt=Laptops_Nov05&hash=item2a272f9b7d").

---

### Post by JHawk56 on 2012-12-23
> **DuckHook said:**
> The lightest weight *buntu distro is lubuntu. I have it installed on my ancient laptops, and it runs very nicely. Almost makes my creaky equipment feel like new again. I did install Lubuntu as a second desktop environment, and I'm much happier with it! Thanks!

---

