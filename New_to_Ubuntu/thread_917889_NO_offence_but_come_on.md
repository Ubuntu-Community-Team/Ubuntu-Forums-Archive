---
title: "NO offence but come on"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Gildp67 on 2008-09-12
I have been a fan of Ubuntu for some time now, but the lack of sound card support is leaving me to think that this version is less than even vista quality. I have ask and emailed and searched the web high and low for a fix for my sound card and still nothing and the audigy line is so widely used I am shocked that it doesn't work without question. I get that this OS is free and all but come on. There should not be this much work just to get sound. Never had this much problem in the past. All I get is buzzing and popping and clicking shouldn't be so messed up at this point. Sorry but very frustrated and very disappointed.

---

### Post by wolfen69 on 2008-09-12
do you have onboard sound? if so, did you disable it? and what is the model# of the audigy card? audigy 1? 2?

---

### Post by halitech on 2008-09-12
can you post the output of ```
lspci
```
I can't see it not working, I've only ever had problems getting old ISA cards to work with sound.

---

### Post by SunnyRabbiera on 2008-09-12
But Sound card support is more of a HARDWARE issue then a Ubuntu one, as it stands Ubuntu technically can support more hardware then Vista as its dynamic kernel is always changing.
But this is more of a manufacturer issue, not a Ubuntu one.
But if you insist on using windows then do so and be done with it, if you are unwilling to learn that linux isnt always at fault then you have no business using it.

---

### Post by Bucky Ball on 2008-09-12
Some more detailed specs on your soundcard would help. Creative make many. :)

---

### Post by MegaJim on 2008-09-12
> **Gildp67 said:**
> I have been a fan of Ubuntu for some time now, but the lack of sound card support is leaving me to think that this version is less than even vista quality. I have ask and emailed and searched the web high and low for a fix for my sound card and still nothing and the audigy line is so widely used I am shocked that it doesn't work without question. I get that this OS is free and all but come on. There should not be this much work just to get sound. Never had this much problem in the past. All I get is buzzing and popping and clicking shouldn't be so messed up at this point. Sorry but very frustrated and very disappointed.

Which sound card do you have?

```
sudo lshw -C multimedia
```

P.s. any moaning should be directed at Creative Ltd., as they are the company who build the audigy and decide not to write drivers for the Linux platform!

FYI I have an Audigy 2 ZS running flawlessly with the emu101k

---

### Post by Gildp67 on 2008-09-12
I have Audigy 2 and yes on board sound is disabled. Worked fine until I decided to use latest vers of Ubuntu

---

### Post by SunnyRabbiera on 2008-09-12
> **Gildp67 said:**
> I have Audigy 2 and yes on board sound is disabled. Worked fine until I decided to use latest vers of Ubuntu

Well hope you know that creative is a crappy sound card company even on windows.
I used a creative sound card on my old Desktop PC, I had XP with all the trimmings, installed all the drivers, restarted my computer and still the creative card gave me issues.
Give me Realtek anyday, I had better luck with them.

---

### Post by jerome1232 on 2008-09-12
My Sound Blaster Audigy 2 ZS works flawlessly perhaps you can run the lshw command that was suggested and provide the output

---

### Post by SunnyRabbiera on 2008-09-12
> **jerome1232 said:**
> My Sound Blaster Audigy 2 ZS works flawlessly perhaps you can run the lshw command that was suggested and provide the output

My experiences with creative have been hellish on a personal note, when I had to do a windows update it seemed I had to fix the rotten thing every time.

---

### Post by Jadd on 2008-09-12
NO offence but come on
What kind of thread title is that?
NO offence but come on
Please, if you want help, stick to some simple rules, such as descriptive thread titles.

---

### Post by jaqie on 2008-09-12
In all honesty if you didn't have trouble with your audigy in windows you got lucky. There was a class action lawsuit against creative tech for the EMU10k series of cards (including the audigy) about serious deficiencies in the hardware and driver, IIRC.  So you didn't get as lucky in linux as you did in windows... sorry to hear that. that card can be just as much a headache in windows as it is being for you in linux (actually it can be moreso!). just google "audigy problem" or "audigy pops" or such and you will see that the problem is HORRIBLY prevelant in windows as well.

---

### Post by jerome1232 on 2008-09-12
> **Jadd said:**
> NO offence but come on
What kind of thread title is that?
NO offence but come on
Please, if you want help, stick to some simple rules, such as descriptive thread titles.

+1

Yet I can understand being frustrated with having no sound and it has already been explained that creative doesn't write drivers for linux, it is creative that doesn't support linux not the other way around.

---

### Post by SunnyRabbiera on 2008-09-12
> **jaqie said:**
> In all honesty if you didn't have trouble with your audigy in windows you got lucky. There was a class action lawsuit against creative tech for the EMU10k series of cards (including the audigy) about serious deficiencies in the hardware and driver, IIRC.  So you didn't get as lucky in linux as you did in windows... sorry to hear that. that card can be just as much a headache in windows as it is being for you in linux (actually it can be moreso!). just google "audigy problem" or "audigy pops" or such and you will see that the problem is HORRIBLY prevelant in windows as well.

Aye, I know this from experience.

---

### Post by philinux on 2008-09-12
> **Jadd said:**
> NO offence but come on
What kind of thread title is that?
NO offence but come on
Please, if you want help, stick to some simple rules, such as descriptive thread titles.

+1. Without your pc specs how is anybody supposed to help.

---

### Post by Gildp67 on 2008-09-12
Hers what I got from the lshw

 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1011MiB
     *-cpu
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1850MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a1
             serial: 00:e0:18:fc:34:8d
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 9
                bus info: pci@0000:01:09.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Audigy Game Port
                vendor: Creative Labs
                physical id: 9.1
                bus info: pci@0000:01:09.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 9.2
                bus info: pci@0000:01:09.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@0000:01:0a.0
                logical name: eth2
                version: 10
                serial: 00:0a:cd:14:d9:f6
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.79 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-pci:1
             description: PCI bridge
             product: nForce2 PCI Bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3C920B-EMB Integrated Fast Ethernet Controller [Tornado]
                vendor: 3Com Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth1
                version: 40
                serial: 00:e0:18:f1:8c:d4
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
        *-firewire
             description: FireWire (IEEE 1394)
             product: nForce2 FireWire (IEEE 1394) Controller
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=0 maxlatency=1 mingnt=3 module=ohci1394
        *-pci:2
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV28 [GeForce4 Ti 4200 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 m

---

### Post by philinux on 2008-09-12
Someone fixed the audigy 2 here.

[https://answers.launchpad.net/ubuntu/+question/30828](https://answers.launchpad.net/ubuntu/+question/30828)

---

### Post by MegaJim on 2008-09-12
just for clarity, the relevant part of the lshw printed above is:

```
*-multimedia
description: Multimedia audio controller
product: SB Audigy
vendor: Creative Labs
physical id: 9
bus info: pci@0000:01:09.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
```

---

### Post by phidia on 2008-09-12
There is a note about losing sound when upgrading to hardy [here]("https://help.ubuntu.com/community/SoundTroubleshooting").

---

### Post by Eisenwinter on 2008-09-12
If have you a sound card from the EMU1010 (emu10k) series, go read the post at my signature.

I have an EMU 1212m, and have struggled for a few hours until I finally got sound to work.

---

### Post by kostkon on 2008-09-12
It may be a *PulseAudio* related issue (it can be solved by installing *padevchooser* for a more granular control of the software volume levels and setting the default device for *PulseAudio* and/or by following some parts of this [how-to]("http://ubuntuforums.org/showthread.php?t=789578")), or maybe a problem with the hardware volume levels (it can be solved using *alsamixer*) than a hardware one.

---

### Post by kostkon on 2008-09-12
Also, try to set your card as the default in *Alsa*. Give the command
```
asoundconf list
```
to get a list of all the sound cards of your system. That way you will see how *Alsa* recognises your card, for example it may list it as *emu10k1*.

Thus, to set it as the default (and using as an example the *emu10k1* name) you'll do
```
asoundconf set-default-card emu10k1
```

---

### Post by k3lt01 on 2008-09-12
I don't now why anyone would have a problem with the Audigy card, I have an Audigy Live and it worked out of the box in Feisty, Gutsy, and Hardy clean install each time.

---

