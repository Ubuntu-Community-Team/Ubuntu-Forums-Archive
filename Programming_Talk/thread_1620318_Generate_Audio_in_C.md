---
title: "Generate Audio in C"
date: 2010-11-12
forum: Programming Talk
---

### Post by Mr.Macdonald on 2010-11-12
I want to write a raw bit stream and output it to the audio device.

So I want to run my program and have it generate audio which is streamed to my speakers. Not my PC beeper speaker (controlled by pcspkr), but the audio jack.

How do I do this magic?
Thank you

---

### Post by worksofcraft on 2010-11-12
> **Mr.Macdonald said:**
> I want to write a raw bit stream and output it to the audio device.

So I want to run my program and have it generate audio which is streamed to my speakers. Not my PC beeper speaker (controlled by pcspkr), but the audio jack.

How do I do this magic?
Thank you

I would look at using gstreamer... I've only used it from Python, so you may have to google for the C API :)

---

### Post by Mr.Macdonald on 2010-11-12
I found [this WFS]("http://www.oreilly.de/catalog/multilinux/excerpt/ch14-05.htm")

When I try to write to dsp, it prints
open of /dev/dsp failed: Device or resource busy

Apparently this is only for the deprecated OSS. Is there an ALSA equivalent?

---

### Post by abhilashm86 on 2010-11-13
You can try [OpenAL]("http://climpxwss01.creativelabs.com/openal/default.aspx") , I however used in C++ to output some .wav sound in simulation.  
The buffer and parameters API are different on windows and Linux platforms, make sure you go through documentation once.

---

### Post by Zugzwang on 2010-11-13
There exists a tuturial on ALSA sound playback: [http://www.linuxjournal.com/article/6735?page=0,1](http://www.linuxjournal.com/article/6735?page=0,1). It is a little bit old but it might still work. If it doesn't, search google for newer tutorials. 

In Linux, there are multiple sound systems. You will need to choose one to find a suitable tutorial. ALSA is probably not a bad choice.

---

### Post by Arndt on 2010-11-13
> **Mr.Macdonald said:**
> I want to write a raw bit stream and output it to the audio device.

So I want to run my program and have it generate audio which is streamed to my speakers. Not my PC beeper speaker (controlled by pcspkr), but the audio jack.

How do I do this magic?
Thank you

Maybe [http://www.portaudio.com/](http://www.portaudio.com/) is useful. I'm new to sound generation, so I don't know if it fits the bill.

---

