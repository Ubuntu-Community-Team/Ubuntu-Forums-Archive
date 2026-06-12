---
title: "Another sound problem"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by xenocide13 on 2008-06-01
Allright so here is the deal
I get no sound what so ever
i go to the alsamixer and the headphone volume is turned down all the way
but it wont let me turn it up 
headphones is all i have, i cant use speakers
anyone know how to make it work?

---

### Post by kansasnoob on 2008-06-01
I don't know that this will work any differently than using alsa-mixer but it's easy and can't harm anything. Try opening synaptic and installing gnome-alsamixer.

Gnome Alsa Mixer will now show up in Sound & Video. Try the toggles in that gui and see if that helps.

If not let us know if sound has ever worked with your current install, or with a previous OS.

---

### Post by xenocide13 on 2008-06-01
Allright i got that and installed it and nothing changed

sound works fine when i boot into windows just wont work in ubuntu

---

### Post by mac143_01 on 2008-06-01
If you install Ubuntu It automatically detects the hardware in you PC so you will have sound ou it no need to install sound card drivers

---

### Post by xenocide13 on 2008-06-01
It did auto detect but the sound still does not work thats my problem

---

### Post by CameO73 on 2008-06-01
What's the output of this command:
```
asoundconf list
```

---

### Post by kansasnoob on 2008-06-01
I have found a few sound cards that don't work without adding "alsa-firmware" which requires the Medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

NOTE: remember to add the GPG key!

Also (and perhaps prior to trying that) it may be a "library" problem. Libraries are generally recognized by "lib" as in "libao2" or "libasound2".

If you're running Hardy (I hope) this is my default list of Hardy alsa apps:

alsa-base
alsa-utils
gstreamer0.10-alsa
libao2
libasound2
libesd-alsa0
libpt-1.10.10-plugins-alsa
libsdl1.2debian-alsa
linux-sound-base
pulseaudio
vlc-plugin-alsa

Of course if you're using (just for instance) xmms2 you'd need "xmms2-plugin-alsa".

Also gstreamer plugins can affect sound in some apps.

---

### Post by markbuntu on 2008-06-01
Try turing up all the volumes in the mixer. Also, go to System/Preferences/Sound and change all the settings from automatic to alsa.
Let us know if that works.

---

