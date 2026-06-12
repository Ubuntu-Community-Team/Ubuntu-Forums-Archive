---
title: "Voice programme"
date: 2021-01-22
forum: New to Ubuntu
---

### Post by kamil997 on 2021-01-22
Hi, i have a question. I am new to Ubuntu. When i was using win10 i had program named "voicemeeter" which i was using to play mp3 or mp4 on my mic. Is there on Ubuntu any same program to to that or not?

---

### Post by TheFu on 2021-01-22
Assuming this is a correct description:
> Voicemeeter is Audio Mixer Application endowed with Virtual Audio Device used as Virtual I/O to mix and manage any audio sources from or to any audio devices or applications. 
Then PulseAudio is how Ubuntu does that.  **pavucontrol** is the program.

If you would like to mux inputs from 20 people over the network and create 1 output - like a band or church might need during COVID, there are other tools for that - like JackTrip.

But there are many, many, many, audio programs of all sorts for Unix systems. Some are more ready for end-users than others. Ubuntu Studio has some tools built in.

---

