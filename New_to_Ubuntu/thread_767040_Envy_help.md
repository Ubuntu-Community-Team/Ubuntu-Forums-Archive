---
title: "Envy help"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by natman on 2008-04-25
Hi i have just installed Kubuntu, and insatlled the nvidia driver using the driver manager. Things are fine, but when i go to systems settings and ask for effects nothing happens, but if i switch from Open GL to Xrender then things work, but still a little sluggish.
I used to run gusty with compiz no bother, i have 128 shard video ram

---

### Post by dark_harmonics on 2008-05-18
Did you install the default NV driver from restricted manager or the nvidia proprietary driver? Are you talking about sluggish compiz fusion effects? What is the output of glxinfo|grep direct? Does your video card support the scaling features (it turns up the memory clock speed when needed and back down when not needed)? I have a slowness problem with compiz that is caused by this scaling. It only happens on my macbook pro which has an nvidia card.

---

