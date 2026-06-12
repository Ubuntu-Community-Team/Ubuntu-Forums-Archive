---
title: "setting up modem router on HH is getting nowhere, can anyone help?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Hylas de Niall on 2008-07-19
Hello all.

I'm probably your worst nightmare: someone who is new to Ubuntu AND broadband! (sorry!)

Well here's my problem, I hope someone can help me:

I'm dual-booting Win XP Pro (SP2) and Ubuntu 8.04 Hardy Heron, and connecting with an ethernet (non wireless) Dynamode R-ADSL-C4-2 modem router.

This works superbly in XP, but i can't for the life of me get it to work in HH. All the lights on the unit show as active, so it isn't being shut down at the close of a Windows session.

I have tried setting it up in the Network manager etc (which for some reason takes AGES to respond to changes made) with no luck.

My network adapter is a Realtek RTL8029(AS) if this helps.

Many thanks in advance!

---

### Post by spiderbatdad on 2008-07-19
I believe the problem is with you nic. There is a thread here that mentions a driver: [http://www.linuxquestions.org/questions/linux-hardware-18/realtek-rtl8029-158088/](http://www.linuxquestions.org/questions/linux-hardware-18/realtek-rtl8029-158088/)

Also, please try google regarding the nic and ubuntu or linux.

May also be a problem with the HH kernel, as there are a lot broken binaries due to missing symlinks. You might try 7.10 which uses kernel 2.6.22, or you might consider leaping ahead to Intrepid Ibex. Alpha 2 is out. I've been using it for over a week, so far my hardware all worked with no issues.

---

### Post by Hylas de Niall on 2008-07-19
> **spiderbatdad said:**
> I believe the problem is with you nic. There is a thread here that mentions a driver: [http://www.linuxquestions.org/questions/linux-hardware-18/realtek-rtl8029-158088/](http://www.linuxquestions.org/questions/linux-hardware-18/realtek-rtl8029-158088/)

Also, please try google regarding the nic and ubuntu or linux.

May also be a problem with the HH kernel, as there are a lot broken binaries due to missing symlinks. You might try 7.10 which uses kernel 2.6.22, or you might consider leaping ahead to Intrepid Ibex. Alpha 2 is out. I've been using it for over a week, so far my hardware all worked with no issues.

Thanks for that.

The irony is that i switched to ethernet from a usb especially for Linux! Even more ironic is that i had Gutsy installed at first as well (though not with the Realtek)!

I'll try switching back to that, as recompiling a kernel sounds way too scary for a noob like me to attempt!

Failing that, would there be any advantage in trying other Linux distros instead, or is the problem inherent in all of them?

I'm itching to be Microsoft-free as soon as i can.

Thanks again!

---

### Post by bumanie on 2008-07-19
As far as I can tell, that realtek nic is supported by the latest linux kernel/s. The thread above is 4+ years old. The nic should work OK. Post output of > lspciwhen the realtek is installed in the computer, please. Mind you, I'm not an expert on network cards.

---

### Post by Hylas de Niall on 2008-07-19
> **bumanie said:**
> As far as I can tell, that realtek nic is supported by the latest linux kernel/s. The thread above is 4+ years old. The nic should work OK. Post output of when the realtek is installed in the computer, please. Mind you, I'm not an expert on network cards.

Thank you for the reply. Here's the lspci return:

hylas@hylas-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
hylas@hylas-desktop:~$ 

I hope that helps, it sees the Realtek AND the onboard VIA (which has no physical socket - and which i THOUGHT i had disabled in the BIOS). so that means it's me doing something wrong, right?
Remember i'm new to broadband and have probably missed something really obvious. I hope not.

Thanks again!

---

### Post by Hylas de Niall on 2008-07-19
bump

---

### Post by Hylas de Niall on 2008-07-19
> **spiderbatdad said:**
> I believe the problem is with you nic. There is a thread here that mentions a driver: [http://www.linuxquestions.org/questions/linux-hardware-18/realtek-rtl8029-158088/](http://www.linuxquestions.org/questions/linux-hardware-18/realtek-rtl8029-158088/)

Also, please try google regarding the nic and ubuntu or linux.

May also be a problem with the HH kernel, as there are a lot broken binaries due to missing symlinks. You might try 7.10 which uses kernel 2.6.22, or you might consider leaping ahead to Intrepid Ibex. Alpha 2 is out. I've been using it for over a week, so far my hardware all worked with no issues.


Thanks again! I reinstalled 7.10 and connected straight away!
No configuring at all!
I'm in your debt.

---

