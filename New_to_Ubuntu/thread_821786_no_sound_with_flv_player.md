---
title: "no sound with flv player"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Fabiolas on 2008-06-07
I installed flv player but when i try to view some .flv video i only get video and no sound !

I have sound in firefox but not work with video players.. Anyone can help ?

thx in advance.:KS

---

### Post by ruha on 2008-06-07
I have the same problem, but i've noticed that the flv sound works if you shut down every media player, and the other way round.

---

### Post by Happy_Man on 2008-06-07
This is an issue with conflicts between the Flash people and the PulseAudio engine (which is what Ubuntu uses). You can fix the problem by installing the package libflashsupport, but be warned: This will make *extremely* unstable. But if you really need it, the fix is there.

---

