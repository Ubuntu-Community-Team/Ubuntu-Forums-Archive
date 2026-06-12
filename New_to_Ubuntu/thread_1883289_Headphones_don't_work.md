---
title: "Headphones don't work"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by robotz421 on 2011-11-18
I am having problems getting my headphones to work after a new install of Ubuntu 11.10 on my desktop machine.  I tried speaker-test and got sound from the headphones.  I notice in alsamixer that above 'Headphon' is only the little box with 00 in it and there is no tall grey box with the volume setting in it, just blank space and Page-Up/Page-Down do nothing.  When I try to get sounds on Youtube or on Banshee Media Player the line behind the volume slider is red if this means anything.  I have been through the Comprehensive Sound Problem Solutions Guide without any luck and have gone around trying to find and unmute any muted controls.  Any help would be greatly appreciated.

---

### Post by SteveDee on 2011-11-19
> **robotz421 said:**
> ...I notice in alsamixer that above 'Headphon' is only the little box with 00 in it and there is no tall grey box....

In alsamixer, if you hit F6 are there more than one sound cards listed? If so, try selecting another device.

Also type in a terminal:-
```

man amixer

```
...and see if you can check/set the headphones using the appropriate commands.

---

### Post by robotz421 on 2011-11-19
Success!  When I hit f6 in alsamixer there were two choices, (default) and HDA Intel.  I selected the second and my headphones started working.  Thank you very much!

---

