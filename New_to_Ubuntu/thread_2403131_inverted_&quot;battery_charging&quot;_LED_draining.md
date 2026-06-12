---
title: "inverted &quot;battery charging&quot; LED draining CMOS battery"
date: 2018-10-08
forum: New to Ubuntu
---

### Post by mauermoss on 2018-10-08
Hi - info:
Lenovo Thinkpad t430, Now running Xubuntu 18.04 but I was having the same issue when I was running windows 7.

When I unplug the power supply, the battery LED stays lit up (a small green battery shape on the outside of the laptop, even when it is fully shut down, as if it were plugged in). In Power Manager, computer recognizes that it's discharging when unplugged, charging when plugged. So eventually, like if I don't use my computer for a few days or if I turn it off when the battery is low, the computer will keep saying "charging, charging, charging!" but it's not it's actually just draining itself slowly, and the CMOS battery will die and either do a BIOS reset when I plug it and power it on, or more recently, I will have to manually disconnect the CMOS battery and then reconnect it, in order to initiate a BIOS reset and get the computer to power on at all.

SO, I'm not a computer wiz but I want to learn, and I'm curious if there is a way to "flip the switch" manually through the terminal? Or somehow tweak something, or disable that LED - I mean, what else would be draining the battery if the computer is powered off, is not plugged in, but "thinks" it is plugged in? Can I just disable that little light and forget whether it "thinks" it's plugged in or not? Like I said, "power manager" recognizes accurately whether or not it is plugged in.

I guess I need a computers for dummies book, but after having just read about user, kernel, bios, I'm really curious how this works, and I don't want to take it to a repair shop.

Thanks for your time!

---

### Post by mastablasta on 2018-10-08
cmos battery? so you take the laptop apart and then reset the battery on the motherboard?

otherwise the laptop battery will discharge over time. older batteries will discharge faster.

---

### Post by Autodave on 2018-10-08
This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by mauermoss on 2018-10-08
@ mastablasta - its not a matter of batteries discharging over time, it's being drained by running some process which includes illuminating the battery LED, when it thinks that its plugged in, but its actually not.

@ autodave - thanks, will try that

still hoping to find a way to get in there and override the function, or flip it manually when neccessary, since this is a recurring issue.

---

### Post by mastablasta on 2018-10-09
> **mauermoss said:**
> @ mastablasta - its not a matter of batteries discharging over time, it's being drained by running some process which includes illuminating the battery LED, when it thinks that its plugged in, but its actually not.



i still do not understand. if PC is off there is no process running. 

however, there might be something in some memory somewhere that is not emptied. for example my desktop is unable to load sound chip. i found out that the chip somehow stays "occupied" even when PC is off. to solve the issue i unplug the pc and after a about 15 seconds i can hear a click in the speakers. pluging it back on and booting it makes the sound available. sometimes it also requires alsa reload. strange but it works.

---

### Post by rocketshiptech on 2018-10-09
Have you considered just unplugging the LED from the motherboard?

---

