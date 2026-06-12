---
title: "[SOLVED] What network card do I have?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Pirkiz on 2008-10-28
Hiya folks!
I just installed Xubuntu (never used Linux before) and my wireless network/internet doesn't seem to work. I suspect that I need to install a driver for my network card. The thing is I don't know how to determine what network card I have. Doesn't Xubuntu have anything like the Windows Device Manager? I've googled it and looked all over this forum and in the Xubuntu help files, but I can't find any answers. So I'm hoping someone here can help me.
How do I determine what network card I have?

---

### Post by spiderbatdad on 2008-10-28
There are several ways to list your hardware. Some of the most popular:
```
lspci
sudo lshw -C net
```either of those should list your network card. Could you also post the results of some other commands from your terminal?
```
iwconfig
nestat -r
```

---

### Post by Pirkiz on 2008-10-28
Okay so I tried the first of those commands, and this is what it tells me:

"pirkiz@Pirkiz:~$ sudo lshw -C net
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:60:fe:63
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s"

(I know, sorry 'bout the uglyness, I wouldv'e wrapped that in code-tags but none of the tags seem to be working, possibly because of really badly updated software or something, using my mom's laptop since I don't have any internet of my own...)

Anyway, I really don't know what much about computers in general, and especially not Linux, so I'm still kinda lost. Could use some help on how to find a driver for that.

---

### Post by spiderbatdad on 2008-10-28
so that is a wired ethernet card, not a wireless card. Do you believe you have a wireless card? Is it a pcmcia removable card?

This ethernet card requires a cable of course...does it work for for you? There was an old issue with this card that required editing the /etc/network/interfaces file to configure the card to use dhcp. Running ```
man interfaces
```might help to explain more. Please post again if you have more questions.

I have not tried this...but looking at the man pages, suggests, to me, adding "iface eth0 inet dhcp"
To edit the file you must launch an editor as root, or superuser:
```
gksu gedit /etc/network/interfaces
```

---

### Post by Iowan on 2008-10-28
FYI, if you have Java and/or JavaScript disabled, the tags won't work.  I disable them to keep "odd" things from happening on some sites I frequent, then remember "the hard way" when I try to post here.

---

### Post by Pirkiz on 2008-10-29
Oops, wrong card indeed, my bad. This one (with cable) is working fine. But I know for a fact that I also have a wireless card, and it worked perfectly fine with Windows Vista. So how do I determine what my wireless card is called (and what driver I need for it)?
Tried "man interfaces", did not understand a thing. As I said, I don't know a whole lot about computers and when it comes to Linux I'm totally *totally* lost. Please help. :cry:

---

### Post by ugm6hr on 2008-10-29
> **Pirkiz said:**
> Oops, wrong card indeed, my bad. This one (with cable) is working fine. But I know for a fact that I also have a wireless card, and it worked perfectly fine with Windows Vista. So how do I determine what my wireless card is called (and what driver I need for it)?
Tried "man interfaces", did not understand a thing. As I said, I don't know a whole lot about computers and when it comes to Linux I'm totally *totally* lost. Please help. :cry:

Have a read through this: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

Although, if **lshw** does not "find" your wifi device, it must be turned off or disabled at BIOS.  Check that first.  Presumably Vista also "power saves" your network card off (as XP did) - that might be worth checking too.

---

### Post by Pirkiz on 2008-10-29
> **ugm6hr said:**
> Although, if **lshw** does not "find" your wifi device, it must be turned off or disabled at BIOS.  Check that first.  Presumably Vista also "power saves" your network card off (as XP did) - that might be worth checking too.

How do I check those things? :confused:
Btw, if it matters, I don't have Vista anymore, did a clean Xubuntu install.

The **lshw** command only showed my other (not wireless) network card. :-s

Also, this may help:
```
pirkiz@Pirkiz:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
pirkiz@Pirkiz:~$ lsusb
Bus 005 Device 003: ID 0bf8:100f Fujitsu Siemens Computers 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04f3:0210 Elan Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000
```

...I didn't really understand any of that, but most people here probably do.

---

### Post by ugm6hr on 2008-10-29
No wifi card on lspci either.

Presumably it is an internal wifi card (or USB)?  Is yours a laptop or desktop?  And which model?

If it worked with Vista, then it is unlikely to be turned off at BIOS.  Is there a light to indicate functioning of wifi (e.g. on front of laptop)?  Do you have an external switch to activate?

I have a feeling that this may be relevant: [http://ubuntuforums.org/showthread.php?t=659416](http://ubuntuforums.org/showthread.php?t=659416)

And perhaps this: [http://uprize.no/index.php](http://uprize.no/index.php)

---

### Post by Pirkiz on 2008-10-30
Yea, it's a laptop (Fujitsu Siemens Amilo Li 1818), so I'm guessing it's internal. The laptop has a WLAN-switch on it, which is set to "on" and the light indicates that it should be working.

The first thing I did was get ndiswrapper, then I downloaded and installed the appropriate driver from the Fujitsu Siemens site (it's called SiS163u) but it doesn't seem to work so I figured maybe there's another driver for my wireless card that works better (actually no I did not figure that, a friend told me), guess maybe that's not the problem after all.

**iwconfig** gives me:
lo        no wireless extensions.

eth0      no wireless extensions.

**ndiswrapper -l** gives me:
sis163u : driver installed
	device (0BF8:100F) present

and **lsusb** gives me:
Bus 005 Device 003: ID 0bf8:100f Fujitsu Siemens Computers 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04f3:0210 Elan Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000


In other words, I seem to be having the exact same problem as the guy ugm6hr linked to ([http://ubuntuforums.org/showthread.php?t=659416](http://ubuntuforums.org/showthread.php?t=659416)). I tried everything mentioned in that thread, I already switched off the encryption and I know our router sends its ssid (I also know the ssid). The one thing I can think of is, in that thread something about dhcp was mentioned. **I don't know whether our router is set to dhcp or not, is there any way to check this without having the password for the router?** Otherwise I'll just ask my dad in the morning, he has the password but he's currently asleep. Do you think this might be the problem?

---

### Post by Pirkiz on 2008-10-31
**[COLOR=Red]Nevermind, problem solved![/COLOR]**

Upgraded to Xubuntu 8.10 (from 8.04), and after installing ndiswrapper and the appropriate driver (same as before) it's working just fine. :D

Thanks anyway for the help!

---

### Post by ugm6hr on 2008-10-31
Glad the new release worked it's magic for you!

Out of interest, your "internal" wifi card on that laptop is one of a new generation of internal USB wifi cards in some laptops.  Hence why lspci doesn't find it, but lsusb does.
 
Unfortunately, USB cards are not well supported on Linux / Ubuntu - but glad yours works OK.

---

