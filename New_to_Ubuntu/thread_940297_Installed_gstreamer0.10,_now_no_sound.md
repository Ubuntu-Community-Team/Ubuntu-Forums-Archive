---
title: "Installed gstreamer0.10, now no sound"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by dunomous on 2008-10-06
As the title says, I installed gstreamer0.10 from the package manager (using Feisty) hit the mute button on my keyboard. When unmuted, I no longer had sound. Reinstalled the alsa drivers, no luck. gconf-editor tells me that it's using gstreamer for all playback options, but I don't even know what to change. All my settings are unmuted. My sound card (Intel ICH6 chipset) is detected just fine, and selected in the sound settings for device to playback (with ALSA). When trying to test the audio, I get the 

```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat
```

error. I've rebooted and such as well (following the Audio Comprehensive Guide). *sigh* just so frustrating.... Thanks for your help, and I will of course give more information if needed.

---

