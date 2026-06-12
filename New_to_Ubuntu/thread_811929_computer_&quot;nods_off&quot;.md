---
title: "computer &quot;nods off&quot;"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by ozarkerbob on 2008-05-29
ubuntu 8.04, acer aspire 1700, 1.6 G processor, 1 G ram.

frequently, about every 5 to 10 minutes, my computer sort of nods off.  Keystrokes don't appear if I am typing at the time. After about 3 to 4 seconds of non-response, the screne goes gray.  Then about 10 seconds later it comes back to life.  Interestingly, the keystrokes I enter in the first few seconds, which don't show at the time, are there when it comes back to life.  The mouse remains active during the "nap".

---

### Post by shifty_powers on 2008-05-29
few more specs would be handy. the screen going grey is a compiz effect, when the computer is waiting for a non-responsive program etc...

what is the graphics card etc...

---

### Post by ozarkerbob on 2008-05-29
> **shifty_powers said:**
> few more specs would be handy. the screen going grey is a compiz effect, when the computer is waiting for a non-responsive program etc...

what is the graphics card etc...

I was afraid you would ask me that. I don't know. is there a place, application or what ever that will tell me?

---

### Post by shifty_powers on 2008-05-29
right.

for a start... ;)

go applications>accessories>terminal and type in

```
lspci
```

and post the output ;)

---

### Post by ozarkerbob on 2008-05-29
here it is
--------------------
bob@bob-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
bob@bob-laptop:~$

---

### Post by Dr Small on 2008-05-29
Oh boy. Intel.

---

### Post by ozarkerbob on 2008-05-29
so, the solution is to just get some heroin and "nod off with the computer?
:lolflag:

---

### Post by arpanaut on 2008-05-29
When I first saw this I read it as "computer USER nods off"... 

Was gonna say, "Man, That's a personal problem." eh?

Honestly though your specs look doable, Dpn't know didly about setting up Intel laptops, So I'll leave it to those who do know...

---

### Post by ozarkerbob on 2008-05-30
thanks any folks, it is a minor irratation at worst.

---

### Post by arpanaut on 2008-05-30
In a terminal type in "top" and it will show what is eating up your cpu & ram.
Also take a look at your Power Mgt. setings, maybe turn off some Services you might not need running, look at your CPU Scaleing settings?
Compiz can eat up a lot or resources, Try disableing that and see if that helps.
I had this issue with Gutsy but not with Hardy.... go figure? With many others it's the other way around.

Hope you work it out!

---

