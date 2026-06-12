---
title: "[SOLVED] sound thru headphone jack, no sound through speaker"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by cautious learner on 2008-08-10
hello
very new to ubuntu. having problems with sound. have read thru multiple threads re how to fix including Comprehensive Sound Problem Solutions Guide v0.5e. still no success. info so far:

a@ubuntu-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

alsamixer
all volume controls are unmuted

can't figure out which is the external mixer

i'm certain that i'm missing something really basic. thanks for your patience

---

### Post by cautious learner on 2008-08-12
update:
with an awful lot of tinkering, i think that i may have a test tone coming out of my desktop speaker (figured out the mixer thing). its difficult to tell. i basically have to be about one inch from the speaker to hear anything. i have covered the obvious level adjustments. is there anything more obscure that i'm missing?
thx

---

### Post by txcrackers on 2008-08-12
Typically, there's a "Master" (Master Mono, Front, etc.) and associcated other inputs/outputs. The one you're mostly concerned with will be the PCM device. What I usually do is pump that one up to 100% and then use the Master device to adjust the volume as needed. I also have my speaker volume at 50%.

You'll probably have to mess with PCM, Master, and hardware volumes to get it to where you want it.

---

### Post by cautious learner on 2008-08-12
many thanks txcrackers...continuing to tinker with it....

---

### Post by Redptc on 2008-08-12
I am not sure what your difficulty is. Do you have your earphones plugged in? If so you will not, normally, get or want sound through your speakers. If you unplug the earphones your main speakers should work.

A bit more explanation of the problem would make it easier for us to help!

---

### Post by cautious learner on 2008-08-13
thank you redptc. the headphones are, and have always been, unplugged. as stated in update, additional tinkering has produced sound thru speaker...but it remains at a remarkably low volume despite 'maxing' all adjustments. this is a dual boot system. when running XP the speaker has a full range of volume. sounds like a little mouse when running ubuntu. is this typical? any way of 'giving it a boost'?

---

### Post by cautious learner on 2008-08-13
solved see:[ubuntu] Ubuntu Hardy 8.04 max sound volume too low

---

