---
title: "Self compiled alsa"
date: 2008-03-22
forum: Packaging and Compiling Programs
---

### Post by LCID Fire on 2008-03-22
Hi.
I patched the alsa usb audio driver in the git repo and compiled the modules. I then put my compiled modules in /lib/modules/...
Now I have 2 thinks I need help with:

1. Why are there 2 different locations for the alsa drivers?
the one is **./kernel/sound** and the other **./ubuntu/sound/alsa-driver**
It's quite confusing and did cost me some time to find out that the ubuntu directory is used :(

2. When I try to load my self compiled alsa modules it complains about:
[B]snd_usb_audio: disagrees about version of symbol snd_pcm_new
snd_usb_audio: Unknown symbol snd_pcm_new[/B]

So appearently there is some meta information mismatch - how can I fix the version?

---

