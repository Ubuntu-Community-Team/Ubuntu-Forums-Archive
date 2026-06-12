---
title: "Making Ubuntu look like OSX Leopard?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by VampiricFang on 2008-05-12
I've pretty much got everything down except the dock. I just have to keep the terminal window open, lest I lose my title bar, I really don't mind that. If anyone could give me an in-depth installation guide on how to install the dock for the OSX Leopard, that would be awesome.

Many thanks in advance!

EDIT: I switched from Vista to Ubuntu just last night, so take it easy with the lingo. :P

---

### Post by tjwoosta on 2008-05-12
you dont need to keep a terminal open for anything


press alt-f2 (put your command in there and press enter)

as for the dock go to System-Administration-Synaptic Package Manager and search AWN (avant window navigator)

also to make commands run when you log on  go to System-Preferences-Sessions

click add and put your command in the command box

---

### Post by VampiricFang on 2008-05-12
> **tjwoosta said:**
> you dont need to keep a terminal open for anything


press alt-f2 (put your command in there and press enter)

as for the dock go to System-Administration-Synaptic Package Manager and search AWN (avant window navigator)

also to make commands run when you log on  go to System-Preferences-Sessions

click add and put your command in the command box

Thanks, that solved the title bar thing, but when I click on Awn manager in 
System-Preferences nothing happens, what's up?

---

### Post by ad_267 on 2008-05-12
Make sure you have the awn-manager package installed. Also if you go to System - Preferences - Sessions and add the command avant-window-navigator to startup then the awn dock will start automatically when you log in.

---

### Post by tjwoosta on 2008-05-12
> Thanks, that solved the title bar thing, but when I click on Awn manager in 
System-Preferences nothing happens, what's up?

go to Applications-Accessories-Avant Window Navigator


the one that is in Preferences is to change the preferences for awn (can also be done by right clicking on the corner of the dock)

---

### Post by VampiricFang on 2008-05-12
Hey, it's working! But it looks...weird..it's alittle offscreen. My resolution is usually at 1440x900, am I running at a different resolution or something...? I'm such a linux noob... *shame*

EDIT: I am running at 1440x900, but icons on the desktop are going off screen...weird.

---

### Post by tjwoosta on 2008-05-12
what do you mean by going offscreen?  

can you see your gnome panel?

---

### Post by VampiricFang on 2008-05-12
Yeah, the panels are on screen fine, but the icons are able to go part way off the screen, unless I have it one space away. I thought it was a resolution issue at first.

---

### Post by tjwoosta on 2008-05-12
hmm.. that is strange 

sry i thougt i had a solution but i guess i was thinking of something else (i though for a minuter you could offset the dock from the center)

---

### Post by VampiricFang on 2008-05-12
Meh, it's not that far off screen, thanks though. I'm getting kind of tired, so yeah...I also just noticed that my computer won't connect to the internet if I disconnect it from the wired connection....I have a wireless card in my laptop...I play world of warcraft two stories up normally. :confused:

---

### Post by tjwoosta on 2008-05-12
ok i think i have a quick and easy solution for you

go to terminal and type this
```

gconf-editor

```

when the editor pops up go to "apps" then to "avant window navigator" then to to "bar"

on the right you will see a key that says "bar_pos"  the default value is 0.5 but change it, play around with it for minute (try 0.7 or 0.3 ) 

i just did this myself and i can make my bar offset to wherever i want it



as for having no wireless, chances are that you have to manually install the correct drivers 

what is the make and model of your wireless card?

when you get the chance post the output of theese two commands

```
lspci
```
and
```
lsusb
```

---

### Post by VampiricFang on 2008-05-12
> **tjwoosta said:**
> ok i think i have a quick and easy solution for you

go to terminal and type this
```

gconf-editor

```

when the editor pops up go to "apps" then to "avant window navigator" then to to "bar"

on the right you will see a key that says "bar_pos"  the default value is 0.5 but change it, play around with it for minute (try 0.7 or 0.3 ) 

i just did this myself and i can make my bar offset to wherever i want it



as for having no wireless, chances are that you have to manually install the correct drivers 

what is the make and model of your wireless card?

when you get the chance post the output of theese two commands

```
lspci
```
and
```
lsusb
```
Awesome, that fixed the AWN thing, thanks! 

As for my wireless issue, here's what Terminal gave me....
For the command lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

For the command lsusb:

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by tjwoosta on 2008-05-12
ok so this must be your wireless card
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

so you should start searching for drivers for a Broadcom BCM4328

here is a link to a thread i found that should have everything you need to get wifi setup

note: this is the link to the keyword search for BCM4328,  just click the title of the post and it will bring you to the actual thread

[http://ubuntuforums.org/search.php?searchid=41068379]("http://ubuntuforums.org/search.php?searchid=41068379")


but i actually have to get going to bed now so ill be back on tomorrow night if you still need any help

---

### Post by VampiricFang on 2008-05-12
I'm going to have to download more things right? I was looking at webpages, and it was saying I'd need fwcutter or something.

---

### Post by tjwoosta on 2008-05-12
yea its possible  (i have a realtek card so my setup is different than what you will have to do)

---

### Post by skymera on 2008-05-12
The best way to make your PC look like a Mac is [here]("http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?mco=47638CE4&fnode=home/shop_mac/software/apple&nplm=MB427Z/A")

But you can folloow this guide here:

[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

---

