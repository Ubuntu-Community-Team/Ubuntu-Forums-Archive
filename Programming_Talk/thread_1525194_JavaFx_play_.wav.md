---
title: "JavaFx play .wav"
date: 2010-07-06
forum: Programming Talk
---

### Post by Thomas Wuensche on 2010-07-06
Good afternoon,
I am really new to this forum and I hope it is the right one.
I have coded a music box, running well on Windows 7.
The coding language is Java (jdk1.6.0_18) using additionally JavaFX 1.2 and 1.3.
I tried to run the application on Ubuntu having in mind JavaFX was realeased for Ubuntu 8.04 as beta version.
I always get an gStreamer unsupported media error when
accessing a .wav file, even if I have copied the libGstreamer.so to my /lib folder. 
Furthermore I installed all gstreamer plugins available.
Hoping someone can help me
Thomas

---

### Post by kahumba on 2010-07-06
One of the areas where Java has failed is qualitative and consistent media support across Windows/Linux/Mac. Oracle hasn't changed that situation. So you're supposed to have random glitches/bugs across platforms.
PS: there are different versions of .wav files, not all of them are supported by Java on all platforms and at same time, since .wav is a product of Microsoft - on window$ Java might support all .wav versions hence the glitch on non-window$ platforms.

---

### Post by Thomas Wuensche on 2010-07-08
Thank you for your quick reply. If there is no way at the moment, I will wait until the availibilty of Java 7.
It was announced to fully support Linux with regard to JavaFx.
I have awarely chosen Java as coding language to support different OS and to provide them with Opensource software, if wished.
Otherwise I would change to Lazarus.
Best regards
Thomas

---

