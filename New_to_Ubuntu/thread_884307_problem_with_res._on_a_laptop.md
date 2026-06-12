---
title: "problem with res. on a laptop"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by NeoEIRE on 2008-08-08
hi, just installed 8.04 on my old laptop.... it wont go any highter than 800x600 and i need to get it to 1700x800 something to put it at full screen...


cqan any1 help

---

### Post by mikewhatever on 2008-08-08
Try <gksu displayconfig-gtk>.

---

### Post by NeoEIRE on 2008-08-08
hi, i cant find that????

---

### Post by cdtech on 2008-08-08
Can you open a terminal and type:
```
lspci
```

**P.S.**
copy and paste the output back here.

---

### Post by mikewhatever on 2008-08-08
> **NeoEIRE said:**
> hi, i cant find that????

I may not have been clear,sorry. Open a terminal window (Apps>Accessories>Terminal) and copy/paste **gksu displayconfig-gtk**.

Before you do that, check under System>Admin>Hardware Drivers, if there is a driver available. You may simply need a restricted graphics driver installed.

---

### Post by adamogardner on 2008-08-08
> **cdtech said:**
> Can you open a terminal and type:
```
lspci
```

**P.S.**
copy and paste the output back here.

whats lspci do?

---

### Post by mikewhatever on 2008-08-08
> **adamogardner said:**
> whats lspci do?

It lists the pci devices present. The one we may be interested is you graphics card.

---

### Post by NeoEIRE on 2008-08-09
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
chris@chris-laptop:~$ 


sorry for the delay

---

### Post by NeoEIRE on 2008-08-09
> **mikewhatever said:**
> I may not have been clear,sorry. Open a terminal window (Apps>Accessories>Terminal) and copy/paste **gksu displayconfig-gtk**.

Before you do that, check under System>Admin>Hardware Drivers, if there is a driver available. You may simply need a restricted graphics driver installed.

no i already checked that as i have another pc with nvidia that had to be enabled


1mo for the rest


the card is a trident cyberblade    (old toshiba portege)

and it failed the 1024x768 screen lcd test....

---

### Post by cdtech on 2008-08-09
Ok, lets see if you can do this:
reboot your system and when you see the GRUB boot screen press the "esc" key. Use your arrow key and select the "recovery mode" option to boot.

When you get to the login prompt, enter your user name and password to login. Once your loged in enter this on the command line:
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask for a password, just enter your user password.
Reboot........

---

### Post by NeoEIRE on 2008-08-09
> **cdtech said:**
> Ok, lets see if you can do this:
reboot your system and when you see the GRUB boot screen press the "esc" key. Use your arrow key and select the "recovery mode" option to boot.

When you get to the login prompt, enter your user name and password to login. Once your loged in enter this on the command line:
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask for a password, just enter your user password.
Reboot........

when i turned her on.... and everything loaded after picking recovery mode... i got 4 choices
i picked boot normail and sighned in....


then i did the above sudo command and got this....

chris@chris-laptop:~$ sudo dpkg-reconfigure xserver-zorg
[sudo] password for chris: 
Package `xserver-zorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-zorg is not installed.
chris@chris-laptop:~$

---

### Post by Shanoes on 2008-08-09
chris@chris-laptop:~$ sudo dpkg-reconfigure xserver-zorg

Looks like you have a typo there ;) It should be

chris@chris-laptop:~$ sudo dpkg-reconfigure xserver-xorg

---

### Post by NeoEIRE on 2008-08-09
> **Shanoes said:**
> chris@chris-laptop:~$ sudo dpkg-reconfigure xserver-zorg

Looks like you have a typo there ;) It should be

chris@chris-laptop:~$ sudo dpkg-reconfigure xserver-xorg

oops... my bad... redone it and it gave me keyboard options....

went through them and played with the test before and all i can get is a full screen with the box saying keep these settings in clear view... but the rest of the screen looks like a mess of pixels.,...


sorry 4 delay... fell asleep but im here now...

---

