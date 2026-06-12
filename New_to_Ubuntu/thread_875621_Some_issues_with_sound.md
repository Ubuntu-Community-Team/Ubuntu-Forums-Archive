---
title: "Some issues with sound"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by gustasonfrever on 2008-07-31
When I'm using ubuntu my sound will frequently work only on select applications. I think that it depends on what program I start listening to first. At the moment i started up firefox and listened to some music and now VLC and Amarok refuse to make any noise. I've tried turning up the individual volume controls but to no avail. Does anyone know how I can stop this from happening?

---

### Post by InfinityCircuit on 2008-07-31
Sounds like a pulseaudio problem: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by gustasonfrever on 2008-07-31
What section do I need to follow?

---

### Post by Ryadt on 2008-07-31
Do ```
killall pulseaudio
```

---

### Post by Nepherte on 2008-07-31
> **gustasonfrever said:**
> What section do I need to follow?
From the how to:
Which part(s) should I follow?
Part A is a required step you must follow, as it will enable proper PulseAudio support in most ALSA-aware applications.

Part B (i386 only) will install version 10 (beta) of Adobe's Flash plugin, as it has better compatibility with PulseAudio.

Part C is highly recommended if you notice a lot of stuttering audio in some applications. The settings proposed in this guide work well for my system, but you may need to do some manual tweaking to get the best results for your hardware.

Part D is an optional step that enables a system-wide audio equalizer (which can be customized using any LADSPA audio processing plugin). The settings provided in this guide are ideal for laptop users who notice poor quality audio playback using their built-in laptop speakers.

Appendix A gives information on specific applications including Skype, WINE as well as SDL and OSS applications. Appendix B helps troubleshoot audio playback/mixing issues using the PulseAudio Volume Control application. Appendix C will revert all changes made by this guide (if for some reason you can't get PulseAudio working properly).

---

