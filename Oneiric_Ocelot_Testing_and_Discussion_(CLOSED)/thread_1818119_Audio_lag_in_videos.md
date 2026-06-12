---
title: "Audio lag in videos?"
date: 2011-08-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-08-04
On two systems I have (according to VLC) an audio lag of 400ms across all videos (and with all video players). Anyone else experiencing the same?

---

### Post by lynrock on 2011-08-04
> **MacUntu said:**
> On two systems I have (according to VLC) an audio lag of 400ms across all videos (and with all video players). Anyone else experiencing the same?
Yes, exactly this. Only noticed it in VLC. Running 11.04 Unity.

---

### Post by ELD on 2011-08-04
It's odd i get this with VLC on natty 11.04 Unity, seems to only be VLC, totem works fine.
 
Haven't tested on my normal monitor, this is from the HDMI output to my TV.

---

### Post by flacker on 2011-08-04
Had this problem with VLC on Natty. Switching the audio output module to ALSA brought the sync back to normal for me.

---

### Post by MacUntu on 2011-08-04
Hm, weird. Cannot currently test this with Totem as it's crashing upon opening any video file.

---

### Post by aka120 on 2011-08-04
> **flacker said:**
> Had this problem with VLC on Natty. Switching the audio output module to ALSA brought the sync back to normal for me.

Hey that fixed it right up! Thanks flacker :)

I completely stopped using VLC for this specific reason alone.
Thanks again!

---

### Post by MacUntu on 2011-08-04
Well, you can adjust that within VLC via "Tools &#8594; Track Synchronization".

Here's a VLC bug report: [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/805807](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/805807)

---

### Post by t1497f35 on 2011-08-04
> **aka120 said:**
> Hey that fixed it right up! Thanks flacker :)

I completely stopped using VLC for this specific reason alone.
Thanks again!
same here with Natty, great advice!

---

