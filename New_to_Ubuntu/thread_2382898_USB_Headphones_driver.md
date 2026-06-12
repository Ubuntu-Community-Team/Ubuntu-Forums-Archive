---
title: "USB Headphones driver?"
date: 2018-01-18
forum: New to Ubuntu
---

### Post by Karsza_Levente on 2018-01-18
Hello, I am using the Panasonic Rig 500 HD headphone, which uses USB for its input and output, but
panasonic only supports windows

How could I get it working?

---

### Post by oldrocker99 on 2018-01-18
It is quite likely that drivers already are n the kernel; plug 'em in and see if they work.

---

### Post by sisco311 on 2018-01-18
USB headphones are detected as separate sound cards.

Is the device recognized? Please post the output of:
```
cat /proc/asound/cards
```
and
```
lsusb
```

Can't you simply select the device in the sound settings?  I don't use Xubuntu, but I think its under Xfce4 menu -> Multimedia  -> PulseAudio Volume Control.

---

### Post by Karsza_Levente on 2018-01-18
Okay, got it, I had the Indicator plugin disabled, thanks!

---

