---
title: "How do I create a hardware profile in Ubuntu 8?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Vistawho? on 2008-08-13
Hi guys, Linux newbie, Ubuntu newbie here too.
How do I create a hardware profile for my system using Ubuntu 8.04?
I can't get the special desktop effects to work but I think it is because I don't have the correct drivers for my on-board video.

---

### Post by Dedoimedo on 2008-08-13
Hello,
You seem to have two problems.
Do you require hardware profiles regardless of the effects problems, or do you want them because you can't get the special effects to work? In other words, if you solved the effects problem, would you still require the hardware profiles?
Dedoimedo

---

### Post by Martje_001 on 2008-08-13
What onboard videocard do you have? Please post the output of```
sudo lshw
```
in a terminal. And please past it between code-tags.

---

### Post by Vistawho? on 2008-08-13
This is the result of the code that I entered.
 ```
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 979MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=32 module=pata_sis
        *-multimedia:0
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:14:85:cb:f3:7f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.3 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
        *-storage
             description: RAID bus controller
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=sata_sis latency=128 module=sata_sis
        *-multimedia:1
             description: Multimedia audio controller
             product: CM8738
             vendor: C-Media Electronics Inc
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci

```
In answer to needing a hardware profile, I thought it might have been beneficial if I need drivers.
This is a spare machine that I wanted to try Ubuntu on. It has a tiny HDD (6 gig)
Cheers

---

### Post by Vistawho? on 2008-08-13
Sorry guys. I am not aware of the "Code-tags" mentioned. I hope the post isn't too big.:(

---

### Post by Martje_001 on 2008-08-13
Just type **[ CODE ]** (without spaces) and paste the code. Then close it with **[ / CODE ]** (withoutspaces).

This is your videocard:
```
*-display UNCLAIMED
description: VGA compatible controller
product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
vendor: Silicon Integrated Systems [SiS]
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 66MHz
capabilities: vga_controller cap_list
configuration: latency=0
```

Can we have the output of
```
cat /etc/X11/xorg.conf
```
also? This time, try it with the code-tags as described above! :)

---

### Post by nothingspecial on 2008-08-13
You can also wrap code tags around part of your post by highlighting the appropriate text then clicking the code button.

[ATTACH]81413[/ATTACH]

---

### Post by 3rdalbum on 2008-08-13
From some quick Google use, it doesn't look like Compiz will work on your integrated SiS graphics.

You have an AGP port though. You could have a look around and see if you can get a graphics card that fits into AGP; there are very few around (maybe even none) but a second-hand jobbie should do fine. Just as long as it's got an Nvidia graphics processor. ATI-based ones are okay too, but the Nvidia ones work better with Linux.

---

### Post by Vistawho? on 2008-08-13
I'd just like to add guys, I really do appreciate the help you are giving me.
Up until now, I have been using Windows (XP) and I am looking for an alternative in Ubuntu.
My Ubuntu system seems to load and run faster. 
Linux, for me, certainly is different but I think it's just a matter of getting used to something else.

Thanks again

---

### Post by Vistawho? on 2008-08-13
Ok Guys, this is the result of entering the code as requested:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

```

---

### Post by Martje_001 on 2008-08-14
You could try this (I don't guarantee it's going to work!):
```
gksudo /etc/X11/xorg.conf
```
and then change these lines:
```
        Option  "AIGLX" "off"
        Option  "Composite" "Disable"
```
to:
```
        Option  "AIGLX" "on"
        Option  "Composite" "Enable"
```

Before you do that, make a backup by entering these commands:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk
```
Then restart your computer (or press CTRL + ALT + BACKSPACE, but that's not recommended).

If you're able to start up, test if compiz-fusion works or not by entering this command:
```
compiz --replace
```

If you're unable to start up (i.e. get the GUI running) press CTRL + ALT + F1, login, and enter this command:
```
sudo cp /etc/X11/xorg.conf.bk /etc/X11/xorg.conf
```
Now, restart your computer again and everything is back to normal.

---

### Post by Vistawho? on 2008-08-14
Since your last message I bought an Nvidia video card and installed it.

I still can't get the 3D cube to work though.
I entered the code you suggested and this is the message I received.
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
```

---

### Post by Vistawho? on 2008-08-14
I meant to say, I entered the last code you suggested:)

---

### Post by nothingspecial on 2008-08-14
What have you done to get compiz working so far?

---

### Post by Vistawho? on 2008-08-14
Well, I've done a couple of things.
Mainly I followed these instructions found here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 

I still haven't been able to see any 3D graphics but it has helped a lot.

---

### Post by Vistawho? on 2008-08-14
I think that when I installed the Nvidia card, it automatically found the drivers for it and removed others that I am not using. I tried ```
gksudo /etc/X11/xorg.conf
```and it returned nothing.
I think I saw something to do with xorg being removed at the time.
I really appreciate your help on this.
I am also searching the forum for any possible solutions to getting the 3D stuff up and running.
I hope I don't mess anything up:)

---

### Post by Vistawho? on 2008-08-15
Hi Nothingspecial.
I thought I would add the fact that when I go to "System - Preferences - Appearance - Visual Effects" I get an error message "The composite Extension is not available" when I click on either "Normal" or "Extra"
Does this mean I need to install or activate something else?

Cheers

---

### Post by Martje_001 on 2008-08-15
So, now you have a Nvidia card? Good!

Install **envyng** and **envyng-gtk** and start Envyng (it's in your menu) and install the drivers for your videocard. Good luck!

---

### Post by Vistawho? on 2008-08-15
Hi Martje_001.

Did as you said. Worked a treat! Now I will play with this for a while and see what it can do.
Is this what I needed to get the 3D cube working?

Thanks heaps:KS

---

### Post by nothingspecial on 2008-08-15
You need to check the custom box in system > preferences > appearance > visual effects.

---

### Post by nothingspecial on 2008-08-15
To get the cube open system > preferences >advanced desktop settings and click on the general options box.
Click on the third tab and change the first option to 4 like so -
[ATTACH]81628[/ATTACH]

Then click back and put a tick in both desktop cube and rotate cube
[ATTACH]81629[/ATTACH]

Press your middle mouse button anywhere on your desktop and drag

EDIT got my pictures the wrong way round but you get the idea.

---

### Post by Vistawho? on 2008-08-15
Thanks again Nothingspecial.

I have the cube working of sorts.
It fills the screen so you can't tell it's a cube until you rotate it.
CAn you make it smaller so that it doesn't fill the screen?

---

### Post by nothingspecial on 2008-08-15
If you click on the rotate cube thing that you put a tick next to and click the general tab. The bottom option is called zoom. The further you move the slider to the right the smaller your cube will be when you rotate.

---

### Post by Vistawho? on 2008-08-15
Thanks again. Now I can fiddle to my heart's content.
It certainly was a journey getting here.
I hope no-one asks how it was done 'cause I simply couldn't tell them.
Was it you that mentioned Nvidia cards were scarce?
I'm in Oz and the local computer shop had 3 for me to choose from.
But then again, we sometimes take a little while to catch up with the rest of the world.

---

### Post by nothingspecial on 2008-08-15
> **Vistawho? said:**
> Thanks again. Now I can fiddle to my heart's content.
It certainly was a journey getting here.
I hope no-one asks how it was done 'cause I simply couldn't tell them.
Was it you that mentioned Nvidia cards were scarce?
I'm in Oz and the local computer shop had 3 for me to choose from.
But then again, we sometimes take a little while to catch up with the rest of the world.
 Ha, ha. I`m what I think you call a whinging pom. Maybe you`ve got all our Nvidia cards. Glad you got it sorted.:guitar:

---

