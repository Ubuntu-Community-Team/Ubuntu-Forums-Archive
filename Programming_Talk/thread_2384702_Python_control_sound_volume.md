---
title: "Python control sound volume"
date: 2018-02-10
forum: Programming Talk
---

### Post by jtodd.fr on 2018-02-10
I was playing with pyalsaaudio (v0.8.4) using python (v2.7.12 with GCC 5.4.0 20160609) on Ubuntu 16.04.3 LTS. My goal is to read the current sound volume level and then adjust the value by e.g. increment by 10% or 10. When testing the sample code

```

import alsaaudio


mixer = alsaaudio.Mixer()
vol = mixer.getvolume()
print(vol)

```

It prints [27, 27], but checking with alsamixer it shows master sound  is 20  where View is F3:[Playback] and Item is Master [dB gain: -33.50].

How should I interpret such different? I completely don't understand Linux sound system, so I appreciate any suggestions. 

Thanks.

---

### Post by norobro on 2018-02-11
[SIZE=2][FONT=arial]From the alsamixer man page:> VOLUME MAPPING
       In alsamixer, the volume is mapped to a value that is more natural for a human ear.
       The mapping is designed so that the position in the interval is proportional to the
       volume as a human ear would perceive it, i.e. the position is the cubic root of the
       linear  sample  multiplication  factor.

So, if I understand the above, the devs modified the display scale for alsamixer.

On my machine:```
In [1]: import alsaaudio

In [2]: mixer = alsaaudio.Mixer()

In [3]: mixer.getvolume()
Out[3]: [48L]

In [4]: mixer.getrange()
Out[4]: [0, 42]
``````
$ amixer -c 0 sget Master 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 20 [48%] [-33.00dB] [on]
```
And alsamixer shows master sound at 21 with dB gain: -33.00

What concerns do you have?[/FONT][/SIZE]

---

