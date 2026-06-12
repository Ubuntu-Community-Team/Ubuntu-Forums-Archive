---
title: "Can connect to internet via ethernet, but not wirelessly..."
date: 2008-08-31
forum: New to Ubuntu
---

### Post by -spy on 2008-08-31
I can get online by using my ethernet cable between the laptop and router, but have absolutely no idea how to get on wirelessly. (wireless works with Vista on same computer) On the Network connections box it doesn't even show a wireless connection option.

help, not too computer savvy btw, sorry:(

here is the laptop i have [http://support.gateway.com/s/Mobile/2007/Tempest/1014770R/1014770Rsp2.shtml](http://support.gateway.com/s/Mobile/2007/Tempest/1014770R/1014770Rsp2.shtml)

In this box I do not see the top option..[IMG]http://beginlinux.com/images/ubgutsy/wireless/w8.png[/IMG]

---

### Post by falcon61102 on 2008-08-31
There should be an icon in the upper right corner of your desktop that looks like two black monitors, one in front of the other.  That's the network manager.  If you click on that, do any wireless networks show up?

Also, could you go into your terminal and post the results of the following command:
```
lshw -C network
```

---

### Post by -spy on 2008-08-31
> **falcon61102 said:**
> There should be an icon in the upper right corner of your desktop that looks like two black monitors, one in front of the other.  That's the network manager.  If you click on that, do any wireless networks show up?

Also, could you go into your terminal and post the results of the following command:
```
lshw -C network
```

When I click the two black monitors it only shows wired connections, no wireless.

Here are the results from the terminal:

"name"s-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:50:80:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.107 latency=0 module=r8169 multicast=yes

---

### Post by -spy on 2008-08-31
^^bump

---

### Post by halitech on 2008-08-31
looking at the screenshot you posted, it looks like you have a wireless connection to a router with the SSID of cydo.

open a terminal and post back the information from 
```
ifconfig
```

---

### Post by falcon61102 on 2008-08-31
By the looks of it, it looks like you need to install the drivers for your wireless card.

Have you check in Hardware Drivers in the System>Administration menu to see if you have all the restricted drivers enabled?  If you open that and nothing shows up, then you don't have any so don't worry about it.

If there are no restricted drivers to be enabled then you probably are going to have to download some and install them manually.  Shouldn't be a problem, just need to get the right ones.

---

### Post by falcon61102 on 2008-08-31
I don't think that's actually a screenshot from his computer.

---

### Post by halitech on 2008-08-31
> **falcon61102 said:**
> I don't think that's actually a screenshot from his computer.

d'oh, never thought to look at the properties of the pic and I think you are right, its from beginlinux.com so doubtful its his.

probably an lspci would help out as well if its an internal card.

---

### Post by falcon61102 on 2008-08-31
Yeah, I was just thinking that might help us in finding the right driver.

If you could post the results of:
```
lspci -v
```

If you want, you can just post the ones dealing with your network card but if you can't pick them out, just post the whole thing.

EDIT:
Or you could use:
```
lspci -nn
```

---

### Post by -spy on 2008-08-31
> **falcon61102 said:**
> Yeah, I was just thinking that might help us in finding the right driver.

If you could post the results of:
```
lspci -v
```

If you want, you can just post the ones dealing with your network card but if you can't pick them out, just post the whole thing.

EDIT:
Or you could use:
```
lspci -nn
```



**Here is the lspci -v :**

lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: ATI Technologies Inc Unknown device 1234
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: cfd00000-cfefffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
	Memory behind bridge: f0200000-f02fffff
	Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0e, subordinate=13, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0300000-f03fffff
	Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
	Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8440 [size=8]
	I/O ports at 8434 [size=4]
	I/O ports at 8438 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8400 [size=16]
	Memory at f0409000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0404000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0405000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0406000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0407000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0408000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0409400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: 66MHz, medium devsel
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8420 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=14, subordinate=19, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller])
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, fast devsel, latency 64, IRQ 255
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at cfdf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 9000 [size=256]
	Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
	Subsystem: ATI Technologies Inc Radeon X1200 Series Audio Controller
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at cfdec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
	Subsystem: Marvell Technology Group Ltd. Unknown device 2a08
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
	Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 0566
	Flags: bus master, fast devsel, latency 0, IRQ 508
	I/O ports at a000 [size=256]
	Memory at f0300000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>


**and here is the lspci -nn :**

 lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
01:05.2 Audio device [0403]: ATI Technologies Inc Radeon X1200 Series Audio Controller [1002:7919]
08:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a08] (rev 03)
0e:00.0 Ethernet controller [0200]: Realtek Semiconduc

---

### Post by halitech on 2008-08-31
```
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
Subsystem: Marvell Technology Group Ltd. Unknown device 2a08
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
```

looks like they had luck here: [http://ubuntuforums.org/archive/index.php/t-575785.html](http://ubuntuforums.org/archive/index.php/t-575785.html)

---

### Post by -spy on 2008-08-31
> **halitech said:**
> ```
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
Subsystem: Marvell Technology Group Ltd. Unknown device 2a08
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
```

looks like they had luck here: [http://ubuntuforums.org/archive/index.php/t-575785.html](http://ubuntuforums.org/archive/index.php/t-575785.html)

sorry, but I dont get what they are saying to do..

and is GNOME terminal the same as the terminal I have been using to to the lspci stuff?

---

### Post by halitech on 2008-08-31
yes, Gnome terminal and terminal are the same thing.

basically you will need the windows driver to get your wireless card working. Do you have the cd that came with the computer? if not we will need to download the file from the net

---

### Post by -spy on 2008-08-31
> **halitech said:**
> yes, Gnome terminal and terminal are the same thing.

basically you will need the windows driver to get your wireless card working. Do you have the cd that came with the computer? if not we will need to download the file from the net

nope, the only CD I have is the Vista re-install cd.

---

### Post by halitech on 2008-08-31
the drivers should be on there *somewhere* but no idea where, will see if I can find a download for you

Edit: found the download file:[http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip](http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip)

---

### Post by falcon61102 on 2008-08-31
Your best bet for the drivers may be to go to Gateway's website and download them there, just be sure to download the WinXP drivers.  That way you know you get the correct ones for your card.

---

### Post by -spy on 2008-08-31
> **halitech said:**
> the drivers should be on there *somewhere* but no idea where, will see if I can find a download for you

Edit: found the download file:[http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip](http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip)

thanks, downloaded it but a box with two white boxes within it comes up and i dont know what to do.. I'm used to windows. :(

---

### Post by halitech on 2008-08-31
> **-spy said:**
> thanks, downloaded it but a box with two white boxes within it comes up and i dont know what to do.. I'm used to windows. :(

huh? can you explain this a little better or take a screenshot and post it

---

### Post by falcon61102 on 2008-08-31
If you right click on it, you should see a option for Extract Here.  Click that and it will create a folder and extract all the files into that folder.  Then we can use those extracted files to install your drivers with.

---

### Post by -spy on 2008-08-31
> **falcon61102 said:**
> If you right click on it, you should see a option for Extract Here.  Click that and it will create a folder and extract all the files into that folder.  Then we can use those extracted files to install your drivers with.

ok, I *think* I did that right, maybe not. It displayed a box titled "File Browser" with the wn511t icon in it (a purple diamond w/ gears), but when I click it I get "Couldn't display "/home/myname/wn511t_3_0_setup.exe" and "there is no application installed for this file type"..

---

### Post by halitech on 2008-08-31
ok, you have the file downloaded then. right click that file and select extract here and you should get a folder showing up with the same name but without the .exe

---

### Post by falcon61102 on 2008-08-31
If you right click on that, does it give you the option to Extract Here?  Let's hope it's a self-extracting archive and not an actual install program.

---

### Post by -spy on 2008-08-31
Here are some screenshots:

[http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot.png](http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot.png)

[http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot-2.png](http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot-2.png)

[http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot-1.png](http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot-1.png)

If you need a screenshot of something more specific let me know.

---

### Post by halitech on 2008-08-31
instead of double clicking, right click the file you downloaded and it should have in the menu, an option to extract here

---

### Post by falcon61102 on 2008-08-31
Ok, try this.  Check out Post #15 on this thread and download that zip file.  That has the files you need in it without all the other stuff.

[http://ubuntuforums.org/showthread.php?t=575785&highlight=TOPDOG+PCI+802.11n&page=2](http://ubuntuforums.org/showthread.php?t=575785&highlight=TOPDOG+PCI+802.11n&page=2)

---

### Post by -spy on 2008-08-31
> **falcon61102 said:**
> Ok, try this.  Check out Post #15 on this thread and download that zip file.  That has the files you need in it without all the other stuff.

[http://ubuntuforums.org/showthread.php?t=575785&highlight=TOPDOG+PCI+802.11n&page=2](http://ubuntuforums.org/showthread.php?t=575785&highlight=TOPDOG+PCI+802.11n&page=2)

k did that but I still cannot open or extract it, it's like the problem i was having with the other file.

**I get to here**

[IMG]http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot-5.png[/IMG]

**Then when I right click it and "extract" i get.**..

[IMG]http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot-6.png[/IMG]


sorry I'm causing so much trouble, thanks for the help..

---

### Post by halitech on 2008-08-31
ok, click on extract

---

### Post by -spy on 2008-08-31
> **halitech said:**
> ok, click on extract
 Clicked extract and get box titled 'file browser' with the NetMW14.inf icon, when I lick that it's a page with text on it. 

Edit: Heres some screens..

W**hen i click extract..**.

[IMG]http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot-11.png[/IMG]

**when I click that NetwMW...**

[IMG]http://i136.photobucket.com/albums/q198/TEXASJCJ/Screenshot12-1.png[/IMG]

can you guys see those?

---

### Post by falcon61102 on 2008-08-31
Don't worry about actually opening those files like you did, just remember where you put them.

Now you need to install ndiswrapper.  Insert your LiveCD (installation CD) and go to System>Administration>Synaptic Package Manager.  Once the package manager loads go to Edit>Add CD... Follow the prompts to add your Cd to the repositories list and then click ok.  Now search for ndiswrapper.  Make sure you install the ndiswrapper-common and the ndiswrapper-utils-1.9.

Now that you've got ndiswrapper installed you need to install your drivers.  

EDIT:  Actually, looking at your screen shots, you shouldn't have to cd anywhere, just start the terminal and run the commands below.

```
sudo ndiswrapper -i NetMW14x.inf
sudo demod -a
sudo modprobe ndiswrapper
```

If you get any errors post them, otherwise go back to your network manager in the upper right hand corner of your desktop and see if you can see any wireless access points.

---

### Post by -spy on 2008-09-05
^^^ I'm back, but none of those commands where found... 

The CD I installed with was an iso file download and burn.

---

### Post by falcon61102 on 2008-09-05
Yeah, that's the CD that you should be using.  Use that and go to the Synaptic Package Manager.  Under the Edit menu you'll see Add CDROM... Go through the menus and then search for ndiswrapper.  Three results should come up; install all three.  Once that's complete go to System>Administration>Windows Wireless Drivers.

This is the GUI version of ndiswrapper.
Once that loads, import your new drivers and go through the install process there and you should be good.

---

### Post by -spy on 2008-09-05
:mad:, I forgot that I culdnt get the CD to download correctly so I had to directly download ubuntu from here [http://wubi-installer.org/](http://wubi-installer.org/)

sorry.

---

### Post by falcon61102 on 2008-09-05
Can you still connect via ethernet?

---

### Post by -spy on 2008-09-05
> **falcon61102 said:**
> Can you still connect via ethernet?

yes, if I unplug it I cannot though, and no wireless icon of any type ever shows up, I'm plugging it into the router btw.

---

### Post by falcon61102 on 2008-09-05
Yeah, if you can connect right now with a cable, you can download the packages that you need to install ndiswrapper.  Once you are connected, go back to Synaptic Package Manager and hit the reload button.  A menu box should come up and say that it's downloading some files.  Those are just the lists of the available packages.  Let that run and when it's finished, then search for ndiswrapper and install all three packages.

---

### Post by -spy on 2008-09-10
After downloading and using the Synpac manager for these...

ndisgtk                  0.8.3-1
ndiswrapper-common       1.50-lubuntul
ndiswrapper-utils-1.9    1.50-lubuntul

and clicking 'reload'...

I did the Terminal codes for the drivers... and got this

:~$ sudo ndiswrapper NetMW14x.inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
mynamees-laptop:~$ sudo demod -a
sudo: demod: command not found
myname-laptop:~$ sudo demod ndiswrapper
sudo: demod: command not found


No wireless Icon is showing up...:(

---

### Post by falcon61102 on 2008-09-10
The driver did not install.  Use the following command to install the driver:
```
sudo ndiswrapper -i NetMW14x.inf
```
Make sure you have the -i in there.

Then go through and run the other commands.

Also, it's:
```
sudo depmod -a
```

Try to watch the typos when your using these codes.  If you get an error and you think something is up, check the typing and try it again.

---

### Post by -spy on 2008-09-10
> **falcon61102 said:**
> The driver did not install.  Use the following command to install the driver:
```
sudo ndiswrapper -i NetMW14x.inf
```
Make sure you have the -i in there.

Then go through and run the other commands.

Also, it's:
```
sudo depmod -a
```

Try to watch the typos when your using these codes.  If you get an error and you think something is up, check the typing and try it again.

I get this:

MyNames-laptop:~$ sudo ndiswrapper -i NetMW14x.inf
[sudo] password for MyName: 
driver netmw14x is already installed
MyName-laptop:~$ sudo depmod -a
MyName-laptop:~$ sudo modprobe ndiswrapper
MyNames-laptop:~$

---

### Post by falcon61102 on 2008-09-10
What's the output of:
```
sudo lshw -C network
```

---

### Post by -spy on 2008-09-10
> **falcon61102 said:**
> What's the output of:
```
sudo lshw -C network
```

s-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:50:80:8c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.107 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

---

### Post by falcon61102 on 2008-09-10
It looks like you need to force ndiswrapper to use that driver for your card.  First we need to get your device Id which you can get with:
```
sudo lspci -nn
```

Post the output of that.

---

### Post by -spy on 2008-09-10
> **falcon61102 said:**
> It looks like you need to force ndiswrapper to use that driver for your card.  First we need to get your device Id which you can get with:
```
sudo lspci -nn
```

Post the output of that.

-laptop:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
01:05.2 Audio device [0403]: ATI Technologies Inc Radeon X1200 Series Audio Controller [1002:7919]
08:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a08] (rev 03)
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)

---

### Post by falcon61102 on 2008-09-10
Alright, now to force ndiswrapper to use the driver:
```
sudo ndiswrapper -i NetMW14x.inf
sudo ndiswrapper -a 11ab:2a08 netmw14x
```

Once that is complete, the driver should be installed.  Check your network manager in the upper right hand corner of your desktop for wireless access points.  If you can connect, great.  If not, post the results of:
```
sudo ndiswrapper -l
sudo lshw -C network
```
-l is a lower case L in the first command.

---

### Post by -spy on 2008-09-10
> **falcon61102 said:**
> Alright, now to force ndiswrapper to use the driver:
```
sudo ndiswrapper -i NetMW14x.inf
sudo ndiswrapper -a 11ab:2a08 netmw14x
```

Once that is complete, the driver should be installed.  Check your network manager in the upper right hand corner of your desktop for wireless access points.  If you can connect, great.  If not, post the results of:
```
sudo ndiswrapper -l
sudo lshw -C network
```
-l is a lower case L in the first command.

Doing the first two codes in the terminal gets me this(but no wireless icon)

MyName-laptop:~$ sudo ndiswrapper -i NetMW14x.inf
driver netmw14x is already installed
MyName-laptop:~$ sudo ndiswrapper -a llab : 2a08 netmw14x
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card


Is that whats supposed to come up or should I go ahead and do..

sudo ndiswrapper -l
sudo lshw -C network

---

### Post by falcon61102 on 2008-09-10
No, the second command didn't run right.  Try copying and pasting the command I posted into your terminal because I think you typed it wrong.

---

### Post by -spy on 2008-09-10
> **falcon61102 said:**
> No, the second command didn't run right.  Try copying and pasting the command I posted into your terminal because I think you typed it wrong.

Copy pasted it and got this:

MyName-laptop:~$ sudo ndiswrapper -i NetMW14x.inf
driver netmw14x is already installed
MyName-laptop:~$ sudo ndiswrapper -a 11ab:2a08 netmw14x
WARNING: Driver 'netmw14x' will be used for '11AB:2A08'
This is safe _only_ if driver netmw14x is meant for chip in device 11AB:2A08
s@j-laptop:~$

---

### Post by falcon61102 on 2008-09-10
Ok, it should be installed now.  Check your Network Manager to see if you can view the wireless access points.  If not, run the other two commands from above and post the results.

---

### Post by -spy on 2008-09-10
> **falcon61102 said:**
> Ok, it should be installed now.  Check your Network Manager to see if you can view the wireless access points.  If not, run the other two commands from above and post the results.

Still no Wireless access points just "wired connection" and "point to point connections"

MyName:~$ sudo ndiswrapper -i NetMW14x.inf
driver netmw14x is already installed
MyNamelaptop:~$ sudo ndiswrapper -a 11ab:2a08 netmw14x
WARNING: Driver 'netmw14x' will be used for '11AB:2A08'
This is safe _only_ if driver netmw14x is meant for chip in device 11AB:2A08
jacejones@jacejones-laptop:~$ sudo ndiswrapper -l
netmw14x : invalid driver!
MyName-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:50:80:8c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.107 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

---

### Post by falcon61102 on 2008-09-10
Ok, it seems that you need to copy and rename a file to get this to work.  Open up the folder that you extracted all these files to.  
You should find a file named: NetMW145.sys 
Copy and rename the file: NetMW146.sys

Once you do that, uninstall the old driver with:
```
sudo ndiswrapper -r NetMW14x.inf
```
If it gives you an error about not being installed, just continue.

Then go back and reinstall it with:
```
sudo ndiswrapper -i NetMW14x.inf
sudo ndiswrapper -a 11ab:2a08 netmw14x
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
```

At the end of that, if you run:
```
sudo ndiswrapper -l
```
You should see a series of code and in there it should say Driver Installed.

---

### Post by duffyatkinson on 2008-09-10
I have had the same problem. I can't believe that I am the first DELL Inspiron owner with this problem.

I've worked this problem from every angle and nothing has worked. Ndiswrapper from every direction. Downloading Wicd. Installing the backport modules. Following the "Comprehensive ndiswrapper troubleshooting guide". Trying to get WinXP drivers to load. Nothing has worked to get wireless to even show up in a network manager, much less work. It shouldn't be this hard. :(

I'm not getting a very warm feeling about Ubuntu my friends. I decided to try it out and installed it into a dual-boot configuration on my DELL Inspiron 1520 with the Intel/PRO Wireless 3945ABG internal card (which works perfect in Vista). Thinking about blowing it out and recapturing the drive space for my perfectly-running Vista install.

So frustrated....  :confused:

I DID manage to get my bluetooth mouse to work though.

I'd like to learn to work in this OS. Can ANYONE help solve this in a STEP-BY-STEP instructional manner (not just a series of forum exchanges with random terminal code to execute the same commands over and over again)????

---

### Post by falcon61102 on 2008-09-10
You're not the only/first person to have a problem with a Dell Inspiron, there are lots of them here.  

Also, Ubuntu is not windows and sometimes it takes a little bit to get something working but the biggest piece of advice I can give you for that is have patience.

There are plenty of people here that are willing and able to help you with your problem, but you're going to have to work with us and that's going to include running some terminal commands.

My first suggestion, if you haven't already done so, is to open a new thread here in the forum with your problem.  This will allow it to come to the attention of many more people.  If you do that, post back here and give us a link so that anyone reading this one can follow you over to your new one and help you there.  When you start the new thread, be descriptive about your problem and it wouldn't hurt to include the results of the following commands in your post:
```
sudo lspci -nn
```
and
```
sudo lshw -C network
```

That will give everyone a better idea of what they are walking into.  Good luck and have patience.

---

### Post by duffyatkinson on 2008-09-10
Thanks Falcon. I'll do that.

I was just hesitant to reintroduce the same issue that seems to be pretty prevalent. Was wondering if I just hadn't searched enough for the answer.

I've been working on getting the wireless connection for over a week, so that's where the little impatience comes from!

I'll keep my fingers crossed!

Thanks again.

---

### Post by falcon61102 on 2008-09-10
No problem.  Don't be hesitant when you searched and tried to get things working and haven't been able to.

---

