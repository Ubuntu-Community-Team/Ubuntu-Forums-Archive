---
title: "Toshiba Satellite A135 (pclinuxos)"
date: 2007-09-02
forum: Other OS Talk
---

### Post by vanden12 on 2007-09-02
Hey I got Ubuntu fully working on this is thing...But I love kde even more then gnome (sure there kubuntu)But I like pclinuxos alot better than that...

But I cant find the wifi driver to work...But I know there something out there for linux since it built into ubuntu...What can I do?


Also need help with the sound...

Been really reading into it but cant seem to find anything on it(even post in the almost dead pclinuxos forums)

I think I have a Atheros wireless network adapter...

And a ATI Technologies SB450 HDA Audio....

Can anyone help me...

I find it kinda lame that ubuntu got this hardware working but pclinuxos cant....

---

### Post by dasunst3r on 2007-09-02
As far as the network card goes, try installing some package having to do with "madwifi."  I can't help you with the sound, unfortunately.  If the hardware works better for you in Kubuntu, you might want to use that distribution instead -- there's no shame in jumping from distro to distro -- I did that back when I first started using Linux.

---

### Post by vanden12 on 2007-09-02
I still use ubuntu...Just dont like kubuntu at all...

---

### Post by wolfen69 on 2007-09-02
maybe the folks over at the PCLOS forums could help you better.

---

### Post by SunnyRabbiera on 2007-09-03
exactly, as that is where to go...
I myself am a PCLOS user but I have no answers for you as I dont have a Toshiba Satellite A135

---

### Post by DreamcastJack on 2007-09-03
> **SunnyRabbiera said:**
> exactly, as that is where to go...
I myself am a PCLOS user but I have no answers for you as I dont have a Toshiba Satellite A135

ditto here. and I agree Kubuntu isnt that great compared to PCLOS..just my opinion.

---

### Post by mips on 2007-09-03
Post the output of **lspci -v** here and we'll have a look.

---

### Post by vanden12 on 2007-09-03
How do I get it..


I tried typing it in the terminal and running the command...

But it just tells me it cant do this?

---

### Post by oiler920 on 2007-09-03
My friend has an A135. I'll stick a LiveCD in and post the output. :) And it does work under Ubuntu 7.04. Never had any experience with PCLOS.

---

### Post by vanden12 on 2007-09-03
Wow thank you.... I real hope I get this to work...

---

### Post by mips on 2007-09-03
> **vanden12 said:**
> How do I get it..


I tried typing it in the terminal and running the command...

But it just tells me it cant do this?

have you tried running it as root or using **sudo lspci -v** ?

---

### Post by mips on 2007-09-03
> **oiler920 said:**
> My friend has an A135. I'll stick a LiveCD in and post the output. :) And it does work under Ubuntu 7.04. Never had any experience with PCLOS.

The wireless cards might not be the same. Manufacturers buy them and batches and if the batch is finished they might use another chipset. It changes the whole time so this might not work.

---

### Post by vanden12 on 2007-09-03
I hope it doesnt matter that i did it on ubuntu...If it matter let me know and I will do it on pclinuxos..

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff00

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 20
        Memory at dc005800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

---

### Post by mips on 2007-09-03
> **vanden12 said:**
> I hope it doesnt matter that i did it on ubuntu...If it matter let me know and I will do it on pclinuxos..

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1


Output from Ubuntu is fine thanks.

The above two entries are the important ones. The first one specifies your sound chipset (Intel) and the second one specifies your Wireless card (Atheros)

From [http://docs.pclinuxos.com/Atheros](http://docs.pclinuxos.com/Atheros) I gather that the madwifi driver is not installed by default and has to be added via Synaptic. Under advanced topics on that same site they cover the setup once the driver is installed, [http://docs.pclinuxos.com/Advancedrf](http://docs.pclinuxos.com/Advancedrf)
Also do a search for  **Atheros**  here, [http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26)

For sound do a search for  **82801G**   here, [http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26)

If you like kde have you considered looking at Mepis ?

---

### Post by vanden12 on 2007-09-03
But how to I get Synaptic to download it without internet on the laptop...

---

### Post by fwojciec on 2007-09-03
Plug the laptop into your router with a cable?

---

### Post by mips on 2007-09-03
> **fwojciec said:**
> Plug the laptop into your router with a cable?

Thats what I would have said.

---

### Post by lnxmomo on 2007-09-04
For sound, follow my article on getting it [here]("http://ubuntuforums.org/showthread.php?t=539595&highlight=A135").

It works on all versions of debian/ ubuntu i tried (although i cant say for PCLOS). However, it should work.

---

### Post by vanden12 on 2007-09-07
Well it doesnt support my ethernet eather...

---

### Post by mips on 2007-09-07
> **vanden12 said:**
> Well it doesnt support my ethernet eather...

You can try and chroot into your pclinuxos install from ubuntu and try and fix it that way manually transferring files. The other option would be to download the correct modules and try to install them manually. Have you tried asking in their forums and IRC channel ?

You might want to have a look at Mepis 7 & Linux Mint Cassandra KDE if kde is your thing.

---

### Post by vanden12 on 2007-09-07
Well dont really like Mepis....BUt Might give Linux Mint a try..Is Linux Mint  built for Kde like pclinux os or is just added in like kubuntu...


Wait can you maybe upload the files in a rpm so I can install them on my laptop...

Tryed the forums they were really no help...

---

### Post by mips on 2007-09-08
> **vanden12 said:**
> Well dont really like Mepis....BUt Might give Linux Mint a try..Is Linux Mint  built for Kde like pclinux os or is just added in like kubuntu...


Wait can you maybe upload the files in a rpm so I can install them on my laptop...

Tryed the forums they were really no help...

I dunno how they built mint but I know the KDE version was released months after the Gnome version so maybe they put some work into it.

Why don't you just download the RPM files via Ubuntu and copy them across to your pclinuxos partitiion.

If the forums/support is not that great then I would consider changing distro.

Another option might be pure Debian but that requires a bit of manual work to get it the way you want.

---

