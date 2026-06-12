---
title: "Stuck on boot up...... using usb"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by Wisco on 2013-03-02
Hi,

I recently found out about ubuntu.. trying to run it off a usb using version 12.10 32 bit. Using the computer at my school it booted perfect, now trying to run it off of 2 other laptops at my house its gets stuck on the first line of code. I have tried switching to the 64bit version still no luck. Booted in once from a cd but it took a solid 10 minutes to boot. and was very slow and unresponsive.

heres a link to a pic: [http://ubuntuforums.org/showthread.php?t=1894513](http://ubuntuforums.org/showthread.php?t=1894513)

I've done everything that was suggested on there so im lost

any help is nice thanks

---

### Post by Wisco on 2013-03-02
Hi,

I recently found out about ubuntu.. trying to run it off a usb using version 12.10 32 bit. Using the computer at my school it booted perfect, now trying to run it off of 2 other laptops at my house its gets stuck on the first line of code. I have tried switching to the 64bit version still no luck. Booted in once from a cd but it took a solid 10 minutes to boot. and was very slow and unresponsive.

heres a link to a pic: [[COLOR=#dd4814]http://ubuntuforums.org/showthread.php?t=1894513[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1894513")

I've done everything that was suggested on there so im lost

any help is nice thanks

---

### Post by Wisco on 2013-03-02
top

---

### Post by Wisco on 2013-03-02
top

---

### Post by cariboo on 2013-03-02
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by carl4926 on 2013-03-02
> [COLOR=#000000]Using the computer at my school it booted perfect, now trying to run it off of 2 other laptops at my house its gets stuck[/COLOR]
Is that with the same USB?




> [COLOR=#000000]Booted in once from a cd but it took a solid 10 minutes to boot[/COLOR]Wow. Sounds like some hardware issues.
If you can get there again, you should open a terminal and get the result of

```
lspci -nnk
```Post it here. Which may demand some ingenuity on your part.

---

### Post by Wisco on 2013-03-03
yes same usb flash drive


well i got it to boot up again and heres the code it gave me

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel modules: i2c-i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: intel ips
    Kernel modules: intel_ips
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z062.12 802.11bgn Wireless Half-size Mini PCIe Card [103c:3040]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
    Kernel driver in use: r8169
    Kernel modules: r8169
7f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
7f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
7f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
7f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
7f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:144c]
7f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:144c]

---

### Post by Wisco on 2013-03-03
anyone?

---

### Post by carl4926 on 2013-03-03
Well I see nothing  dramatic, though I can't really explain why some of it is minimal
By that I mean
```
[COLOR=#000000]7f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company Device [103c:144c][/COLOR]
[COLOR=#000000]7f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company Device [103c:144c][/COLOR]
[COLOR=#000000]7f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company Device [103c:144c][/COLOR]
[COLOR=#000000]7f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company Device [103c:144c][/COLOR]
[COLOR=#000000]7f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company Device [103c:144c][/COLOR]
[COLOR=#000000]7f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company Device [103c:144c][/COLOR]
```


It just lists the device and no kernel module

IMO. It would be worth testing other distros to see how they perform.

---

### Post by Wisco on 2013-03-04
somewhat new at this. so could you explain what distros are? are they the linuxs themselves such as Ubuntu,Linux mint,Fedora etc.....

---

### Post by carl4926 on 2013-03-04
> [COLOR=#000000]are they the linuxs themselves such as Ubuntu,Linux mint,Fedora etc.....[/COLOR]Correct

---

### Post by Wisco on 2013-03-05
alright thanks... i've tried ubuntu 12.10, Linux mint 14, and fedora and still no luck

---

### Post by carl4926 on 2013-03-06
Perhaps try some of these options
[https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.44.40.jpg](https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.44.40.jpg)

---

### Post by GregA on 2013-03-06
Also, many older PC's (even 2-3 yo) won't recognize USB flash sticks as bootable devices (2 of my 3 PC's won't, but a newish Acer Laptop will).   Further, even if your systems are capable of booting usb flash, the bios may need to be reconfigured to change the boot order, placing removable drives as first, optical drives as second and standard hard drives as third in sequence.

---

### Post by Wisco on 2013-03-09
Well i have found a solution but it does'nt really make any sense. With a diferent usb flashdrive its boots up fine on my computer at home. But the other one i was using that was giving me problems also booted up fine on another computer but not mine.... But now it does'nt really matter, thanks for all the help

---

### Post by fiodev on 2013-03-09
I would try a fedora distro, one of my computers will only boot fedora oddly enough. I named that computer...it's a bad word and I can't post that here.

---

### Post by squakie on 2013-03-10
May be a USB 2 versus USB 3 issue (or if REALLY old, a USB 1 versus USB 2 issue), depending on what your laptop has compared to the others.

---

