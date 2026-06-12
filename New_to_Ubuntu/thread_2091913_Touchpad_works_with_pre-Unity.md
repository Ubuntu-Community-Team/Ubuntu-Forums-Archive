---
title: "Touchpad works with pre-Unity"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by hubmat on 2012-12-06
I have a Samsung RV515-A03 Laptop.  When I have Ubuntu 10.10 or earlier installed, the touchpad and left/right buttons work but when I have 11.04 or later installed, they do not work and a USB mouse works.   Is there a work around this?

---

### Post by hubmat on 2013-02-07
bump

---

### Post by sandyd on 2013-02-07
> **hubmat said:**
> bump

Hi, can you post the output of
```

lspci
xinput --list
lsusb
```

Thanks!

---

### Post by hubmat on 2013-02-08
> **sandyd said:**
> Hi, can you post the output of
```

lspci
xinput --list
lsusb
```Thanks!
```
lspci: 00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```
xinput --list:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; WebCam SC-0311139N                          id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
```

lsusb:
```
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 002: ID 2232:1020  
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

It doesn't matter if I have it installed on the hard drive or running from the USB flash drive, I still get the same results with the mouse.

---

### Post by hubmat on 2013-02-10
Problem solved.  It was this that solved it:
 "Open the Terminal
cd /etc/modprobe.d/
gksudo gedit options.conf
In the text editor, type: options psmouse proto=imps
Save the file and close it.
sudo modprobe -r psmouse
sudo modprobe psmouse"

---

### Post by mörgæs on 2013-02-10
Good, then please mark the thread so.

---

