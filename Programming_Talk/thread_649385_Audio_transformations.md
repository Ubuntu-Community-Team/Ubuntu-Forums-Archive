---
title: "Audio transformations"
date: 2007-12-24
forum: Programming Talk
---

### Post by neko18 on 2007-12-24
Is there a fairly easy-to-use library that can perform audio transformations such as changing the pitch, tempo, and volume? Python or Ruby bindings are best, but I can manage some C as well.

Thanks

---

### Post by samjh on 2007-12-25
Unless the sound file is in raw PCM encoding, I think you'll need to decode the audio file to raw PCM, make your alterations, and then re-encode it into the format you want.

Try here: [http://wiki.python.org/moin/Audio/](http://wiki.python.org/moin/Audio/)

---

### Post by MadMan2k on 2007-12-25
[http://gnonlin.sourceforge.net/](http://gnonlin.sourceforge.net/)

---

