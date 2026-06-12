---
title: "no sound due to root rights?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by sven_wien on 2008-11-09
hi sorry this is my second thread but maybe i have a problem with my root rights as i have no sound on my acer aspire 6920.
im new to ubuntu and it just doesnt work any idea?

thanks

---

### Post by gate on 2008-11-10
Question 1: did it ever work?

Question 2: Are you in the group? Go to System->Administration->Users and Groups->Unlock->Your User->Properties->User Privileges->Use Audio Devices must be checked. If it is not checked, check it and log out and back in.

Question 3: is everything unmuted? Right click on the volume indicator on the top right of the screen and make sure that all of the sliders are up at least half way and all the mute icons are unmuted. If you have a "switches" tab, go to it and make sure they are all checked.

If it has never worked and your user is set up properly, it is probably a driver setup problem or something.

---

### Post by sven_wien on 2008-11-10
i TICKED ALL BOXES AND NO IT NEVER WORKED AS I JUST INSTALLED IT TODAY

---

### Post by gate on 2008-11-10
OK, what kind of computer is it and please open a console and run 'lspci' which should tell me what kind of audio driver you have.

---

### Post by sven_wien on 2008-11-10
i got a acer aspire 6920 
and when i put in the command than it tells me command not found

---

### Post by gate on 2008-11-10
lspci without the quotes

---

### Post by sven_wien on 2008-11-10
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500M GS (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0a:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
0a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
xxl@xxl-laptop:~$

---

### Post by gate on 2008-11-10
Go figure, you have the same sound card I do. I am looking up the instructions for fixing it :)

---

### Post by gate on 2008-11-10
Try these instructions: [https://help.ubuntu.com/community/MacBook_Santa_Rosa#Fix%20Sound](https://help.ubuntu.com/community/MacBook_Santa_Rosa#Fix%20Sound)

---

### Post by sven_wien on 2008-11-10
i tells me command not found

---

### Post by gate on 2008-11-10
You are supposed to add that line to a file and then restart. Read the instructions there.

---

### Post by sven_wien on 2008-11-10
sounds stupid but i cant get it to work hmm

---

### Post by sven_wien on 2008-11-10
maybe u can write it so a newbee understand it pls.
thanks

ps. 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0146
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

---

### Post by gate on 2008-11-10
OK 
```
sudo gedit /etc/modprobe.d/options
```

add 

```
 options snd_hda_intel model=mbp3 
``` 

to the bottom of that file then save it and restart.

---

### Post by sven_wien on 2008-11-10
it tells me cant write press enter

---

### Post by sven_wien on 2008-11-10
aha now it lets me so i goi ng to restart now

---

### Post by sven_wien on 2008-11-10
no change no sound but,

now the sign is gone from the tap and when i try to test sound it tells me:
audiotest wave=sine freq 512 audioconvert....
cant open audioplayer

but my mediaplayer seems to run the file but no sound

---

### Post by gate on 2008-11-10
well, that is all I had. I would double check that everything is unmuted and all the boxes are checked in the switches tab of the volume control.

---

### Post by sven_wien on 2008-11-10
but the volumen control button now its als gone ??

---

### Post by sven_wien on 2008-11-10
anybody else any ideas how to get sound on my acer aspire 6920g?

---

### Post by sven_wien on 2008-11-10
well i hope someone can help me as i realy need sound asap

---

### Post by sven_wien on 2008-11-10
pls

---

