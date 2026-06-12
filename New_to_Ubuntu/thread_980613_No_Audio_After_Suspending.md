---
title: "No Audio After Suspending"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by tigerking615 on 2008-11-13
Okay, so I'm pretty much a Ubuntu noob. I installed it a week or two ago, and every time I suspend and resume from that, I don't get sound in my headphones (I keep them plugged in almost all the time). I tried taking the headphones out, but that doesn't work either. 

If I boot up with headphones in, headphones work. They work until I suspend.
After I resume, no audio works. I made sure nothing is muted and the volume is high enough. I have to reboot to get sound again.

I'm using Intrepid Ibex, and I'm on a Fujitsu laptop, and I believe the sound card was made by Intel. If you need me to provide any other information, I can do that, but I'm going to need to know how to find it :(

In System > Preferences > Sound, "Sound Events" and "Music and Movies" are on Autodetect. When I test on a fresh reboot, the test is successful, but after a suspend (like now) I can't hear anything. I tried changing it to ALSA and that didn't work either, so I switched it back. 

Any help fixing this would be greatly appreciated.

---

### Post by roquefilipe on 2008-11-13
I had the same problem, so I did a workaround. I kill all process using sound, unload the sound modules and load them back. This is what my script look like:
```

#!/bin/bash

sudo fuser -k /dev/snd/*

#kill  ''pid's''
sudo modprobe -r snd_hda_intel
sudo modprobe snd_hda_intel
```

Sure this is not a good solution but it keeps me going :)

---

