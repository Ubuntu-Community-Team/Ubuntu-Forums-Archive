---
title: "Need help on programming with OPAL and full duplex sound problem"
date: 2007-06-29
forum: Programming Talk
---

### Post by qbl on 2007-06-29
Hi all! Right now I'm working on a project using OPAL library. I've tried the sample program called 'simpleOpal' and it run. But I've got a problem that I can hear any sound with the program (the readme says that I should be able to hear sounds). My Ubuntu works well for other programs, I can hear music with Amarok, I can hear system sounds, etc... .

I've tried a lot to find what's the problem with this sample program, at last I end up finding in one abandoned forum saying,

"you should check whether your soundcard is full duplex"

actually, I'm bit confused whether to post this in "programming talk" or in "multimedia" but then I choose to post here. So my question is, 

1. how to know wheteher my sound card is full duplex or not?
2. if it is indeed a full duplex soundcard, how to enable its capability to support full duplex?

for information, here is the result of aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Best regards.

---

