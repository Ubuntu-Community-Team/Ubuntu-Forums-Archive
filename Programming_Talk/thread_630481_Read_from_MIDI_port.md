---
title: "Read from MIDI port"
date: 2007-12-03
forum: Programming Talk
---

### Post by Royall on 2007-12-03
I have an Audigy 2 ZS which has a front panel with an infrared receiver on it. I'm pretty sure that the IR port manifests itself in software as a MIDI input. The software that comes with the card is terrible and makes the potentially powerful remote worthless. I want to write myself an app to receive signals from this MIDI port and respond with keypresses, and maybe other things later on.

To make the long story short, does anyone have any suggestions for languages and libraries that are easy to use to access MIDI input? 
I've messed with Java's built-in stuff a bit, and found it too cumbersome.

---

### Post by j_g on 2007-12-03
If you want to try C/C++ programming, using the native MIDI API of Linux (ie, ALSA), then read my article "Linux MIDI and digital audio programming" at:

[http://home.roadrunner.com/~jgglatt/tech/linuxapi.htm](http://home.roadrunner.com/~jgglatt/tech/linuxapi.htm)

In particular, you'll want to read the article "Record MIDI using ALSA rawmidi" since it appears that all you need is to respond to incoming MIDI messages in real-time. Also, download the gzip archive of C source examples. There is an example that displays incoming MIDI messages.

---

### Post by Royall on 2007-12-03
I'm fairly comfortable with C++, so this looks great. I hope I can get this to work; I think this will be a great tool for any disappointed owner of an Audigy 2 ZS.

---

