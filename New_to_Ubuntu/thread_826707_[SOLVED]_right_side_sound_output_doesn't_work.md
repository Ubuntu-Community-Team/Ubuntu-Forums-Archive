---
title: "[SOLVED] right side sound output doesn't work"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by vamsibethapudy on 2008-06-12
something is wrong with my compuer.
i cant listen to the right speakers. i checked if the problem is with the speakers by inserting my headphones in , but the same thing repeats , right side does not give sound.i finally checked by logging into windows xp .
everything works fine there.
Yes i have checked the volume control.

---

### Post by vamsibethapudy on 2008-06-12
and another interesting thing - i use matlab in linux, if there is an error matlab gives an error sound.the thing is , this error sound can be heard form both sides of the speakers, strange!!

---

### Post by powerpleb on 2008-06-12
> **vamsibethapudy said:**
> and another interesting thing - i use matlab in linux, if there is an error matlab gives an error sound.the thing is , this error sound can be heard form both sides of the speakers, strange!!

in console open```
alsamixer
```
and make sure the right and left channels are set to the same volume

---

### Post by vamsibethapudy on 2008-06-12
hey, thanks.
i have checked alsamixer before.
but now i have seen a strange thing, under the PCM control one has M ( the right one ) , the other one 0.
i tried pressing key 'm'.but that just made the mute, to shift to left speaker.
then i just muted volume from the gnome-panel & than pressd key 'm' in alsamixer & that did the trick!!
hope others with this problem find it useful.

---

