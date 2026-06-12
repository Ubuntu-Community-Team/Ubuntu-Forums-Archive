---
title: "command line mp3 player"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by user2000 on 2008-11-04
hi,

i am looking for a command line mp3 player with the following features: 
1. volume normalization
2. fade-in & fade-out of the mp3 track (no crossfading)

i tried using mplayer. its great, it has volume normalization also. but i dont know whether it has fade-in and fade-out feature. can someone tell me how to do that or suggest any other program to play mp3 files?

thank you very much

---

### Post by duruttye on 2008-11-04
Hey, have you tried xmms2? I did't use it, but as far as I remember it is a command line player.
Someone correct me if I'm wrong.

---

### Post by mc4100 on 2008-11-04
Don't know if you're any better with this than mplayer, and it's strictly mpeg (layers 1-3), but ...

[http://www.mpg123.de](http://www.mpg123.de)
> Features

We all know that mpg123 is the fast console mpeg audio decoder/player, don't we? But here are some things that go beyond simple decoding:

    * support for many platforms (many Unices, MacOSX, Windows) and audio subsystems
    * simple but powerful control mode for frontends (commands via STDIN)
    * realtime control of efficient equalizer (because built into decoder)
    * built-in terminal control keys
    * **support for gapless playback of mp3 files (skipping encoder/decoder padding/junk)**
    * many audio data settings: resampling, choose channel, mono, ...
    * really efficient with a growing number of assembler optimizations (pentium, MMX, AltiVec, ...)
    * **support for Relative Volume Adjustment / ReplayGain**

Also, especially for the simple decoding, the decoder part of mpg123 is usable as a library in your application! 

---

### Post by user2000 on 2008-11-04
thank you for your prompt replies. but i am looking for something which can fade-in and fade out music. i find mplayer perfect. but i dont know if its possible to fade in and fade out. since i will be playing only one track at a time i dont need a crossfade option.

---

