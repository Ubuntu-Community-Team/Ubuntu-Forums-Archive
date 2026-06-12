---
title: "NO sound output via headphone jackport"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by D.Sync on 2008-07-22
Whenever I tried to plug in any headphone/earphone to the jack port, the sound still comes from my Acer Aspire 5920G laptop speaker instead of coming from the head/earphone.

There are currently 3 devices shown on the 'change device' option:
-> HDA Intel (Alsa Mixer)
-> Realtek ALC888 (OSS Mixer)
-> Capture ALSA PCM ....

When I choose HDA Intel, there is a tab named 'Switches' and even though I tick the 'headphone' box, the sound still doesn't output to my headphone but it still output to my laptop speaker.

Any way to solve this issue? Thanks.

---

### Post by oliviacond on 2008-07-24
edit the **/etc/modprobe.d/alsa-base**
```

sudo gedit /etc/modprobe.d/alsa-base

```

add this to the last line
```

options snd-hda-intel model=acer-aspire

```

save it and restart, if still can't work,
change the line to
```

options snd-hda-intel model=acer

```

---

