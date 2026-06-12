---
title: "How to install additional drivers?"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by nifty542 on 2012-10-26
Hi, all

Could someone please tell me how to install graphics drivers? It used to be an item in the preferences menu, but has disappeared in Lubuntu 12.10.
I have tried software sources, but it is greyed out and I can't seem to enable it.
Regards
David

---

### Post by kaldor on 2012-10-26
Which driver is it that you're trying to install? 

But, to answer your question, the software is called Jockey. Try running *jockey-gtk* from the Terminal, or install the app with apt-get.

Otherwise, you can install the drivers via the terminal.

NVIDIA: 
```
sudo apt-get install nvidia-current
```


AMD/ATI:
```
sudo apt-get install fglrx
```

Good luck :)

---

### Post by nifty542 on 2012-10-26
Hi
Many thanks for the reply.
I am trying to install ATI drivers.
I tried the code, but repeatedly got "something wicked happened".
I don't know if it's relevant, but since I moved to Ramsgate (UK), I seem to have a very slow connection- even though it is supposedly broadband.
Anyway, thank you for the reply
Regards
David

---

### Post by kaldor on 2012-10-26
Which ATI card? The newer drivers have dropped support for some older cards (anything before HD 5000 series).

If you're not a gamer or into heavy HD playback, there may not be a need to install the drivers- the default open source one is pretty decent these days.

---

### Post by nifty542 on 2012-10-26
Hi, and thank you for the reply
I'm actually not sure of which graphics card I have- it used to be more easily identified in previous versions. But, it IS recent- a DDR3 system with an HDMI output- although, it's onboard. No, I'm not a gamer (does Kpat count?) so I guess, I may not need to install better drivers.
Sorry, but I am a slow learner- now if it was a piece of literature, I could dive in and bore you to tears.
Regards
David

---

### Post by kaldor on 2012-10-26
No problem :)

You can find some more information on your system by using the lspci command. Copy and paste the output from it. Here's mine:

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTS 450] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```

Look for the bit that says "VGA compatible controller". Near the bottom you can see my NVIDIA graphics card: "01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTS 450] (rev a1)"

Edit: I should mention that sometimes older graphics are used even in newer computers. My PC is only a year old, but the integrated graphics are from 2008.

---

### Post by Mark Phelps on 2012-10-27
> **nifty542 said:**
> ...  it IS recent- a DDR3 system with an HDMI output- although, it's onboard. 
I also have a recen DDR3 system, with an onboard video chip (AMD 4290) and that is NOT supported anymore with Ubuntu 12.10.  I have to use the default open-source Radeon drivers now.
> No, I'm not a gamer (does Kpat count?) so I guess, I may not need to install better drivers.
Then you're right -- you probably don't need the drivers.  The AMD drivers also bring the ability to control the GPU temps and fans -- but if you're not stressing the video chip, you may not need those.

We need to know which model video chip -- so do the "lspci" thing, or we can't help you.

---

### Post by nifty542 on 2012-10-27
Hi
Thank you for the replies. I really appreciate it. I got:

ort 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series]
02:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:06.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:06.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:06.2 USB controller: VIA Technologies, Inc. USB 2.0 (rev 63)
04:06.3 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)

Hope this makes sense to you. I'm not used to handling long lines of code.
Regards
David

---

### Post by Mark Phelps on 2012-10-27
Sorry, but the only drivers that will work with an AMD HD3xxx series card in Ubuntu 12.10 are the default Radeon drivers -- which are installed by default.

AMD dropped Linux restricted driver support for its HD 2x/3x/4x series this summer.

---

### Post by DGINSD on 2012-10-27
> **Mark Phelps said:**
> Sorry, but the only drivers that will work with an AMD HD3xxx series card in Ubuntu 12.10 are the default Radeon drivers -- which are installed by default.

AMD dropped Linux restricted driver support for its HD 2x/3x/4x series this summer.

Couldn't he also use the xorg-edgers ppa's for the more advanced open  source drivers? I'm on my phone so I can't post a link.

---

### Post by nifty542 on 2012-10-27
Hi
Many thanks for the reply. I don't know if I can do what the previous post suggests- I don't have much idea what it means.
But, thank you for the replies, anyway.
Regards
David

---

### Post by marlow59 on 2012-10-27
You may also check if your device is not supported on 12.10 since it includes better support for Nvidia and ATI graphics =)

---

### Post by oldos2er on 2012-10-28
> **nifty542 said:**
> Hi
Many thanks for the reply. I don't know if I can do what the previous post suggests- I don't have much idea what it means.


[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by monkeybrain2012 on 2012-10-28
> **kaldor said:**
> Which driver is it that you're trying to install? 

But, to answer your question, the software is called Jockey. Try running *jockey-gtk* from the Terminal, or install the app with apt-get.

Otherwise, you can install the drivers via the terminal.

NVIDIA: 
```
sudo apt-get install nvidia-current
```AMD/ATI:
```
sudo apt-get install fglrx
```Good luck :)

There should be something called "Ubuntu-drivers-common" or something like that in 12.10 which replaces jockey, but as far as my installation goes it doesn't work in detecting the driver, I have to install it from synaptic.

---

### Post by nifty542 on 2012-10-28
Hi, all
Thanks for the replies. I tried fglrx in the terminal, and something happened this time (instead of "something wicked happened". Not sure what I have done, though, or if it has made the system better.
Regards
David

---

### Post by nifty542 on 2012-10-29
Hi, all
I now have AMD catalyst control centre, but get the following message:
There was a problem initializing Catalyst Control Center Linux Edition. It could be caused by the following: No AMD graphics driver is installed or the AMD driver is not functioning properly. Please install the AMD driver appropriate for your hardware, or configure using aticonfig.
When I try aticonfig, I get:
No supported adpaters detected.
So, I guess that's it?
Would it be better to reinstall now (I have everything backed up) or is there a way to revert to the default drivers?
Regards
David

---

### Post by amjjawad on 2012-10-31
Hi,

If everything works just fine, why to install any driver?

Sometimes, using a previous release such as 12.04 is not bad idea at all.

I'm still on 12.04 on Lenovo Laptop Core i5 2nd generation with 4GB RAM and I'm not planning to upgrade nor install 12.10.

I have an HP Laptop at home and it has ATI. Not sure if it is just like yours or not but it works fine on Lubuntu 12.04 :)

---

### Post by Kaneda187 on 2013-07-11
This helped a lot thank you!
Coming back to linux after a long break....too long! Its good to be back :D

---

