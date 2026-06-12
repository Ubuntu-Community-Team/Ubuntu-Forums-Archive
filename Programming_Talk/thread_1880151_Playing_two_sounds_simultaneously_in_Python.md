---
title: "Playing two sounds simultaneously in Python"
date: 2011-11-13
forum: Programming Talk
---

### Post by Datweakfreak on 2011-11-13
I'm working on mapping musical notes of different frequencies to algorithms in python. I want to play a long tone of low frequency and several short tones over it, say, akin to piano over strings. My code for generating a single sinewave is here:

```
from struct import pack
from math import sin, pi
import time

def play(name, freq, freq1, dur, vol):
    dump = open(name, 'wb')
    dump.write('.snd' + pack('>5L', 24, 8*dur, 2, 8000, 1))
    factor = 2 * pi * freq/8000
    for i in range(8 * dur):
        wave = sin(i * factor)
        dump.write(pack('b', vol * 64 * wave))
    dump.close()

```
How do I go about playing different sinewaves over each other, with delays in them?

I could add two sinewaves together(like harmonizing), but that doesn't serve the purpose, I want to play a bassline kinda thing and other sine waves over it. I dont want to harmonize the bass wave and the higher tones, I want them to be separate tones.

---

