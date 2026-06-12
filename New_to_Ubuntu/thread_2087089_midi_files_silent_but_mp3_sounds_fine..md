---
title: "midi files silent but mp3 sounds fine."
date: 2012-11-22
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-11-22
Hi there,

hey I have noticed that my system isn't playing midi files. Sound works ok. Movie player is default for midi files, it plays mp3 fine but midi silent.
Checked sound settings in system settings and speakers working ok.

Play mp3 through banshee and works ok. 

Any help?

---

### Post by andrew.46 on 2012-11-22
Probably the easiest way to get midi playback (and there are a few different approaches) is to download audacious and a sound font:

```
sudo apt-get install audacious fluid-soundfont-gm
```

and then open the audacious Preferences and look at Plugins --> Input --> Amidi-Plug (Midi Player). Look at the Preferences for this plugin and select the FluidSynth backend, then fill in the SoundFont settings with the path to the soundfont you have just downloaded. This should be in /usr/share/sounds/sf2/FluidR3_GM.sf2.

Now press apply, save etc and play your midi file directly with audacious :)

---

