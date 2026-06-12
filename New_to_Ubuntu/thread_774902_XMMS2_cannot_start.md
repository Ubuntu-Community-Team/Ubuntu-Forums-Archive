---
title: "XMMS2 cannot start:"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by diaz028 on 2008-04-29
> diaz@diaz-desktop:~$ xmms2-launcher -v
Log output will be stored in /home/diaz/.cache/xmms2/xmms2d.log
startup failed!
diaz@diaz-desktop:~$ 


output:

> --- Starting new xmms2d ---
 INFO: ../src/xmms/log.c:36: Initialized logging system :)
 INFO: ../src/xmms/config.c:760: No configfile specified, using default values.
 INFO: ../src/xmms/ipc.c:893: IPC listening on 'unix:///tmp/xmms-ipc-diaz'.
 INFO: ../src/xmms/xform.c:1295: Successfully setup chain for 'file:///usr/share/xmms2/mind.in.a.box-lament_snipplet.ogg' (1) containing file:magic:vorbis
 INFO: ../src/xmms/main.c:499: Using output plugin: alsa
 INFO: ../src/xmms/main.c:319: Installing scripts from /usr/share/xmms2/scripts/startup.d
ERROR: ../src/xmms/main.c:322: Global script directory not found

--- Starting new xmms2d ---
 INFO: ../src/xmms/log.c:36: Initialized logging system :)
ERROR: ../src/xmms/ipc.c:881: Couldn't setup IPC listening on 'unix:///tmp/xmms-ipc-diaz'.
FATAL: ../src/xmms/main.c:476: IPC failed to init!


---

### Post by nawitus on 2008-04-29
This is not really an answer, but audacious does pretty much everything that XMMS2, you should try using that. I had crashes often with xmms2, but Audacious has been stable so far.

---

### Post by diaz028 on 2008-04-30
Audacious works awesome!

-D

---

### Post by fontenot_1031 on 2008-05-13
ugh same problem here but would rather not switch to Audacious.

---

### Post by SunnyRabbiera on 2008-05-13
> **fontenot_1031 said:**
> ugh same problem here but would rather not switch to Audacious.

yeh but XMMS is pretty much dead so sorry.

---

### Post by billgoldberg on 2008-05-13
> **SunnyRabbiera said:**
> yeh but XMMS is pretty much dead so sorry.

I thought it already was.

---

### Post by Phreakazoid on 2008-11-12
XMMS2 is a different program to XMMS.

It's more like MPD than it is like XMMS.

XMMS = X MultiMedia System
XMMS2 = X Music Multiplexing System

---

### Post by Phreakazoid on 2008-11-12
This error happens when there is already an instance of xmms2d running, and you try to start another. Make sure there isn't already one running before trying again.

---

### Post by emecas on 2009-01-07
same to me.... Audacious works great!!!

---

