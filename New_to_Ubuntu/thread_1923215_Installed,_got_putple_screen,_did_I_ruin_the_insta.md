---
title: "Installed, got putple screen, did I ruin the install?"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by Cheeky88 on 2012-02-10
After installing Ubuntu from the Live CD I was asked to restart, but after restarting and selecting Ubuntu from grub I got a purple screen. 

I hit the restart button on my computer after about 6 minutes of the purple screen. I moved the mouse and could see it, so it must have been a graphics error, not a loading screen.

I tried to boot in recovery mode after the restart but that did not work it was simply a list of checks and the "fallback graphics" "failed" or something.

Should I just reinstall over the Ubuntu partitian using the LiveCD again? Will this ruin by grub or does that just reinstall along with ubuntu?

I have an AMD 6850 and a Phenom II X4 965, I am dual booting with Windows 7.

If someone could give me specific instructions I would be happy :)

---

### Post by Cheeky88 on 2012-02-10
no one else know?

---

### Post by cortman on 2012-02-10
Be patient! :)

From the live CD, run lspci in the terminal to get us some info on your graphics card. If you have no data in the Ubuntu installation that you need to save, a re-installation is the best idea. Grub will re-install along with Ubuntu- just select to install OVER the existing Ubuntu installation when you're re-installing, or select the partition manually.

---

### Post by Cheeky88 on 2012-02-10
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Barts PRO [ATI Radeon HD 6800 Series]
01:00.1 Audio device: ATI Technologies Inc Barts HDMI Audio [Radeon HD 6800 Series]
02:00.0 IDE interface: VIA Technologies, Inc. VT6415 PATA IDE Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

thats what I get

---

### Post by cortman on 2012-02-10
Ok, try re-installing Ubuntu, and if you can boot to the desktop, we can step you through getting drivers for your graphics card, if that is indeed the problem.

Good luck!

---

### Post by wildmanne39 on 2012-02-10
Hi, you can try this it usually lets you boot so you can install graphic drivers if hitting the power off button did not do any damage.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by holytree on 2012-02-10
Hi I had the same problem...after which ubuntu 11.10 dint install again via wubi..i had to install 11.04 then upgrade.

So---
Which version do you use?
Wubi or native install?

---

### Post by Cheeky88 on 2012-02-10
> **holytree said:**
> Hi I had the same problem...after which ubuntu 11.10 dint install again via wubi..i had to install 11.04 then upgrade.

So---
Which version do you use?
Wubi or native install?

I installed so it runs from grub dual boot. 


Now after putting in nomodeset and acpi_osi= it went to this screen, i took a photo and attached...

---

### Post by cortman on 2012-02-10
And it just hangs at this screen, and doesn't proceed to booting your desktop? How long does it hang there?

---

### Post by Cheeky88 on 2012-02-10
> **cortman said:**
> And it just hangs at this screen, and doesn't proceed to booting your desktop? How long does it hang there?

As long as I left it, which was about 15 minutes

I wonder if it would be best if I just installed 11.04 ?

---

### Post by Bartender on 2012-02-10
> **Cheeky88 said:**
> I wonder if it would be best if I just installed 11.04 ?

It might be best to check your download with an md5 utility.  If it checks out OK, the next question would be how you burned the CD.  Did you let it burn at maximum speed?  4X to 8X is safest with a modern PC.

Have you booted from your CD, and asked it to check itself?  I'm guessing there are errors on the CD.

---

### Post by Cheeky88 on 2012-02-11
> **Bartender said:**
> It might be best to check your download with an md5 utility.  If it checks out OK, the next question would be how you burned the CD.  Did you let it burn at maximum speed?  4X to 8X is safest with a modern PC.

Have you booted from your CD, and asked it to check itself?  I'm guessing there are errors on the CD.

Yes, I checked the CD in the ubuntu livecd menu and it said it was all good.

---

### Post by Bartender on 2012-02-11
> **Cheeky88 said:**
> I wonder if it would be best if I just installed 11.04 ?

If you're thinking about dropping back to a "safer" version, why not go all the way?  D/l 10.04 LTS 32-bit (not 64!) and see what happens.

---

### Post by Cheeky88 on 2012-02-11
> **Bartender said:**
> If you're thinking about dropping back to a "safer" version, why not go all the way?  D/l 10.04 LTS 32-bit (not 64!) and see what happens.

I did and it worked, I went to 10.04 lts, I really want 11.10 though so I installed drivers and am now upgrading option from disc. hopefully yhat works

downloading the upgrade didn't seem to work said "definitions couldn't be found" - wierd.

---

### Post by Cheeky88 on 2012-02-11
Ok I'm pretty sure it is a driver problem, because once I updated, Ubuntu 11.10 took me to a flcikery glitched purple screen. The amd drivers I downloaded from their site work, any way to boot into 11.10 in text mode and any way to run them from a USB or something?

---

