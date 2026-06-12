---
title: "wireless keyboards stopped working in grub"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by gandalf3 on 2012-07-29
like it says in the title.
(it least i think its grub.. the thing where you pick what OS to boot when you first turn on the computer)
they used to work fine, (i have tried two) but now nothing happens when i press a button.
it still sometimes works, but rarely.:confused:
it all works fine when i get to the login screen though.
help much appreciated.. i have a old PS2 keyboard i can use to get past it, but im used to the wireless working and its quite annoying when i can't get to the Ps2 fast enough.. lol

---

### Post by arochester on 2012-07-30
Wireless keyboards are often USB.

Look in your BIOS to make sure that you have USB enabled.

---

### Post by gandalf3 on 2012-07-30
yes, both keyboards are usb.
i checked the bios, and it said something like this:
connected devices

two keyboards
one mouse

 usb 1.0 controller ENABLED
usb 2.0 controller ENABLED
usb 2.0 controller speed FULLSPEED
HCSI (thats not it.. i'll edit once i check again.. it's close though..) handoff mode  ENABLED


plus it was working before, it just started not working intermittently, and now it's only working very rarely.
and when i got into the bios, NONE of the keyboards would work, until after trying them all i just pressed a bunch of keys on the PS2 keyboard and it started working (only the PS2 though)

---

### Post by Jay Christnach on 2012-07-30
I had the same problem and I found a setting in the BIOS (a more advanced one) I could change. I could choose between "usb keyboard controlled by" "bios" or "OS". Setting it to BIOS, which btw also corresponded to the safe default settings fixed the problem.
(I cannot recall how this setting got changed, maybe it was myself, but I can't remember)

Best greetings!

---

### Post by audiomick on 2012-07-30
I don't know if this has changed, but it used to be the case a couple of years back that there was often a thing in the bios called "legacy USB" or somthing along those lines. Setting this to "on" slowed down the bios loading phase, but caused usb drivers to be loaded so that the usb keyboard and mouse stuff was working by the time grub started. I had to turn it on to get my USB keyboard working during boot-up.

---

### Post by NikTh on 2012-07-30
> **audiomick said:**
> I don't know if this has changed, but it used to be the case a couple of years back that there was often a thing in the bios called "legacy USB" or somthing along those lines. Setting this to "on" slowed down the bios loading phase, but caused usb drivers to be loaded so that the usb keyboard and mouse stuff was working by the time grub started. I had to turn it on to get my USB keyboard working during boot-up.

Hi ,
+1 . 

had this problem in the past and fixed by enabling the Legacy Usb support in Bios.

Thanks

---

### Post by gandalf3 on 2012-08-01
> **Jay Christnach said:**
> I had the same problem and I found a setting in the BIOS (a more advanced one) I could change. I could choose between "usb keyboard controlled by" "bios" or "OS". Setting it to BIOS, which btw also corresponded to the safe default settings fixed the problem.
(I cannot recall how this setting got changed, maybe it was myself, but I can't remember)

Best greetings!
i didn't see anything like that.. :(
 and legacy USB is on, still not going..:confused:
why would it just stop working if it was working before?

---

### Post by gandalf3 on 2012-08-04
AHA!!
:D
when my new USB sound card is plugged in, the wireless/USB keyboards don't work in grub.
but when it's NOT plugged in..
i tried it twice, worked both times..
now i could just unplug it when i boot, then plug it back in, but is there some way i can get the keyboard to work WITH the soundcard in?

---

### Post by gandalf3 on 2012-09-07
strange, also when i UNplug something, (for example my joystick) it won't work. the only thing this hasn't happened with is a usb stick.
why is this happening? :confused:

---

### Post by windowslicker on 2012-11-09
Thanks to this thread I've finally managed to get mine working at GRUB.

Logitech K260 USB keyboard.

Phoenix BIOS

Integrated peripherals> On board device set up> USB keyboard support> enable

---

