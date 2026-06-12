---
title: "Lightscribe problems"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by nifty542 on 2012-05-07
Hi, all
I have installed lightscribeapplications, lightscribe:i386 and 4l:i386. I have also googled how to install the compatibility stuff (for 64 bit) and it seemed to work ok in the terminal.
I have two problems: I can't find 4l:i386. Second, the software doesn't recognise my optiarc DVDRW AD-7173A.
I have no idea how to proceed, and would need small steps if this requires a terminal solution.
Thanks, in advance.
Regards
David

---

### Post by nifty542 on 2012-05-08
Help, please, anyone?
I would love to get this to work in Lubuntu.
Regards
David

---

### Post by nifty542 on 2012-05-11
Hi, all

I tried to get help on this issue two days ago. No answers so far. Does anyone have any ideas about how to help, please?
Regards
David

---

### Post by khelben1979 on 2012-05-11
What version of Ubuntu are you using?

The hardware support which comes with the version of Ubuntu, differs a lot, depending on what version of Ubuntu you are trying with. Recommending a fresh version would be to recommend, if you want these lightscribe technologies to work correctly with your Ubuntu system.

If your Ubuntu version lacks the proper hardware support, you have different choices:

1. Wait until a new version of Ubuntu comes out, with more hardware support which hopefully solves this issue.
2. Get another Lightscribe compatible CD/DVD burner, and make sure that Linux is supported by the manufacturer.
3. Compile your own Ubuntu Linux kernel, to make sure you got the proper hardware support inbuilt.
or
4. Ignore the whole thing, and hope for some Ubuntu updates to take care of it for you. [-o<

---

### Post by nifty542 on 2012-05-11
Hi
Many thanks for the reply.
I think your reply just about covers it all!
Could you (or anyone else) please recommend a suitable drive?
I live in the UK, so would probably go for Amazon UK, Dabs.com, Play.com or Overclockers UK.
Many thanks- I was beginning to think this was unsolvable (know that's ungrammatical, but, what the hell).
If it comes down to it, I know it's very easy to reinstall if I need to.
Regards
David

---

### Post by nifty542 on 2012-05-11
Hi
Err, just realised I didn't answer your question. I'm using Lubuntu 12.04 64 bit.
System is AMD Phenom II X4 965 Processor 800 Mhz
3.5 Gb DDR3 memory
ATI Radeon 4250
Hope that helps- I'm still learning, despite using Ubuntu for a while, on and off
Regards
David

---

### Post by khelben1979 on 2012-05-12
Type ```
lspci
``` from a terminal so we can have a look if the Linux kernel finds your DVD burner, and if it does identify it correctly, then it means that the fault must be with the software you're using, and in that regard you have several applications to choose from.

If you have a Windows system, you can always look for newer Optiarc firmware and see if it can get upgraded, but I doubt that this is the problem here.

I have no experience in burning discs using Lightscribe technology myself using Linux, but I can say that if the Linux system correctly identifies what you got, looking at the model number specified by the lspci output, that's a good sign!

---

### Post by nifty542 on 2012-05-12
Hi
Thanks for the reply.
I get:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4250]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:06.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
03:06.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
03:06.2 USB controller: VIA Technologies, Inc. USB 2.0 (rev 63)
03:06.3 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
I'm afraid that doesn't mean much to me. I'm guessing it's a problem with the Lightscribe software, or I presume the drive wouldn't burn Cds and DVDs, which it does without a problem.
Regards
David

---

### Post by nifty542 on 2012-05-12
Hi, all
A further thought occurred to me: when I use Asunder or Kaffeine, I have to change the device to dev/sr0, not dev/cdrom.
Don't know if that helps. I can't see a way of making the Lightscribe software "see" my DVDRW drive.
Regards
David

---

