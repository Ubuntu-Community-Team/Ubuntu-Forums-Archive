---
title: "VLC Player Audio Issues on Acer C7 Chromebook/XFCE Crouton Dualboot"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by Satchel88 on 2013-09-26
So I have some MKV files that wouldn't play in Chrome, so I went into my XFCE desktop to play them on VLC and the audio doesn't work.  The video runs perfectly, but with no sound.  At best it will skip in and out.  I tried updating ALSA per someone's suggestion elsewhere but with no luck.  Any advice?

---

### Post by andreazzz on 2013-09-27
Check ALSA´s settings in terminal by just typing "alsa" (without quotation marks), or "sudo alsa". Check if outputs are muted or at a low level.

---

