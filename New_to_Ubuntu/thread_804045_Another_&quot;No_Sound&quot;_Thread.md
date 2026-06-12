---
title: "Another &quot;No Sound&quot; Thread"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by musicxas on 2008-05-22
Hey everyone. I'm a super noob to Linux, I just installed Ubuntu last night. I'm on a Toshiba Satellite laptop, and I can't get any sound at all. I hear the little bongo sound before you log in when you start up, but after that, I hear nothing. When I go to audio preferences, if I try to test anything other than "autodetect" it locks up, and when I do test autodetect, I get this message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

When I do a hardware test, it also doesn't go past testing the audio. Can someone please help me? I need to hear sounds! :P

---

### Post by iaculallad on 2008-05-22
> **musicxas said:**
> Hey everyone. I'm a super noob to Linux, I just installed Ubuntu last night. I'm on a Toshiba Satellite laptop, and I can't get any sound at all. I hear the little bongo sound before you log in when you start up, but after that, I hear nothing. When I go to audio preferences, if I try to test anything other than "autodetect" it locks up, and when I do test autodetect, I get this message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

When I do a hardware test, it also doesn't go past testing the audio. Can someone please help me? I need to hear sounds! :P

Could you post whatever message this command produce:

**sudo lspci -vnnn**

and this one too:

**uname -a**

---

### Post by musicxas on 2008-05-22
lsci says

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e000 [size=8]
	Memory at a0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0080000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [d0] Power Management version 2

00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, fast devsel, latency 0
	Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000dfff
	Memory behind bridge: cc000000-cfffffff
	Prefetchable memory behind bridge: 000000009c000000-000000009fffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000bfff
	Memory behind bridge: c8000000-cbffffff
	Prefetchable memory behind bridge: 0000000098000000-000000009bffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1200 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1220 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1240 [size=32]

00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1260 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at f4000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: b8000000-c7ffffff
	Prefetchable memory behind bridge: 0000000088000000-0000000097ffffff
	Capabilities: [50] Subsystem: Gammagraphx, Inc. Unknown device [0000:0000]

00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at e100 [size=256]
	I/O ports at e200 [size=64]
	Memory at d0180000 (32-bit, non-prefetchable) [size=512]
	Memory at d0180200 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 04) (prog-if 00 [Generic])
	Subsystem: Toshiba America Info Systems Unknown device [1179:0001]
	Flags: medium devsel, IRQ 5
	I/O ports at e300 [size=256]
	I/O ports at e400 [size=128]
	Capabilities: [50] Power Management version 2

00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 04) (prog-if 80 [Master])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1100 [size=16]
	Capabilities: [70] Power Management version 2

01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
	Subsystem: Toshiba America Info Systems Marvell 88E8036 Fast Ethernet Controller (Inventec) [1179:ff10]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at cc000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at c000 [size=256]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

05:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
	Subsystem: Intel Corporation Unknown device [8086:2741]
	Flags: bus master, medium devsel, latency 128, IRQ 11
	Memory at b8008000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2

05:06.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at b8001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: bc000000-bffff000
	I/O window 0: 00008000-000080ff
	I/O window 1: 00008400-000084ff
	16-bit legacy interface ports at 0001

05:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029] (rev 01) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
	Flags: bus master, medium devsel, latency 128, IRQ 11
	Memory at b8000000 (32-bit, non-prefetchable) [size=2K]
	Memory at b8004000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

did i copy too much?

---

### Post by musicxas on 2008-05-22
Linux matt-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

is what uname -a said

---

### Post by iaculallad on 2008-05-22
> **musicxas said:**
> Linux matt-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

is what uname -a said

Try upgrading your current kernel:

**sudo apt-get install linux-686**

Hope that could fix your "No Sound"

---

### Post by musicxas on 2008-05-22
unfortunately, it still didn't work :(

---

### Post by iaculallad on 2008-05-22
> **musicxas said:**
> unfortunately, it still didn't work :(

Go to: System->Preferences->Sound
and on your "Device" tab, replace all "Autodetect" to ALSA.

---

### Post by musicxas on 2008-05-22
I've tried this before... Does it usually take a long time to test? A testing pipeline window comes up, and the little bar goes back and forth but never does anything. After that, I have to force quit for the "testing pipeline" window to go away.

EDIT: After waiting for about 5 minutes to see if the "testing" box would go away, nothing happened.

I'm wondering if maybe something happened during installation? Is there a way I could download a new torrent of Ubuntu and reinstall? Or would that not even be the problem?

---

### Post by iaculallad on 2008-05-22
A recurring problem on your Audio, I can't think of anymore solutions :confused: As for the torrent file you're asking, try this [link]("http://torrent.ubuntu.com:6969/").

---

### Post by Centx on 2008-05-22
I'm not any genius, but if you get the startup sound, I'd almost assume that you've got PA setup right, but maybe not for your particular user.

If you are out of options I would suggest that you try to set all the tabs in system > preferences > sound to pulseaudio server, and install "pavucontrol" and "padevchooser", then you shut off all programs that outputs sound, run "padevchooser" and add the "simultanous output" from the last tab of "configure local sound server" in the notification applet of padevchooser. If you haven't yet installed flash support for PA, add "libflashsupport" to the list of downloads.

Now if the issue is ALSA, and not PA, all of this probably is in vain =D

---

### Post by musicxas on 2008-05-25
is there any possible way I can download the soundmax sound driver from toshiba (the maker of my laptop) and install it on ubuntu? it's a .exe file, and I wonder if that could solve the problem...

---

### Post by joshsmith on 2008-05-25
hey, i would definitely try running the command
killall -9 pulseaudio 
a few times in the terminal, until it says no process killed, and then try playing sound, and report if that works


ps, downloading exe drivers for windows is not going to work at all, its not the correct type of solution

---

### Post by musicxas on 2008-05-25
sorry, I didn't know... I'm a complete noob to anything linux-related. killall -9 didn't work... I hope I figure something out soon...

---

