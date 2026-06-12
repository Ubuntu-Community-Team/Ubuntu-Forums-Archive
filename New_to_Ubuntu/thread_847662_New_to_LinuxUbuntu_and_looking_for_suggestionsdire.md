---
title: "New to Linux/Ubuntu and looking for suggestions/direction"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by davesalyers on 2008-07-02
Hi all,

I'm new to Linux and Ubuntu 8.04 (Hardy Heron). I am also definitely "non-techie" although I have played with computers since the Atari, Apple II, and early DOS days. I'm transitioning from Windows Vista on the home desktop and Windows XP on my home laptop (Compaq Presario 2000). I've installed Ubuntu 8.04 on both as dual boot - no problems there. I'm still have difficulty getting the wireless to work on the laptop - there is no problem with the wired internet connection on both. The graphics on the laptop are okay for most games but start "flashing" on more complicated games like the TuxRacer, Oolite, etc. I did enable the drivers for the graphics (and wireless) on the Hardware Drivers program on Ubuntu for both.

If I can ever figure out how to get the wireless and graphics to work then I would like to reinstall Ubuntu 8.04 on the Compaq Presario 2000 laptop as the sole OS. "Non-techie" direction (even things I can copy and paste) would be appreciated.

I will be keeping the desktop as dual boot (I use Windows to access Magic the Gathering Online, Yu-Gi-Oh Online, etc.). This computer is used for general home use (word processing, casual games like card games) as well as for homeschooling/educational purposes for our older elementary school age kids. They are ages 8 and 10. Would we benefit from installing the Edubuntu desktop (or I guess Ubuntu Education Edition now)?

I'm also looking for suggestions for software to do greeting cards and flyers with graphics for kids' events a la Printmaster Gold for my wife (who is less likely to want to explore a full desktop publishing suite to do those tasks).

I'm also looking for more "non-online" (single player against CPU players) casual games like card games (Mille Bornes, Bridge or Rook, etc. - I haven't found these yet) and other board/puzzle games (I have the standard right now). I also would like to track down some of the "classic" computer games (the old Star Trek game like on DOS or similar program, Babylon or other kingdom economy/battle "simulator" games, Adventure text games - I already found NetHack which reminds me of Rogue, etc. Old fogies know what I am talking about.) 

Suggestions would be appreciated.

Thanks!

Dave

---

### Post by phidia on 2008-07-02
Just addressing the wireless issue for the moment-you need to know what card your laptop has.
Post the output from lspci -v (typed in the terminal application).

---

### Post by ChildOfMana on 2008-07-02
> I also would like to track down some of the "classic" computer games (the old Star Trek game like on DOS or similar program, Babylon or other kingdom economy/battle "simulator" games, Adventure text games - I already found NetHack which reminds me of Rogue, etc. Old fogies know what I am taling about.)

DOSBox is your friend. Go to Applications > Add/Remove... and type dosbox in the search bar and you should see it right away. Tick the little box on the left and then click Apply Changes and DOSBox will be installed, and an entry added for it in the Applications > Games submenu.

DOSBox, as you might expect, is a DOS emulator and plays most old-school DOS games flawlessly.

More info on DOSBox can be found here: [http://www.dosbox.com/](http://www.dosbox.com/) 

And Abandonia [http://www.abandonia.com/](http://www.abandonia.com/) is a good place to start when looking for games to play.

Hope this helps man.

---

### Post by Werewolf85 on 2008-07-02
Hey!

First of all i don't do much gaming in Ubuntu. If you want to play old DOS based games try DOSBox, [http://www.dosbox.com]("http://www.dosbox.com") It allows you to "mount" and play the games we all loved back then.

You can get it from the repos, use Synaptic and search for "dosbox".

Good luck!

- Werewolf85

EDIT: ChildOfMana answered while I was typing, nice.

---

### Post by davesalyers on 2008-07-03
> **phidia said:**
> Just addressing the wireless issue for the moment-you need to know what card your laptop has.
Post the output from lspci -v (typed in the terminal application).

Here it is. Thanks!

david@david-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: 66MHz, medium devsel
	I/O ports at 8400 [size=16]
	Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c0200000-c02fffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 16
	Memory at c0003400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 16
	Memory at c0003800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 16
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at a000 [size=256]
	Memory at c0208000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 1355
	Flags: bus master, fast devsel, latency 64, IRQ 20
	Memory at c0204000 (32-bit, non-prefetchable) [size=8K]

05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at c0209000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 34000000-37fff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001

05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at c0208800 (32-bit, non-prefetchable) [size=2K]
	Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at c0206000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
	Subsystem: Hewlett-Packard Company Unknown device 3091
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at c020a400 (32-bit, non-prefetchable) [size=256]
	Memory at c020a000 (32-bit, non-prefetchable) [size=256]
	Memory at c0208400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

david@david-laptop:~$

---

### Post by phidia on 2008-07-03
This "Network controller: Broadcom Corporation BCM4318 " is your card.
See if the [guide here]("http://ubuntuforums.org/showthread.php?t=766560&highlight=Network+controller%3A+Broadcom+Corporation+BCM4318") works for you.

---

### Post by vikramaditya on 2008-07-03
> I'm still have difficulty getting the wireless to work on the laptop 

A lot of folks having wireless problems with the gnome network manager are reporting good experiences with wicd.  Here's how to install it ( courtesy sourceforge.net )
> Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line: 
deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 
where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. **_Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily._** 


In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".

If you can't get wicd working & are unable to get online again, you can reinstall network manger from the Live CD by opening terminal and copy/paste the following lines:
> sudo apt-cdrom add
sudo apt-get install network-manager-gnome
Hope that works for you!

---

### Post by davesalyers on 2008-07-03
Great! I will try the first suggestion on Broadcom first and if that does not work then I will try the wicd suggestion. Many thanks!

Also thanks for the dosbox suggestion. I'm hoping that since most of the old gamesI am looking for were old Unix text based games (Star Trek, Adventure, Babylon) that were subsequently coded for DOS that I can find native versions for Linux. But I will use DOSBox if there are no other options.

Dave

---

