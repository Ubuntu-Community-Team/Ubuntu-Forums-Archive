---
title: "[SOLVED] Adjusting playback speed: Which app?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Berean on 2008-07-07
Hi,

I'm wanting to adjust the playback speed of a variety of lectures but don't know which sound and video applications allow me to do so.  Can anyone recommend one, and - if the speed adjustment isn't simple - tell me how to do it, please?  Many thanks.

---

### Post by tab1293 on 2008-07-07
I'm pretty sure MPlayer can adjust playback speed.

---

### Post by annda on 2008-07-07
i haven't found the option in Gnome GUI, but you can use the command line mplayer from the terminal:

```
mplayer -speed 1.1 <path_to_file>
```

of course, 1.1 is just an example to speed the playback by 10%. and it distorts the pitch, too. there is KDE-based GUI for MPlayer called SMPlayer that you can install (go to play>speed).

it seems that the very latest versions of MPlayer (not available in the repositories yet) do support adjusting speed with preserved pitch.

---

