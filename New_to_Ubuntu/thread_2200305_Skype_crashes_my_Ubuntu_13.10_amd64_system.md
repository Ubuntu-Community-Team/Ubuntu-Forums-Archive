---
title: "Skype crashes my Ubuntu 13.10 amd64 system"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by jositotj on 2014-01-18
Hi I'm new to the Ubuntu forums and this is going to be my first post (fingers crossed).

I've installed Ubuntu 13.10 x64 just few days ago and I cannot manage to make Skype work. I installed Skype from the Canonical repos (4.2.0.11-0ubuntu0.12.04.2) as suggested in many places and tried a bunch of tweaks/suggestions but every time I enable the video in a call, or go to the Options > Video Devices my complete system crashes. X freezes, I cannot even switch to console (keyboard doesn't answer), so the only way to recover control is resetting the computer. Cheese works ok, and doesn't hangs my PC.

I tried with other 64bit distro based on Ubuntu 13.10 (Linux Mint 16)  and the same happens. The 32bits version of Linux Mint works OK, so  Ubuntu 13.10 32bits should do as well (although not tested).
Running  gstreamer-properties shows the same behavior. Crash when testing input  video with any configuration. I would say it has to do with the V4L2  libraries, but I don't have enough knowledge and don't know what else to  try. This was my last resource before switching finally to 32bits linux  distro.

My attempts to fix this have been:

1) Ensuring swappiness is not causing SWAP. Every time I enable video my used RAM is around 1GB out of 3GB available and SWAP always 0%.
2) Enabling multi-arch, and installing skype from the canonical repos, instead of Skype's website[INDENT]```
sudo dpkg --add-architecture i386
```
[/INDENT]
3) Preloading V4L libraries when launching Skype
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so

I run skype from console, but it doesn't log any error prior to the freeze. Neither Syslog or X.org.0.log report any issue.

Some relevant data in case it help. PC Configuration: APU AMD A6-6400K, 4GB RAM, fglrx driver in use (the open source is really unstable with my embedded graphics Radeon HD 8470D).

```
Linux zeus 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
joseluis@zeus:~$ lsusb 
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:6341 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 1bcf:05ca Sunplus Innovation Technology Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 1567:8902  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
joseluis@zeus:~$ dmesg | grep -i usb
[    0.303014] ACPI: bus type USB registered
[    0.303029] usbcore: registered new interface driver usbfs
[    0.303035] usbcore: registered new interface driver hub
[    0.303057] usbcore: registered new device driver usb
[    0.867884] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.868028] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.876208] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.876247] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.876249] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.876250] usb usb1: Product: EHCI Host Controller
[    0.876252] usb usb1: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.876253] usb usb1: SerialNumber: 0000:00:12.2
[    0.876351] hub 1-0:1.0: USB hub found
[    0.876570] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.888207] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.888230] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.888232] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.888234] usb usb2: Product: EHCI Host Controller
[    0.888235] usb usb2: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.888236] usb usb2: SerialNumber: 0000:00:13.2
[    0.888343] hub 2-0:1.0: USB hub found
[    0.888445] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.888451] uhci_hcd: USB Universal Host Controller Interface driver
[    0.888605] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 3
[    0.888894] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.888895] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.888897] usb usb3: Product: xHCI Host Controller
[    0.888898] usb usb3: Manufacturer: Linux 3.11.0-12-generic xhci_hcd
[    0.888899] usb usb3: SerialNumber: 0000:00:10.0
[    0.888971] hub 3-0:1.0: USB hub found
[    0.889026] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 4
[    0.892202] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.892203] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.892205] usb usb4: Product: xHCI Host Controller
[    0.892206] usb usb4: Manufacturer: Linux 3.11.0-12-generic xhci_hcd
[    0.892207] usb usb4: SerialNumber: 0000:00:10.0
[    0.892267] hub 4-0:1.0: USB hub found
[    0.904368] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 5
[    0.904665] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    0.904667] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.904668] usb usb5: Product: xHCI Host Controller
[    0.904669] usb usb5: Manufacturer: Linux 3.11.0-12-generic xhci_hcd
[    0.904671] usb usb5: SerialNumber: 0000:00:10.1
[    0.904767] hub 5-0:1.0: USB hub found
[    0.904830] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 6
[    0.907969] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    0.907970] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.907971] usb usb6: Product: xHCI Host Controller
[    0.907972] usb usb6: Manufacturer: Linux 3.11.0-12-generic xhci_hcd
[    0.907974] usb usb6: SerialNumber: 0000:00:10.1
[    0.908034] hub 6-0:1.0: USB hub found
[    0.958813] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 7
[    1.016193] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.016196] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.016198] usb usb7: Product: OHCI PCI host controller
[    1.016199] usb usb7: Manufacturer: Linux 3.11.0-12-generic ohci_hcd
[    1.016201] usb usb7: SerialNumber: 0000:00:12.0
[    1.016329] hub 7-0:1.0: USB hub found
[    1.016577] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 8
[    1.076229] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    1.076232] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.076234] usb usb8: Product: OHCI PCI host controller
[    1.076236] usb usb8: Manufacturer: Linux 3.11.0-12-generic ohci_hcd
[    1.076237] usb usb8: SerialNumber: 0000:00:13.0
[    1.076362] hub 8-0:1.0: USB hub found
[    1.076608] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 9
[    1.136168] usb usb9: New USB device found, idVendor=1d6b, idProduct=0001
[    1.136172] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.136174] usb usb9: Product: OHCI PCI host controller
[    1.136175] usb usb9: Manufacturer: Linux 3.11.0-12-generic ohci_hcd
[    1.136176] usb usb9: SerialNumber: 0000:00:14.5
[    1.136304] hub 9-0:1.0: USB hub found
[    1.244163] usb 1-4: new high-speed USB device number 3 using ehci-pci
[    1.493062] usb 1-4: New USB device found, idVendor=0c45, idProduct=6341
[    1.493066] usb 1-4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.493068] usb 1-4: Product: USB 2.0 Camera
[    1.493069] usb 1-4: Manufacturer: Sonix Technology Co., Ltd.
[    1.736087] usb 5-1: new high-speed USB device number 2 using xhci_hcd
[    1.760609] usb 5-1: New USB device found, idVendor=1567, idProduct=8902
[    1.760613] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.760614] usb 5-1: Product: USB Product String123456
[    1.760616] usb 5-1: Manufacturer: USB Flash Disk
[    1.760617] usb 5-1: SerialNumber: 12122701115F
[    1.762268] usb-storage 5-1:1.0: USB Mass Storage device detected
[    1.762349] scsi2 : usb-storage 5-1:1.0
[    1.762421] usbcore: registered new interface driver usb-storage
[    1.896059] usb 7-3: new low-speed USB device number 2 using ohci-pci
[    2.063169] usb 7-3: New USB device found, idVendor=1bcf, idProduct=05ca
[    2.063173] usb 7-3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.063175] usb 7-3: Product: 2.4GHz 2way RF Receiver
[    2.085209] usbcore: registered new interface driver usbhid
[    2.085212] usbhid: USB HID core driver
[    2.086648] input: 2.4GHz 2way RF Receiver as /devices/pci0000:00/0000:00:12.0/usb7/7-3/7-3:1.0/input/input2
[    2.086748] hid-generic 0003:1BCF:05CA.0001: input,hidraw0: USB HID v1.00 Keyboard [2.4GHz 2way RF Receiver] on usb-0000:00:12.0-3/input0
[    2.087437] input: 2.4GHz 2way RF Receiver as /devices/pci0000:00/0000:00:12.0/usb7/7-3/7-3:1.1/input/input3
[    2.087845] hid-generic 0003:1BCF:05CA.0002: input,hiddev0,hidraw1: USB HID v1.00 Mouse [2.4GHz 2way RF Receiver] on usb-0000:00:12.0-3/input1
[   13.844050] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:6341)
[   13.857698] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/input/input10
[   13.857974] usbcore: registered new interface driver uvcvideo
[   13.857976] USB Video Class driver (1.1.1)
[   13.886348] usbcore: registered new interface driver snd-usb-audio
```

```
joseluis@zeus:~$ lsmod | grep -i usb
snd_usb_audio         149162  1 
snd_usbmidi_lib        25070  1 snd_usb_audio
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102033  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_rawmidi            30095  2 snd_usbmidi_lib,snd_seq_midi
snd                    69141  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
usb_storage            62062  0
```

---

### Post by DuckHook on 2014-01-18
You have commendable instincts to post with so much info. It makes helping you much easier.

I don't use Skype, so my input will be of limited value. However, a few observations:

1. You are not the first person to report broken or frozen Skype on these forums. Ever since Skype sold out to MS, it has deteriorated by degrees into a smelly sock. You may wish to switch to a SIP-based service like Ekiga, LinPhone, QuteCom, (many others&#8212;look in software centre). This may not be feasible if you have a business dependence on Skype, but there are obvious advantages to severing the dependence on proprietary ransomware&#8212;as you are now seeing in Skype's increasingly crippled functionality with any OS not MS.

2. In the event of a frozen system, do not punch the reset button without trying these other techniques first. Set up your box as a *properly secured* [ssh server]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring"). Often, if the local inputs are frozen out, you can still ssh into your box from another machine and shut it down properly. Also, if all else fails, use the [REISUB]("http://en.wikipedia.org/wiki/Magic_SysRq_key") technique to shut it down without corrupting files.

3. Your problems are extremely unlikely to be caused by swappiness.

4. Which fglrx driver are you using? If easier, do:```
lspci -vnnk | grep -iA20 vga
```Have you tried it with other (newer/older) drivers?

5. dmesg will only give you the kernel messages since start of your current boot. Therefore, it won't report what caused your last freeze-up. Better to look in syslog, Xorg.0.log and kern.log, which straddles boot cycles. Instead of filtering for "USB", filter for keywords like "warning", "error" and "fatal". i.e.```
egrep "warning|error|fatal" /var/log/syslog
```

Please don't take my response for help that is of any value. As noted, I don't use Skype and know nothing about it, nor its interactions with Ubuntu. However, the above info may make it easier for someone who really does know what they are doing to help you. Hoping that they see this thread and jump in.

---

### Post by jositotj on 2014-01-21
Thanks DuckHook. Sometimes we forget to build the house from the bottom. Finally I fixed the issue by installing propietary "beta" drivers for my card. Your advice to log-in remotely via SSH to reboot/shutdown cleanly worked like a charm. Indeed the problem was not the system hung, but only the X that got frozen.

I tried other drivers. None of the default privative drivers in the Ubuntu repos worked with Skype (they all made the X to freeze when enabling video in Skype). When I switched to the opensource drivers from the repositories, the webcam worked fine, but then the system was really unstable, with the embedded vga card of my APU failing to draw the desktop all the time. I was about to install the newest available stable AMD drivers from their website, but finally didn't, after remembering last time I did it, my X got corrupted after upgrading some Ubuntu component. As a result I had to re-install Ubuntu from scratch. They seem to don't get long very well. I found instead a ppa with .deb packaged drivers, which seem beta, but work well for me so far:

```
***ppa:xorg-edgers/ppa***
```

The steps I followed were:

1) Add PPA and install the new driver, fglrx-13:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-13
```

```
joseluis@zeus:~$ apt-cache show fglrx-13
Package: fglrx-13
Source: fglrx-installer-13
Priority: extra
Section: misc
Installed-Size: 242619
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2:13.101~beta-0ubuntu1~xedgers~saucy1

```

2) Reboot the system. My X failed to start, so I tried to fall back to the previous driver
```
sudo apt-get install fglrx
```

3) Reboot the system again. This time the X started successfully and skype worked as well.

Apparently the driver is not the one from the ppa, but it seems together with the fglrx-13 it came some udpated library that made the difference. Currently:

```
sudo lspci -vnnk | grep -iA15 -B10 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8470D] [1002:9996] (prog-if 00 [VGA controller])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8470D] [1002:9996]
    Flags: bus master, fast devsel, latency 0, IRQ 58
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
```

I hope this helps others as well. It has been a pain. I'll post if I find any issue after my daily use of this computer.

---

