---
title: "Live Radio Streams Won't Work"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Sugi on 2008-08-28
I can't listen to live radio streams from professional websites.  I did install the restricted formats from ubuntu
sudo apt-get install ubuntu-restricted-extras
I thought the "restricted extras" included libs for radio streams?

What do I need to install to get radio streams for Hardy Heron?

Thanks,
Sugi

Update:
After messaging #ubuntu, someone pointed me to gstreamer.
Install the following:
```
sudo apt-get install gstreamer0.10-tools gstreamer0.10-x gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-alsa gstreamer0.10-schroedinger gstreamer0.10-pulseaudio
```

It should work. I have some every high CPU usages. So, I am unsure if it worked yet. I will report later with the final word.

Sugi

---

### Post by t0p on 2008-08-28
I think you may need to add the **Medibuntu** repository and install the **W32/64 codecs** as detailed [here]("https://help.ubuntu.com/community/Medibuntu#Adding").

---

