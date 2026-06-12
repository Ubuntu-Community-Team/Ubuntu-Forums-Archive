---
title: "adding sound in program??"
date: 2009-06-15
forum: Programming Talk
---

### Post by abhilashm86 on 2009-06-15
actually i've done a program that has transformations like rotation and translation in opengl, its a small aircraft, so i want to add sound, where to start and which are formats of audio it can recognise??
also can we achieve sound in c++, just for curiosity?? how to do it??

---

### Post by Krupski on 2009-06-15
> **abhilashm86 said:**
> actually i've done a program that has transformations like rotation and translation in opengl, its a small aircraft, so i want to add sound, where to start and which are formats of audio it can recognise??
also can we achieve sound in c++, just for curiosity?? how to do it??

You could write to the /dev/dsp device (the sound card).

This page ([[COLOR="RoyalBlue"]_**LINK**_[/COLOR]]("http://www.oreilly.de/catalog/multilinux/excerpt/ch14-05.htm")) should give you enough information to get started and use the /dev/dsp device.

-- Roger

---

### Post by nvteighen on 2009-06-15
I guess you can use libogg, libsndfile or some other library to load a pre-recorded file rather than feeding data directly to the sound card... :p

---

### Post by Krupski on 2009-06-16
> **nvteighen said:**
> I guess you can use libogg, libsndfile or some other library to load a pre-recorded file rather than feeding data directly to the sound card... :p

The reason I mentioned /dev/dsp was that I made a DTMF generator program (to dial telephone tones) in C. And, it generates the tones on the fly into a buffer. Frankly, I wouldn't know how to do it any other way BUT to use /dev/dsp..

---

