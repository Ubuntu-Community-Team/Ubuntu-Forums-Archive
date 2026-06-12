---
title: "Sound stopped working"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by tezcat51 on 2013-05-08
Loaded Ubuntu 12.04 LTS last night, everything worked fine until this afternoon.  All normal sound suddenly stopped, all I get is a scratchng noise at random.  I have tried every troubleshooting guide I could find, nothing at all has changed.  I'm a rank beginner, so I'm not at all sure what I'm doing.

---

### Post by tezcat51 on 2013-05-08
Okay, after trying all the troubleshooting, I just noticed the sound controller next to the clock is showing the speaker icon and then "--".

---

### Post by tezcat51 on 2013-05-08
According to my sound settings, the play sound through box is empty, and I have no idea how to fix this.  The application tab lists no application currently playing audio, no matter what I have running.  Is there something I can do to fix this, please?

---

### Post by Frogs Hair on 2013-05-08
If you had installed and were using the pulse audio equalizer I have a possible solution if not I have no suggestions other than what you have tried. I had a sound icon that looked like the symbol but it was my equalizer profile at fault.  .....(

---

### Post by UltimateCat on 2013-05-08
By default I'm pretty sure that Ubuntu and Debian distributions use alsa-

One way to know is to open the terminal and run:
```
alsamixer

```
If your Ubuntu distro is using 'alsa' by default you can adjust each one of the columns in the alsa mixer.
If your not greeted with a black/grey background with several colums than your distro is not using alsa--

Ensure that you have all of the columns raised all the way up and the PCM and the Master turned all the way up as well.

You should be able to perform a sound test too-
{00} means un-muted and {mm} means muted at the bottom of the columns.

I have heard of pulse audio but Frogs Hairs should be trusted with the details of that as I do not know that much about
'pulse audio'

Hope this helps:D

---

