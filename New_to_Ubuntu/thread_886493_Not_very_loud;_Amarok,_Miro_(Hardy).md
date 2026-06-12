---
title: "Not very loud; Amarok, Miro (Hardy)"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by metasolaris on 2008-08-11
Hi,

The max sound level on Hardy using headphones - at least with Miro and Amarok - is not very much even when set on 100%. Is there anything I can do about it?
Thanks

meTa

---

### Post by LowSky on 2008-08-11
go to the sound icon, look for PCM and increase the volume of that one. Careful It might become distorted if it at 100%

---

### Post by metasolaris on 2008-08-12
> **LowSky said:**
> go to the sound icon, look for PCM and increase the volume of that one. Careful It might become distorted if it at 100%

It was already at 100%!

---

### Post by billgoldberg on 2008-08-12
Open up a terminal (applications -> accessories -> terminal) and copy/paste this:

```
sudo apt-get install gnome-alsamixer
```

After it's installed, go to "applications -> sound and video -> gnome-alsamixer".

Look around there and max everthing out.

--

I don't really know if this also works if you are using PulseAudio.

Maybe another user could clarify this for me.

---

### Post by aimpau on 2008-08-12
try also to install oss-compat.

---

