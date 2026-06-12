---
title: "Sound problem"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by babacan on 2008-07-20
Hello
Yesterday I have installed a fresh Ubuntu on my desktop computer, the sound was fine and I was able to listen listen mp3s well via Audacious but today the sound comes VERY low and scratchy. How can I fix this ?

I installed some Gstreamer codes via add/remove program, can this be the reason ?

---

### Post by billgoldberg on 2008-07-20
> **babacan said:**
> Hello
Yesterday I have installed a fresh Ubuntu on my desktop computer, the sound was fine and I was able to listen listen mp3s well via Audacious but today the sound comes VERY low and scratchy. How can I fix this ?

I installed some Gstreamer codes via add/remove program, can this be the reason ?

Could be.

Try switching to ALSA.

In system -> preferences ->sound, select ALSA.

Then use "alsamixer" in a terminal or install gnome-alsamixer to control the sound.

---

