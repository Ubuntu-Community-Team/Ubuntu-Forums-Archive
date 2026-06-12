---
title: "Problems Recording"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by thehereaway on 2008-07-26
Hey all, i bought a really cheap mic today and im having trouble recording on audacity with it.

If i tap on the microphone, i can hear it through my speakers but if i blow into the mic or talk into it then nothing is picked up *(i've tried turning the volume up on my speakers and i can hear the blowing noises, but my speakers have to be turned up ridiculously loud)* 

Also, when i select record on Audacity i get an error message saying *'Error while opening sound device. Please check the input device settings and the project sample rate'*. If i try sound recorder i get an error message saying *'Your audio capture settings are invalid. Please correct them in the multimedia settings'*

So i've no idea what im supposed to do here...

---

### Post by freak42 on 2008-07-26
try different settings in system->preferences->sound

especially the sound capture part.

you can also change the (input volume) of your microphone, do this with a right click on the gnome volume icon (in the top toolbar normally) and select open volume control (sorry I don't know another way how to access it, even though there must be one).

hth

---

### Post by tonychar on 2008-08-10
Also in the << Sound Preferences \ Devices >> menu, in the << Audio Conferencing >> box, ensure << ALSA >> is selected as the sound capture.  You can then alter the record level etc using Sound Recorder.  Make sure the record level is less than halfway up.

---

### Post by Crafty Kisses on 2008-08-10
Yeah make sure you make ALSA as the device, also post the following output:
```
lspci
```

---

