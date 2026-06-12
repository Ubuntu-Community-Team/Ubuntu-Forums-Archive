---
title: "phone won't mount to Ubuntu Gnome 15.10"
date: 2015-11-28
forum: New to Ubuntu
---

### Post by Mitchell_Davis on 2015-11-28
Hi all-

I'm having issues with my Nexus 5 and Nexus 6 mounting to my Dell XPS 8700 running Ubuntu Gnome 15.10.  Typing in dmesg command gives output below:

[116584.953319] usb 1-11: Product: Nexus 5
[116584.953320] usb 1-11: Manufacturer: LGE
[116584.953321] usb 1-11: SerialNumber: 07626fb400cb2e79

If I try running lsusb it just hangs and does nothing, I've tried booting into a live cd and all USB ports work and in the OS my USB keyboard and mouse work perfectly.  

My phone's are both set to MTP mode and I have tried installing mtpfs from another thread and no luck with that either.  

Does anyone have any other troubleshooting steps I can do to hopefully resolve this?

Thank you!

---

### Post by ajgreeny on 2015-11-28
Does the command **lsusb** always hang or is it only when the phone is attached?

Also read and follow the info at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) if you have not already found and tried all this; however, it does need info from **lsusb** so that could be a problem, hence my query above.

---

### Post by Mitchell_Davis on 2015-11-28
It always hangs when trying to run lsusb, not quite sure why.  I have tried the link you posted, sorry forgot to mention that.  I've also tried adding the android udev rules as well.

---

### Post by jim Kane on 2015-11-28
are you sure you have usb-debugging turned off on the phones

---

### Post by Mitchell_Davis on 2015-11-28
Yes, I've tried with USB debugging off and with it on.  Still no luck.

---

### Post by ajgreeny on 2015-11-28
Something is wrong somewhere if lsusb causes your computer to hang.
Do memory sticks work when plugged in?

---

### Post by Mitchell_Davis on 2015-11-28
Nope, they work in live mode but I can't seem to get them to work now that I check. I can see them connected if I do a dmesg but lsusb gives no output.

---

### Post by Mitchell_Davis on 2015-11-30
So for the sake of trying everything it seems that lsusb still hangs when trying today and freezes terminal but running lsusb -t works...not sure why.  Still cannot get any usb devices to be recognized.  Any other ideas?  Output of lsusb -t below.

```

root@mitch-XPS-8700:/# lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 1: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 2: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 13: Dev 6, If 0, Class=Wireless, Driver=, 12M
    |__ Port 13: Dev 6, If 1, Class=Wireless, Driver=, 12M
root@mitch-XPS-8700:/#

```

---

### Post by Geoffrey_Arndt on 2015-12-01
Maybe I missed it, but are you running a dual boot?   If so, does USB still work in Windows?

---

### Post by Mitchell_Davis on 2015-12-01
> **Geoffrey_Arndt said:**
> Maybe I missed it, but are you running a dual boot?   If so, does USB still work in Windows?

I am not running a dual boot but I just installed Ubuntu on here and before that I had Win 10 which USB worked perfectly. USB is also recognized by the BIOS as I'm able to boot from USB to a live system and USB works as it should.

---

### Post by sandyd on 2015-12-01
Run
```

lsusb
```

Do not close the terminal window, open a new tab or something to run the below
Run
```

dmesg
```

Any error messages or anything?

---

### Post by Mitchell_Davis on 2015-12-05
> **sandyd said:**
> Run
```

lsusb
```

Do not close the terminal window, open a new tab or something to run the below
Run
```

dmesg
```

Any error messages or anything?

Okay so I ran both at the same time (in different terminals) lsusb just hung and froze, ended up having to close it and dmesg showed a lot of output but no errors.  I've pasted a little bit of it below (there was a lot of output but it was all of the same type).

```

mitch@mitch-XPS-8700:~$ dmesg
[145378.457353] usb 1-7: new low-speed USB device number 34 using xhci_hcd
[145393.759473] usb 1-7: new low-speed USB device number 35 using xhci_hcd
[145409.061596] usb 1-7: new low-speed USB device number 36 using xhci_hcd
[145424.363703] usb 1-7: new low-speed USB device number 37 using xhci_hcd
[145439.665822] usb 1-7: new low-speed USB device number 38 using xhci_hcd
[145454.967874] usb 1-7: new low-speed USB device number 39 using xhci_hcd
[145470.270061] usb 1-7: new low-speed USB device number 40 using xhci_hcd
[145485.572164] usb 1-7: new low-speed USB device number 41 using xhci_hcd
[145500.874283] usb 1-7: new low-speed USB device number 42 using xhci_hcd
[145516.176426] usb 1-7: new low-speed USB device number 43 using xhci_hcd
[145531.478524] usb 1-7: new low-speed USB device number 44 using xhci_hcd
[145546.780611] usb 1-7: new low-speed USB device number 45 using xhci_hcd
[145562.082705] usb 1-7: new low-speed USB device number 46 using xhci_hcd
[145577.384907] usb 1-7: new low-speed USB device number 47 using xhci_hcd
[145592.687023] usb 1-7: new low-speed USB device number 48 using xhci_hcd
[145607.989121] usb 1-7: new low-speed USB device number 49 using xhci_hcd
[145623.291294] usb 1-7: new low-speed USB device number 50 using xhci_hcd
[145638.593391] usb 1-7: new low-speed USB device number 51 using xhci_hcd
[145653.895548] usb 1-7: new low-speed USB device number 52 using xhci_hcd
[145669.197682] usb 1-7: new low-speed USB device number 53 using xhci_hcd
[145684.499807] usb 1-7: new low-speed USB device number 54 using xhci_hcd
[145699.801908] usb 1-7: new low-speed USB device number 55 using xhci_hcd

```

---

### Post by Vladlenin5000 on 2015-12-05
I have a suspicion about what's happening here. Please post the hardware specs of the computer.

---

### Post by Mitchell_Davis on 2015-12-05
> **Vladlenin5000 said:**
> I have a suspicion about what's happening here. Please post the hardware specs of the computer.

Its a Dell XPS 8700, I ran lspci and the output is below.  If you need anything else, please let me know!

```

mitch@mitch-XPS-8700:~/cm/system$ lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 645 OEM] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```

---

### Post by Vladlenin5000 on 2015-12-05
Sorry... Absolutely nothing of what I was expecting.

You should check the BIOS for USB settings and play with them though.

---

### Post by cariboo on 2015-12-05
I have a Nexus 5 running Marshmallow (v 6.0), and have run into the same problem, I've tried setting the phone as a PTP device as well as MTP and still no joy. The problem has actually gotten worse since the upgrade to Android 6.0. At least with the previous version, 5.1, I could connect if I set the phone to use PTP. The problem shows up in both Windows 10, and Xenial (16.04).

---

### Post by Mitchell_Davis on 2015-12-06
[COLOR=#000000][IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **Vladlenin5000** [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13402388#post13402388")[/COLOR]
[COLOR=#000000][I]Sorry... Absolutely nothing of what I was expecting.

You should check the BIOS for USB settings and play with them though.[/I][/COLOR]

Unfortunately, I have already tried all the settings in BIOS :cry:

---

