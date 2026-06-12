---
title: "[SOLVED] Headphone"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by appoloin on 2008-07-09
Hi guys,

i just recently installed ubuntu on my laptop and all works fine. except for 1 thing.

When i plug in my headphone to my laptop the sound still plays on the laptop speaker. i tried going properties and select headphone but still playing on both headphone and laptop speaker. is there any way i can just cancel speaker on laptop sound or is there a program to be able to choose?

---

### Post by ibutho on 2008-07-09
I've noticed this behaviour whilst running other linux distros. I have'nt really found a solution other than manually muting the speaker using the volume control application.

---

### Post by billgoldberg on 2008-07-09
Muting the sound should do.

How I do it is by using alsa, and using alsamixer to only allow the headphones.

I presume alsamixer won't work with pulseaudio :p

---

### Post by Dr Small on 2008-07-09
My external speakers have a power button on them, so when I use the headphones, I turn the power out on the speakers. But as others have said, you can use alsamixer to mute the speakers and only have the headphones unmuted.

Dr Small

---

### Post by appoloin on 2008-07-09
cool thanx all for the advise

---

