---
title: "Audio Volume"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by riv359 on 2008-07-06
Volume is low even at max setting.

---

### Post by billgoldberg on 2008-07-06
Try going to "system -> preferences -> sound".

Switch everything to "ALSA" or ALSAMIXER, whatever it says.

Then open up a terminal an copy/paste this

```
sudo apt-get install gnome-alsamixer
```

Then go to 

applications -> sound&video -> gnome alsamixer.

Max everything out.

That should do it.

---

