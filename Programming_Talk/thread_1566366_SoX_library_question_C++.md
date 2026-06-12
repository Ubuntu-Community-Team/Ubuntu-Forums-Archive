---
title: "SoX library question C++"
date: 2010-09-02
forum: Programming Talk
---

### Post by hakermania on 2010-09-02
Can anybody explain me how do I play mp3,ogg and wav files with sox library? I've installed it but I have no idea how to use it and there are notutorials out there.

---

### Post by andrew.46 on 2010-09-10
Hi hakermania,

> **hakermania said:**
> Can anybody explain me how do I play mp3,ogg and wav files with sox library? I've installed it but I have no idea how to use it and there are notutorials out there.

If you mean simply playback audio files, the command is *play*:

```

andrew@skamandros~/music/ftgws$ **[COLOR="Red"]play -V3 revelation_21.mp3 [/COLOR]**
play: SoX v14.3.0

Input File     : 'revelation_21.mp3'
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Duration       : 00:06:05.29 = 17533824 samples ~ 27396.6 CDDA sectors
File Size      : 5.84M
Bit Rate       : 128k
Sample Encoding: MPEG audio (layer I, II or III)
Comments       : 
Title=A New Heaven
Artist=Lesley Garrett
Album=Lesley Garrett - The Singer
Tracknumber=01
Genre=Classical


Output File    : 'default' (alsa)
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Duration       : 00:06:05.29 = 17533824 samples ~ 27396.6 CDDA sectors
Sample Encoding: 16-bit Signed Integer PCM
Endian Type    : little
Reverse Nibbles: no
Reverse Bits   : no

play INFO sox: effects chain: input      48000Hz 2 channels
play INFO sox: effects chain: output     48000Hz 2 channels
In:100%  00:06:05.28 [00:00:00.01] Out:17.5M [      |      ]        Clip:0    
Done.

```

Andrew

---

### Post by dwhitney67 on 2010-09-10
> **hakermania said:**
> Can anybody explain me how do I play mp3,ogg and wav files with sox library? I've installed it but I have no idea how to use it and there are notutorials out there.

Then why are you using SoX?  I also Googled for information, and came up empty.  If the product is not supported, I would think that the best alternative is to look elsewhere.

Perhaps you should consider using SDL (mixer).

---

