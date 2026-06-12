---
title: "Dial-Up Internet Help, Ubuntu"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by dowell22 on 2008-11-15
hi,

i'm new to ubuntu, and want to put an internet connection on it, so i can stop using windows.

i use peoplepc (high-speed not offered here) and i don't know really what to do.

when i googled it (for the bigillionth time) i was told to

(using windows)

1)download dial gaurd 1.8.7

2)extract it

3)disconnect from peoplepc

4)reconnect, a think poped up with "my real user name and passoword" and a few other things.
(user name and password were actually more of a 30 long character code)

5)copy the information down

6)restart computer and bring up ubuntu this time

7)put in all your information and your done


but some where i got lost, i need the DNS for peoplepc. dial gaurd didn't give me a DNS.

any help? or maybe a completely different way to do it?

---

### Post by MasterSander on 2008-11-15
You have to enable automatic DHCP configuration, that way peoplepc will tell you your DNS, you can only enter a DNS if you have a static IP

---

### Post by dowell22 on 2008-11-15
what exactly is a static IP?

will that help me get the DNS?

i'm just a beginner, i dont know exactly what i'm doing...

step by step instructions would be nice.

---

### Post by Sealbhach on 2008-11-15
What is the modem peoplepc have provided for you?

Is it a USB modem?

If so, plug it in and open a terminal and copy and paste the results you get from these commands:

```
lsusb
```

```
sudo wvdialconf
```

Static IP means you have one IP address at all times. Dynamic IP means your ISP (peoplepc) assign you a different IP address every time you connect to the internet.


.

---

### Post by dowell22 on 2008-11-15
i'm guess i have a Static IP...

and not a usb modem, phone line connected to back of computer, i'm not sure what that is called.

---

### Post by Sealbhach on 2008-11-15
OK, can you do

```
ifconfig
```

and 

```

lshw -C network
```

and copy and paste the results here.

thanks.

.

---

### Post by dowell22 on 2008-11-15
just to be clear i do that in the terminal?

and, why would i have to enter in the codes?

all i need is the DNS (i think)? will this help?

i'll try...

---

### Post by Sealbhach on 2008-11-15
Oh, Ok. I was thinking your hardware might not be detected.

I just looked at the instructions provided here and it says:
> 
Leave settings for gateways and DNS's as automatic or default, and check dynamic IP adress

[http://www.linuxforums.org/forum/linux-newbie/100801-how-connect-peoplepc-linux-yay.html](http://www.linuxforums.org/forum/linux-newbie/100801-how-connect-peoplepc-linux-yay.html)

So you leave that as automatically selected. Otherwise, you could try the Open DNS addresses:

208.67.222.222
208.67.220.220

.

---

### Post by dowell22 on 2008-11-15
ok, i did what you said anyway... but i forgot the file in ubuntu, :(  sorry, i really don't wanna log back on to get it...

and also, how does it dial? i got all the information...

---

### Post by Sealbhach on 2008-11-15
In that link I posted there, the guy was using kppp. If you're in Kubuntu that's the one to use. If you're using Ubuntu, then you can use gnome-ppp.

It's just a gui which allows you to set up a connection and dial.

You can get it here:

[http://packages.ubuntu.com/intrepid/i386/gnome-ppp/download](http://packages.ubuntu.com/intrepid/i386/gnome-ppp/download)

If you're using 64-bit get the other one. I'm assuming you're using Intrepid.


.

---

### Post by dowell22 on 2008-11-15
no, hardy, 8.04.

intrepid is on the way.

and thanks but there's a bizillion links, which is what i want?

sorry i'm asking so many questions, i just don't like to mess things up

---

### Post by dowell22 on 2008-11-15
never mind the last post,

i got it downloaded now, how do i install it on ubuntu? (never installed any applications yet)

---

### Post by Sealbhach on 2008-11-15
It's a deb file, so you just double click to install, just like an .exe file in windows.

Then you'll find it in the Applications/Internet menu.


.

---

### Post by dowell22 on 2008-11-15
sorry about that, i can be retarded sometimes...

i installed it entered all my information but it says it can connect to modem...

the same thing that you originally posted

i followed your intructions... but nothing happened...


this is what the terminal says (after gnome-ppp installed):

dowell@dowell-desktop:~$ ifconfigand
bash: ifconfigand: command not found
dowell@dowell-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:13:d4:b9:e1:7f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
dowell@dowell-desktop:~$ 




i also got this when i clicked connect:

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory



...where do i get a modem driver for ubuntu?

---

### Post by dowell22 on 2008-11-15
this is my modem:

PCI Data Fax SoftModem with SmartCP (COM3)

---

### Post by Sealbhach on 2008-11-15
Type 

```
sudo wvdialconf
```

in the terminal and paste the output of it here.


.

---

### Post by dowell22 on 2008-11-15
dowell@dowell-desktop:~$ sudo wvdialconf
[sudo] password for dowell: 




i won't let me type after that...

---

### Post by Sealbhach on 2008-11-15
> **dowell22 said:**
> dowell@dowell-desktop:~$ sudo wvdialconf
[sudo] password for dowell: 




i won't let me type after that...

Just put in your password.

Also, while you're in the terminal, give the command "lspci" as well. After you've done this one.


.

---

### Post by dowell22 on 2008-11-15
i won't let me type my password...it's weird... idk

i type in "sudo wvdialconf"... 

[sudo] password for dowell:"

i try to type and it won't let me... i'll try again..

---

### Post by Sealbhach on 2008-11-15
Weird...

Just do wvidalconf then.


.

---

### Post by dowell22 on 2008-11-15
i tried a couple more times... the last time i tried it didn't ask for my password... idk...

it just went.. i saved the file, but then ubuntu froze for some reason and it didn't save to my flash drive...

but it said couldn't detect modem...

---

### Post by dowell22 on 2008-11-15
it's getting on my nerves... ubuntu keeps freezing on me

---

### Post by dowell22 on 2008-11-15
PeoplePC with Ubuntu, (dial up) 



i use people pc. (high speed isn't an option)

and i need to use it with Ubuntu 8.04.

i already installed gnome-ppp.

all my info is in there. it just doesn't detect the modem...

can anyone help me find a driver for my modem?

if it help the modem is, "PCI Data Fax SoftModem with SmartCP (COM3)"

and it's not a USB modem.

it uses a phone cord and a phone cord only. and plugs directly into the phone jack.

---

### Post by Sealbhach on 2008-11-15
Please put

```
lspci -vv
```

in the terminal and paste the output here.

We need more information on this modem. If it's a PCI modem it may not work at all, but some PCI modems do. 


.

---

### Post by Bartender on 2008-11-15
Well, my firend, you have two problems.
One, PeoplePC (PPC) is a crappy ISP for Linux.  Remember all those programs you had to load onto your Windows PC to make PPC work?  PPC requires propietary software in order to connect.

First, dump PPC and go with some other ISP that does not require any proprietary software.  

Second, your internal modem is almost certainly not going to work.  Internal dial-up winmodems get no love in Linux.  Nobody's bothering to reverse-engineer the Windows-based drivers.  There are two good external modems you can buy - USR serial modem or the old AOL/Actiontec serial/USB models.

See this thread 
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)
for further directions

Even if you get dial-up working, Ubuntu updates are a killer.  In the last year I've gotten several 30MB updates.  One was 90+MB! Not fun on dial-up.

The ultimate solution to dial-up?  Get a Centrino laptop.  Install Ubuntu.  Go into town and find a wireless hotspot.  I'm not kidding.  Ubuntu on dial-up is that bad.

---

### Post by dowell22 on 2008-11-15
i think i'm just gonna get a hard modem... sounds simpler... and not so much codes and stuff that i don't understand...

since walmart has everything... is this a good modem?

[http://www.walmart.com/catalog/product.do?product_id=10073738](http://www.walmart.com/catalog/product.do?product_id=10073738)

---

### Post by cek on 2008-11-15
> **dowell22 said:**
> i think i'm just gonna get a hard modem... sounds simpler... and not so much codes and stuff that i don't understand...

since walmart has everything... is this a good modem?

[http://www.walmart.com/catalog/product.do?product_id=10073738](http://www.walmart.com/catalog/product.do?product_id=10073738)

Yes that is a good modem, even though it is USB it is a full hardware modem.  It will be detected as /dev/ttyACM0 (or similar)

---

### Post by Mardoct909 on 2008-11-15
I'd really recommend a real computer store with people that actually know what there doing for your purchase. Often cheaper there, too.

---

### Post by dowell22 on 2008-11-15
sadly, i can't dump peoplepc, it's just not an option... i would if i could tho.

when i entered in

```
lspci -vv
```

into the ubuntu terminal, this was the output:

```
dowell@dowell-desktop:~$ lspci -vv
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 32
	Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: ed000000-ed0fffff
	Prefetchable memory behind bridge: e0000000-e7ffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 128
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 4000 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: Hewlett-Packard Company Unknown device 2a05
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (13000ns min, 2750ns max)
	Interrupt: pin C routed to IRQ 23
	Region 0: I/O ports at a000 [size=256]
	Region 1: I/O ports at a400 [size=128]
	Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at ed113000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 18
	Region 0: Memory at ed114000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 19
	Region 0: Memory at ed110000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (20000ns max)
	Interrupt: pin D routed to IRQ 21
	Region 0: Memory at ed111000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (13000ns min, 2750ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at a800 [size=256]
	Region 1: Memory at ed112000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at ac00 [size=8]
	Region 1: I/O ports at b000 [size=4]
	Region 2: I/O ports at b400 [size=8]
	Region 3: I/O ports at b800 [size=4]
	Region 4: I/O ports at bc00 [size=16]
	Region 5: I/O ports at c000 [size=128]
	Capabilities: <access denied>

00:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
	Subsystem: Conexant Unknown device 200c
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at ed100000 (32-bit, non-prefetchable) [size=64K]
	Region 1: I/O ports at c400 [size=8]
	Capabilities: <access denied>

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a04
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at ed115000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at c800 [size=128]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 2a06
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 5
	BIST result: 00
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at ed000000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at 9000 [size=128]
	Capabilities: <access denied>
```



yeah i know... huge...




and which ubuntu installation is better?

the "install in side windows"?

or

the "disk partition"?

---

### Post by Sealbhach on 2008-11-16
It tells us a little more information:

```


Communication controller: Conexant HSF 56k Data/Fax Modem
```


A quick Google of this information: searching for "ubuntuforums +  Conexant HSF 56k Data/Fax Modem" brings us up this information:

[http://archives.linmodems.org/27580](http://archives.linmodems.org/27580)

> The hsfmodem package serves a great variety of Conexant chipset modems. 
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem_VersionSpec_k2.6.20_15_generic_ubuntu_i386.deb.zip 
                           with 2.6.20_15_generic equivalent to 2.6.20-15-generic, your kernel version.
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

And also this information which might be useful:

[http://linux.dell.com/wiki/index.php/Tech/Modems](http://linux.dell.com/wiki/index.php/Tech/Modems)

So the driver you need is "hsfmodem".

This link shows where you can get the drivers:

[http://ubuntuforums.org/showthread.php?t=492416](http://ubuntuforums.org/showthread.php?t=492416)

I hope this helps and that someone else who has got this modem working will be able to walk you through it.


.

---

### Post by Bartender on 2008-11-17
That tiny USR USB external is cuter than a button!  Has anyone tried it out?  If I didn't already have two big old USR serial externals I'd spend the money just to see if it worked!
Some favorable reviews on USR website...
[http://www.usr.com/products/modem/modem-product.asp?type=media&sku=USR5637](http://www.usr.com/products/modem/modem-product.asp?type=media&sku=USR5637)

And Sealbach is on to something.  If you have the same internal winmodem as Dell uses in their Ubuntu desktops you can try their drivers.

---

