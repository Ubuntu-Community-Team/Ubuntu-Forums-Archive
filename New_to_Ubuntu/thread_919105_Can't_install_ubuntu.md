---
title: "Can't install ubuntu"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by LittleIrishDevil on 2008-09-13
I'm trying to install ubuntu 7.04 from a cd on my acer running vista. It's a brand new machine.

I get the cd to boot and get the list of alternatives. I choose to install and it begins process but then goes to black screen and reads ...

BusyBox v1.1.3 (Debian 1:1,1,3-3ubuntu3) built-in shell (ash)
Enter 'help' for a list of built in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)


come on guys, any suggestions ....

---

### Post by icheyne on 2008-09-13
7.04 is getting quite old now. Best to download and burn the latest Live CD.

---

### Post by natman on 2008-09-13
When you Burn an 8.04 cd do a disc check on boot up just to make sure your discs are not bad or anything

---

### Post by jeaves on 2008-09-13
Having this same problem with 8.04 currently. I've verified my Bios settings, used Safe Graphics mode and it's still dumping me straight to BusyBox. 

removing the splash page and adding in "noapic" gets me some more info, but I'm sorta new at this so I'm not sure what I'm looking for. 

It's been scrolling:

ata5.00: stats: {DRDY} 
ata5: soft resetting link
ata5.00: configure for PIO0
ata5: EH complete
ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen 
ata5.00: cmd a0:00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
         cdb 12 00 00 00 25 00 00 00  00 00 00 00 00 00 00 00 
         res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

Here's my specs: 

Abit AB9 PRO motherboard
Intel Core2 Duo proc
Drives (all western digital)
WDC - WD1600AAJS-00PSA
WDC - WD10EACS-00ZJB0
WDC - WD5000AAKS-00TMA
Nvidia GeForce 8800 GTS graphics card

.... the REALLY weird thing is that it booted to the graphical installer a few times but locked up, or wouldn't see the hard drive. 
I've tried a couple different disks too... I'm really lost.

---

