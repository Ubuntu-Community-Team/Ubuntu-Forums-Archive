---
title: "Sound input/recording issue"
date: 2021-04-28
forum: New to Ubuntu
---

### Post by chromepanda on 2021-04-28
Hi,

Recently switched over to Ubuntu from Windows. Figured most things out except this recurring sound quality issue. 

The sound output is fine, through speakers and headset, but when I try to use zoom/discord etc. my voice is either way too quiet, or if I turn the input volume up, it becomes unclear and muddy. I've tested the quality using a basic voice recorder and the issue is still the same regardless of what program I'm using. 

Any ideas of where to start troubleshooting? Sound quality is fine on windows so it's not faulty hardware.

---

### Post by ajgreeny on 2021-04-28
Laptop or desktop?
What microphone do you use?

Have a look in the **pulseaudio-volume-control** which you get to either with command ***pavucontrol*** or from the volume control in your panel -> **Audio Settings** (that wording may vary with the DE you use, eg, in Xubuntu it is **Audio-Mixer**

---

### Post by grahammechanical on 2021-04-28
I do not know if this happens to you but it happens to me. Every time I open zoom-client and join a meeting the zoom voice engine for my microphone has a default setting of 50%. I have to open System Settings>Sound and move the slider more completely to the right. This is regardless of the main Ubuntu microphone input device setting which is also set by default to 50%.

Regards

---

### Post by ajgreeny on 2021-04-28
By default Zoom settings have the system setting microphone gain automatically.

Maybe you need to change that to manual gain setting.

You may also need to make sure that microphone boost is disabled in alsamixer.

---

