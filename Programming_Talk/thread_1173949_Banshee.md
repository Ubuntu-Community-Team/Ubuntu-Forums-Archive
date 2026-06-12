---
title: "Banshee"
date: 2009-05-30
forum: Programming Talk
---

### Post by matmatmat on 2009-05-30
Does anyone know how you can use the Banshee API in your own c# programs
Does banshee use gstreamer (if so can anyone point me to a tutorial for that)?
Thanks in advanced...

---

### Post by SKLP on 2009-05-30
Banshee uses GStreamer (it has also support for Helix but Gstreamer on ubuntu at least).

Use the banshee API... Do you mean like extend banshee, e.g. create a plugin ?
Or do you want to use Gstreamer in your application? Sadly, the Mono Gstreamer bindings was so bad, banshee had to create their own Gstreamer mono binding (called libbanshee), which I would believe is not general-purpose enough for you to use it in your app.

---

### Post by directhex on 2009-05-30
> **SKLP said:**
> Banshee uses GStreamer (it has also support for Helix but Gstreamer on ubuntu at least).

Use the banshee API... Do you mean like extend banshee, e.g. create a plugin ?
Or do you want to use Gstreamer in your application? Sadly, the Mono Gstreamer bindings was so bad, banshee had to create their own Gstreamer mono binding (called libbanshee), which I would believe is not general-purpose enough for you to use it in your app.

Sebastien Droge is writing some new bindings.

---

