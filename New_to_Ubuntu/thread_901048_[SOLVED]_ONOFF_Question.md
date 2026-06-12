---
title: "[SOLVED] ON/OFF Question"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-08-26
On my computer the power switch on the caes is shot.  I tried contacting the manufacturer and they told me a switch was 3.00 plus 10.95 P/H.  I am not about to pay 13.95 for a new switch.

My question is will it hurt to never shutdown the system.  It has been running straight for the past year.  I have plenty of air flow since I am using 7 high output fans.  Is there a chance I ham going to hurt the machine since it is an old AMD K6-III 450 system.

Donnie

---

### Post by ntu on 2008-08-26
My understanding is that the machine may well last longer if it is running all the time as the main stress on the system is switching it on and off.

---

### Post by iaculallad on 2008-08-26
> **alienexplorers said:**
> On my computer the power switch on the caes is shot.  I tried contacting the manufacturer and they told me a switch was 3.00 plus 10.95 P/H.  I am not about to pay 13.95 for a new switch.

My question is will it hurt to never shutdown the system.  It has been running straight for the past year.  I have plenty of air flow since I am using 7 high output fans.  Is there a chance I ham going to hurt the machine since it is an old AMD K6-III 450 system.

Donnie

It won't probably hurt your system, just be sure that you have a good power supply installed. The last time I checked my FTP server (Clone/Generic PC actually), it's been running for 5 months:18 days for now (it's been (as I use HEC 500W power supply) without any shutdown.

---

### Post by Too Late on 2008-08-26
I don't even remember when I've used my power switch last time. And I shutdown and start the computer every day. Well, the shutdown is obvious. But if you want to start your computer without a power switch, go to BIOS and check if there's a keyboard boot option. I think most of mobos have such a feature. Computers with AT power supply might not have that, but I think yours is ATX, since it's not *so* old.

And the traditional power switch is a very simple "device", it's just an ordinary switch, which connects two wires together. So it shouldn't be impossible to start the computer without a working switch in the case.

And lastly, you can still spin-down your hard drives (which are probably the "less durable" parts of a machine, among the PSU and fans) with the [hdparm](http://ubuntuforums.org/showthread.php?t=900405) command in linux.

---

### Post by alienexplorers on 2008-08-26
Thanks for all your helpfull information.  I am going to check in to that hdparm command to see if I can write scripts to turn it off at night and on during the day.

---

