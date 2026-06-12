---
title: "AMD SMbus problem"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by doom-ws508 on 2013-09-14
Now this *might* be a better fit for the ''hardware'' section, but I wasn't too sure, and I'm definitly an ''Absolute Beginner'' anyway, so here goes;

I ran the ''sudo lshw -html'' command to get my precise specs, and I found that this: [http://postimg.org/image/f51ega6pt/full/](http://postimg.org/image/f51ega6pt/full/) section (and only this one) is highlighted red for some reason.
I was messing around looking for system info to find out why my CPU fan goes absolutely crazy loud whenever I do anything that's slightly demanding (and sounds like a jet engine if I try to play a recent game)
Could this have anything to do with it? Is it something I should be worried about?

---

### Post by Android_63 on 2013-09-14
Please post the output of

```
lspci
```

(just open a terminal and type *lspci*, hit enter, then you can copy and paste the results here.

---

### Post by doom-ws508 on 2013-09-14
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde XT [Radeon HD 7770 GHz Edition]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)
```

---

### Post by doom-ws508 on 2013-09-16
Anyone?

---

