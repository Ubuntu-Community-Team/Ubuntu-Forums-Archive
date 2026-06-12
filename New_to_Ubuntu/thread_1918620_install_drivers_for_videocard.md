---
title: "install drivers for videocard"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by Newbehans on 2012-02-01
My videocard died. The repairman can replace it, butdoes not know how to install the drivers. Neither do i as amatter of fact. Who can help me

---

### Post by mikewhatever on 2012-02-01
...and what's wrong with the old ones? If the new card is the same as old, same driverses should work. How many drivers do you use, by the way?

---

### Post by seawolf167 on 2012-02-01
How did you originally install the drivers for your device?
Is the new video card the same as the old one?
What is the make/model of the card?

---

### Post by Newbehans on 2012-02-02
No it is not the same card.The old one dates from pre hdmi times, and the new one is hdmi.I am an old sod who thinks that **** films don't get better with crisp images so have never bothered with updating my videocard before it croaked. The new card is an Asus EAH5450SilentDM2, burt of course the manufacturer thinks I use windows, and my computershop has lost it's single Linuxsavvi mechanic. I will  try if Ubuntu picks up the drivers if i add them to the computer on a usb stick, but would like input for a worse case scenario.

---

### Post by 3rdalbum on 2012-02-02
The card will work with 2D out-of-the-box, so you can get a basic desktop up. Then you can install the correct driver using the Hardware Drivers program in Ubuntu. Simple.

If instead you get a blank screen when booting with the new card, hit Control-Alt-F2. Log into the text terminal and run the commands:

```
sudo rm /etc/X11/xorg.conf
sudo reboot
```

which will force the computer to re-detect the new graphics card on next boot and use the default 2D driver.

---

### Post by Newbehans on 2012-02-02
Thanks for the reply. Ijust got back from the computer. I havean old fassioned black screen and a blinking cursor. The computer sees the usb stick and works in text only mode. But although I have worked with ubuntu for years. (it never failed me) I am at a loss in my black screen with text. How do I start the installing. Sorry foe being such a clutch (that is a five letter word so it will pass the decency filter).

---

### Post by Newbehans on 2012-02-02
I am not ready for advanced maintenance. I have found the drivers on the Ubuntu resource site. But I was unaible to activate it on the ubuntu version actieve on the hard disk. I could only get it working on the live-cd-session. Fed up with the lotI saved all valuable files and are now reïnstalling Ubuntu. No it is not sophisticated, but I clean up the computer in the same sweep.
Thanks for your input

---

### Post by grahammechanical on 2012-02-02
You never said what version of Ubuntu you were using. If your version of ubuntu is as old as the broken video card then the driver that was installed and activated would not be able to work the new video card.

The latest drivers will work (may be) on old video cards but an old driver cannot work a newer card.

Regards.

---

