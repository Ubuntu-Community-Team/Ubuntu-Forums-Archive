---
title: "Sound problems"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by Panekoek on 2012-04-02
Hi guys

I just installed Ubuntu 11.10 on my HP Pavillion DV6 laptop and I am still very new to it.

The problem is that it is still playing sound through the computer pictures even when the headphones are plugged in. It plays through both the speakers and headphones.

How can I fix this?

Thank you!

---

### Post by Gleichsnerd on 2012-04-02
After some scrying, I found this command:


```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

Hopefully this does the trick.
Have you tried the controls in the alsa-mixer  yet?

---

### Post by Kevin McCready on 2012-04-02
the command in the terminal is
alsamixer

then use the cursor keys

---

