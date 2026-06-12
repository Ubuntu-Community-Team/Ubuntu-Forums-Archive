---
title: "Sound Effect with Linux"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by jon35 on 2014-02-26
Just yesterday, I installed Ubuntu on my Chromebook.

To start Linux from the Chrome OS, I open the Chrome Browser, open the terminal, type 'shell', followed by 'sudo startunity', which is when Linux starts.

My question is this:

Does anyone know how to make my Chromebook play some like hyperdrive, light-speed sound effect when I type in 'sudo startunity' and blast from Chrome OS into Raring Unity?

Thanks.

JB

[http://www.blondyn.com](http://www.blondyn.com)

---

### Post by tgalati4 on 2014-02-27
```
sudo startunity; aplay /home/jon35/star_trek_phasers.wav
```

It might be cleaner to put it at the bottom of the *startunity* script.

---

