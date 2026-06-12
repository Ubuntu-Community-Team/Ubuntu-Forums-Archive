---
title: "New stable NVidia driver 275.19 released"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-15
NVidia has released a new stable driver 275.19.
> 
Added support for the following GPU: GeForce GT 540M
Fixed memory error and abort reported by glibc when running the application FieldView from Intelligent Light.
Fixed an OpenGL driver bug that caused an application crash when running Altair HyperMesh.
Fixed a performance problem when switching between stereo and monoscopic rendering in the application Smoke.
Fixed poor X driver handling of pixmap out of memory scenarios.
Fixed an interrupt handling deficiency that could lead to performance and stability problems when many NVIDIA GPUs shared few IRQs.
Fixed bugs in the VDPAU presentation queue that could cause GPU errors and hangs when destroying a presentation queue. This happens when exiting applications, and also when toggling to and from full-screen mode in Adobe Flash.


The 280 series is beta ATM.

---

### Post by MAFoElffen on 2011-07-15
> **Harry33 said:**
> NVidia has released a new stable driver 275.19.


The 280 series is beta ATM.
Thanks Harry33!  LOL  I'm starting to think you either sit on the refresh button on these or are psychic...  I'm hoping this fixes a few thing that have been challenged.

---

### Post by VinDSL on 2011-07-16
Still no relief for us 1 GB RAM users though, yes?!?!?

I'll try it in the morn, when I awake, but I doubt it will cure my excessive RAM usage problems.  I think that concern is independent of nVidia (et al.) and falls strictly on Canonical's shoulders.

In the meantime, Nouveau is working a treat on this machine, RAM-wise (1/3 the usage of nVidia drivers).

I'm sorely missing the "Digital Vibrance Control (DVC)" feature in the nVidia x-server settings.

If Nouveau had this, or something similar, I would never switch back.

Just saying...

EDIT

Linkage:  [http://www.nvidia.com/object/feature_dvc.html](http://www.nvidia.com/object/feature_dvc.html) (nVidia DVC description)

The pics on the left look like a direct comparison between Nouveau and nVidia.

Nouveau is rather pastel-like -- much the same as nVidia with a DVC setting of "0" (default).

nVidia with a DVC setting of "7" - like the segments on the right - is breathtakingly beautiful.  ;)

Alas, Nouveau has no such feature AFAIK.

---

### Post by BigCityCat on 2011-07-16
My mouse keeps flickering and disappearing with this driver. I'm using Kubuntu and the nouveau driver works much better for me, but I'm not using a lot of effects either.

---

