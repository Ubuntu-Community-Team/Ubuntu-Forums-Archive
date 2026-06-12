---
title: "Lazarus Ubuntu sound"
date: 2008-01-14
forum: Programming Talk
---

### Post by vigor2008 on 2008-01-14
I just installed Lazarus on Ubuntu 710 and found that Lazaros doesn't have any multimedia control. Please can anybody explain me how to make program which will play sound (MP3, ogg, wav...) or to send me some example

---

### Post by vigor2008 on 2008-01-14
I found ACS component and install v2.4. 
Put ACSfileIn in form and choose one ogg song, then ACSAudioOut1 connected with ACSfileIn, and try to play. 

Something like 
AcsAudioOut1.run
I think it is working, because if I try to close form it is impossible before song finish.
But i can't hear any sound??? Anybody has idea what to do?

---

### Post by vigor2008 on 2008-01-15
Nobody has idea?

---

### Post by VictorR on 2008-02-19
I would suggest to try command-line interface players as external processes, say aplay (ALSA player for .wav, .au files) or splay for MP3s.

---

### Post by Xealot on 2008-02-20
[fmod]("http://www.fmod.org/") works, and supports a lot of formats

---

