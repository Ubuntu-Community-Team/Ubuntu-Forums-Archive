---
title: "[SOLVED] How do i know what graphics card i have?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-25
Do not care if it is gtk or cli.

---

### Post by Ryadt on 2008-07-25
type ```
lshw -C Display
```

---

### Post by gimlithedwarf on 2008-07-25
```
lspci
``` then look for a component which has something like "ati" or "nvidia" in it

---

### Post by Oldsoldier2003 on 2008-07-25
```
lspci | grep Display
```
works if you have a pci video card
```
sudo lshw -C Display
``` also works and is probably the best choice to use.

---

### Post by cristo-father on 2008-07-25
None of them say the model...

```
diastopher@diastopher-desktop:~$ sudo lshw -C Display
[sudo] password for diastopher: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
diastopher@diastopher-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation ICH10 PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation ICH10 PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation ICH10 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
00:1f.5 IDE interface: Intel Corporation ICH10 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442
01:00.1 Audio device: ATI Technologies Inc Unknown device aa30
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)
05:02.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
diastopher@diastopher-desktop:~$ sudo lspci | grep Display
diastopher@diastopher-desktop:~$ 

```

---

### Post by gimlithedwarf on 2008-07-25
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442 would be your graphics card, however ubuntu cannot identify what it is

---

### Post by ET! on 2008-07-25
you can download gpuz software and use wine to run it in linux

---

### Post by Oldsoldier2003 on 2008-07-25
01:00.0 *VGA compatible controller*: ATI Technologies Inc Unknown device 9442 is the video controller.

edit: nvm I seem to be typing too slow today and gimlithedwarf already answered :)

---

### Post by Kevbert on 2008-07-25
If the display card came with the PC, (not custom built) what's the PC ? It could be a HD 4800 series card.

---

### Post by LowSky on 2008-07-25
What brand and model computer we might be able to figure it out from that alone.

---

### Post by gimlithedwarf on 2008-07-25
> **oldsoldier2003 said:**
> 01:00.0 *vga compatible controller*: Ati technologies inc unknown device 9442 is the video controller.

Edit: Nvm i seem to be typing too slow today and gimlithedwarf already answered :)

:p

---

### Post by cristo-father on 2008-07-25
> **LowSky said:**
> What brand and model computer we might be able to figure it out from that alone.

I want to know it through an app, it can run through wine.
BTW: GPUZ does not work in wine.

---

### Post by gimlithedwarf on 2008-07-25
if you haven't changed the graphics card and you know what model/make of computer you have you can just google the information to find out. Why do you need an app?

---

### Post by cristo-father on 2008-07-25
> **gimlithedwarf said:**
> if you haven't changed the graphics card and you know what model/make of computer you have you can just google the information to find out. Why do you need an app?

I need more reasons to believe that i have what i was told to have.

---

### Post by gimlithedwarf on 2008-07-25
if you have windows on your machine you can boot that up and go start->run and type dxdiag which might tell you. Failing that you could open up the case and see if you can find a label telling you what the graphics card is

---

### Post by cristo-father on 2008-07-25
> **gimlithedwarf said:**
> if you have windows on your machine you can boot that up and go start->run and type dxdiag which might tell you. Failing that you could open up the case and see if you can find a label telling you what the graphics card is

Do not have windows(Lol...why would i use windows? I am not a masochist).
I will not open my case...
Any other ideas?

---

### Post by gimlithedwarf on 2008-07-25
if you have a laptop not wanting to open your case is understandable, however on a desktop you shouldn't have a problem. I can't think of any other software method for hardware detection other than the ones we have done here

---

### Post by ET! on 2008-07-25
> **gimlithedwarf said:**
> if you have windows on your machine you can boot that up and go start->run and type dxdiag which might tell you. Failing that you could open up the case and see if you can find a label telling you what the graphics card is

if he had windows he could have used gpuz

---

### Post by gimlithedwarf on 2008-07-25
we've already established that he doesn't have windows

---

### Post by overdrank on 2008-07-25
Hi if you have a internet connection update the pci ids
```
sudo update-pciids
```

---

### Post by ET! on 2008-07-25
the information says that your card's memory width is 64 bit so it could not be a 4850 or 4870 maybe a 1900 series

---

### Post by cristo-father on 2008-07-25
> **ET! said:**
> the information says that your card's memory width is 64 bit so it could not be a 4850 or 4870 maybe a 1900 series

So it can not be a 4850??? That is what i was told to have?

---

### Post by Kevbert on 2008-07-25
If you take a look at this [[COLOR="Red"]site[/COLOR]]("http://www.overclockersclub.com/reviews/powercolor_hd4850/") it gives you details on what it looks like.  I've been looking at the HD4870 which has been mentioned in another post (and is similar).

---

### Post by cristo-father on 2008-07-25
> **Kevbert said:**
> If you take a look at this [[COLOR="Red"]site[/COLOR]]("http://www.overclockersclub.com/reviews/powercolor_hd4850/") it gives you details on what it looks like.  I've been looking at the HD4870 which has been mentioned in another post (and is similar).

The box looks like that, but that does not prove that it is in my case.

---

### Post by cristo-father on 2008-07-25
Do not tell me i have to install windows....Come on....

---

### Post by Kevbert on 2008-07-25
Does the card look like the pictures ?  There should also be an id label on it somewhere.  On the ATI website there are no drivers for the HD4800 series listed, but they're very new.  Didn't you get a driver CD with the card ?

---

### Post by cristo-father on 2008-07-25
> **Kevbert said:**
> Didn't you get a driver DVD with the card ?

Yes. Can i install the drivers from the dvd(on ubuntu)?

---

### Post by ET! on 2008-07-26
did you find out what card do you have ????

---

