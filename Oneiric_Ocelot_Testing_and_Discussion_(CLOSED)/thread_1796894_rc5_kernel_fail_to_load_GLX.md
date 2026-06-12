---
title: "rc5 kernel fail to load GLX"
date: 2011-07-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-07-04
wonder if i'm the only one:

Failed to initialize the GLX module, logged into xorg.log, with nvidia

---

### Post by jfernyhough on 2011-07-04
I have to reinstall my drivers. Once done I can restart GDM and it works as normal. It's a bit weird. :)

$ sudo aptitude reinstall fglrx
$ sudo service restart gdm

(Yes, I have aptitude installed.)

---

### Post by Harry33 on 2011-07-04
> **dino99 said:**
> wonder if i'm the only one:

Failed to initialize the GLX module, logged into xorg.log, with nvidia

I did not have to reinstall nvidia-current. The linux kernel 3.0-3.4 (rc5) is working OK.

---

