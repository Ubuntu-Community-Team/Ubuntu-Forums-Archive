---
title: "Audio Library?"
date: 2009-08-29
forum: Programming Talk
---

### Post by jacensolo on 2009-08-29
I want to dabble into audio programming, but I can't find a good library. I don't mean I need to play an mp3 player, but play specific frequencies - like a synth. Can I do this with GStreamer?

---

### Post by abhilashm86 on 2009-08-30
> **jacensolo said:**
> I want to dabble into audio programming, but I can't find a good library. I don't mean I need to play an mp3 player, but play specific frequencies - like a synth. Can I do this with GStreamer?

yes you can use OpenAl libraries to achieve this, it provides you specific position, velocity, other attributes in the scene, i tried this in c++, you [can refer this for more information]("http://connect.creativelabs.com/openal/default.aspx") and[ packages in ubuntu]("https://launchpad.net/ubuntu/+source/openal"),
open a terminal, install OpenAl,
```
 sudo apt-get install libalut0 libalut-dev libghc6-alut-dev libghc6-alut-doc libghc6-alut-prof libhugs-alut-bundled
```
check [programming tips ]("http://abhilash.co.nr/")on my website for adding sound

 all the best:)

---

### Post by soltanis on 2009-08-30
With ALSA, you can also look into writing sound output to the /dev/dsp (digital signal processor) device; or, with the recent trends in Linux sound, use pulseaudio (a sound server).

For basic sound synthesis, either system is pretty straightforward and easy.

---

### Post by jacensolo on 2009-08-31
I'm confused on how sound works in Linux. What does the sound server do and how do all of the libraries know how to talk to every sound server? How do libraries handle it on windows?

---

