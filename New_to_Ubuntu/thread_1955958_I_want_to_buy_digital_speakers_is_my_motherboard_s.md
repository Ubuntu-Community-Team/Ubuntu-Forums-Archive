---
title: "I want to buy digital speakers is my motherboard sound digital or analog?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by hopelessone on 2012-04-10
Hi,

Speakers are Boston BA735 Digital only speakers, Motherboard is P5G41C-M LX.

```
blade@oneiric:~$ aplay -l | grep card
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
```

Does that mean my sound is digital and will work?

Many Thanks

---

### Post by wyliecoyoteuk on 2012-04-10
mobo specs say:
1 x S/PDIF Out connector 
It does not say if that is Optical or Coax.
EDIT: it seems to be an internal header only.
the bostons seem to need Coax
also the speakers in question seem to need a special cable:
[http://www.turtlebeach.com/support/index.php?View=entry&EntryID=532519590](http://www.turtlebeach.com/support/index.php?View=entry&EntryID=532519590)

---

### Post by grahammechanical on 2012-04-10
What does Sound Settings say?

I am on 11.10 and when I click sound Settings>Hardware tab I get

High Definition Audio Controller 1 output Digital Stereo (HDMI) Output

and

Internal Audio 1 Output/1 Input Analogue Stereo Duplex

I also get to select a profile which ranges from Digital Stereo to Digital Surround 5.1

So, what are you seeing in Sound Settings?

Regards.

---

