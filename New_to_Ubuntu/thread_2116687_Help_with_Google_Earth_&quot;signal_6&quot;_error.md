---
title: "Help with Google Earth &quot;signal 6&quot; error"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by raggiotralenuvole on 2013-02-12
I get the same crashlog as reggiehg (I tried both with gdebi & with usc, following the uninstall instructions each time):

> googleearth-bin: ../../../../../src/mesa/swrast/s_renderbuffer.c:588: map_attachment: asserzione "srb->Map" non riuscita.
Google Earth has caught signal 6.

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:


> Major Version 7
Minor Version 0
Build Number 0002
Build Date Dec 13 2012
Build Time 17:54:43
OS Type 3
OS Major Version 3
OS Minor Version 5
OS Build Version 0
OS Patch Version 0
Crash Signal 6
Crash Time 1360684973
Up Time 4,62596

Stacktrace from glibc:
./libgoogleearth_free.so(+0x1e9fab)[0xb75a3fab]
./libgoogleearth_free.so(+0x1ea1f3)[0xb75a41f3]
[0xb7731400]

Is there a solution?

---

### Post by raggiotralenuvole on 2013-02-16
up

---

### Post by oldos2er on 2013-02-16
Posts moved to their own thread. Please start a new thread rather than posting in someone else's older one. You're much more likely to receive timely help that way.

---

### Post by Impavidus on 2013-02-16
Signal 6 is abort, typically send by programs to themselves using the abort() function whenever they encounter an unrecoverable error. As the error message indicates, this is a bug in Google Earth.

If the crashes are avoidable, try to avoid them. In the past I have seen very consistent crashes when zooming in on terrain below sea level and memory leaks when zooming in on 0&#8304;N 0&#8304;E, but these have been fixed. I expect this one soon to be fixed too.

If they are too annoying you can try the previous version (6.2, go to the download site of google earth and click "advanced settings"). Not much else you can do. This is closed software.

---

