---
title: "Can't shutdown."
date: 2008-06-27
forum: New to Ubuntu
---

### Post by bob_hilton on 2008-06-27
I cant shutdown by pressing the exit icon on my gnome bar. if i press it nothing at all happens. 

i can only currently shutdown by pressing ctrl+alt+bkspace and shuting down from the login screen.

Any ideas?

---

### Post by Dylock on 2008-06-27
Not sure why the button isn't working for you.

But you can do a shutdown from the terminal.
The most common form is: 
```
sudo shutdown -h now
```

the -h flag says to halt the system after shutdown and now says to do it now (you can time delay it) You can find more information on the man page.

---

### Post by bhadotia on 2008-06-27
Does the log out window appear when you do ctrl+alt+delete?

---

### Post by bob_hilton on 2008-06-27
..erm yes-ish. It brings up the menu and gives hibernate, logout etc but not shutdown?

---

### Post by st33med on 2008-06-27
> **bob_hilton said:**
> ..erm yes-ish. It brings up the menu and gives hibernate, logout etc but not shutdown?

Sounds like your computer wants to make the Guinness World Record for the longest uptime :).

Could you give us your hardware? Just type in the terminal:
```
lspci
```
and post here.

Also, does trying the same thing on the LiveCD work?

---

### Post by jakupl on 2008-06-27
you can also alternatively hold down the Alt+SysRq (Print Screen) keys and type in R E I S U O

Here is some reference.

[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by st33med on 2008-06-27
> **jakupl said:**
> you can also alternatively hold down the Alt+SysRq (Print Screen) keys and type in R E I S U O

Here is some reference.

[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Or REISUB. But, this guy wants to do the GUI shutdown and I would think it would be better than tapping these keys every time.

---

### Post by jakupl on 2008-06-27
> **st33med said:**
> Or REISUB.

Ending it with "B" will make the system reboot, ending it with O will make it shut down.

> **st33med said:**
>  But, this guy wants to do the GUI shutdown and I would think it would be better than tapping these keys every time.

Ofcourse, i'm just sayin'.
But it is easier than

 
```
sudo shutdown -h now
```

.. maybe not healthier though.

---

### Post by bob_hilton on 2008-06-28
Print from lspci;

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

Yeah, I've learned all about shuting down through the terminal now! I'm not the only one using this machine though and i need a GUI shutdown too.

---

### Post by jakupl on 2008-06-28
What computer are you using?

---

### Post by bob_hilton on 2008-06-28
A home built desktop. Can I just ask what people are looking for in my hardware? 

The story is that it was working fine on hardy for around 1-1.5 weeks but it unexpectedly gave up. I can get the menu/window/panel thing by pressing ctrl+alt+del but it has no shutdown option (all other logout, hibernate etc are still there) and can shutdown using the terminal. However..

what i really want to do is restore the functionality of the launcher on the gnome bar or add a new option to shutdown graphically. My girlfriend also uses this machine and she's no use with a terminal!

anyone who's had a similar problem or can point me in a general direction would be a massive help!

---

### Post by bob_hilton on 2008-06-28
**bump**

---

