---
title: "First Time Linux User"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by funkfrisk on 2013-07-16
Hello everyone,

           So I've been trying out so many distros for my hp tc4200 tablet pc and i've decided to stick to ubuntu 12.04. At first I wasn't, but the more I use it the better it works. For instance, when I tried to resart it would fail and say something about  ipw2200 and say command line timed out and now it restarts fine. Both internet connections work fine, the pen and screen works but I don't think all of the functions are. It has a built in mic and light sensor around the screen that doesn't work that I would like to. Is there anything I should do after a fresh install and how could I cofigure everything to where it works like it should? I like this OS a lot and I'm not trying to install any other distros. I've been in distro hell for almost a week and I'm finally satisified. Thanks to everyone who put in they're time and hard work towards this awesome project. Maybe one day I can contribute and return the favor.

---

### Post by newbie-user on 2013-07-17
At this point, your next step probably would be to figure out what hardware is in your tablet pc. Run the command
```
lspci
```
to see what hardware is detected. Then you can go about finding configurations or drivers to get everything working.

---

### Post by Bashing-om on 2013-07-17
funkfrisk; Hi ! Welcome to the forum.

On your fresh install have you ran updates to get all applications current ?
Terminal codes (ctl+alt+t yields a terminal) :
```

sudo apt-get update
sudo apt-get upgrade

```
sudo == Super User DO, requires your password, and will get no response to the screen.

Once you are updated, we can look at any remaining problems on an individual basis.

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

### Post by funkfrisk on 2013-07-18
Haven't done that yet. Thanks for letting me know. I'm a do it right now.

---

### Post by funkfrisk on 2013-07-18
Hi Bashing-om. I've done the upgrade and afterwards it hung up trying to restart saying speech dispatcher disabled. I disabled it using BUM and it restarts fine. Would this have to do with a built in mic? Because I don't think it's working. I don't really need the mic, I would just like to get it working for the fun of it.

---

### Post by funkfrisk on 2013-07-18
I ran the command and here's what I got:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
10:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

Could you suggest anything I can do? I forgot I had a sd card slot. Maybe it's because it doesn't work. lol

---

### Post by Bashing-om on 2013-07-18
funkfrisk; Morning !

Ok all updated,, and looking good !.."lspci" advises all kinds of stuff is loaded and ready to go to work.
So what is not presently working ... after a (re-)boot ??
In all likely hood is but a matter of making sure the appropriate drivers for the external (to the Operating System ) devices are loaded and recognized.

One thing at a time and it will all get done.

[INDENT][INDENT]a process of learning[/INDENT][/INDENT]

---

