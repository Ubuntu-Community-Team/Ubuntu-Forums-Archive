---
title: "what can I use for do sound in python?"
date: 2009-07-14
forum: Programming Talk
---

### Post by hecato on 2009-07-14
That is the question?

1) for dont block (allow other programs to do sound)
2) the used way

Because I see some programs block others, for example if I have open rhytombox and try other program, thus I see a message that the device is in use and things like that.

Also I have thinked to learn to use for example pygame and go on, but for some simple apps, perhaps the extra pygame dependency is to much?

---

### Post by lavinog on 2009-07-14
> **hecato said:**
> 
Because I see some programs block others, for example if I have open rhytombox and try other program, thus I see a message that the device is in use and things like that.

The blocking of others can be a configuration issue. Generally if the program doesn't use the sound server it will do that.
you can use padsp rhythmbox to force it to play using the pulseaudio daemon. I haven't messed with it much since intrepid, so I don't know if there are any changes.

---

