---
title: "The udev Thing with 11.10 Alpha 1"
date: 2011-06-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fjgaude on 2011-06-05
I've not been able to run, much less install, the LiveDVD or thumb drive with 11.10 Alpha 1. I get this error message: udevd[72] error cannot /run/udev, not writable. Going to use /dev/udev... or something to this effect.

Does anyone know what this is about, and how to proceed?

---

### Post by cariboo on 2011-06-05
Are you waiting long enough for the command to time out? I get the message on two systems, After about a 10 second pause, the system continues to boot.

---

### Post by fjgaude on 2011-06-05
On the LiveDVD after waiting awhile it goes onto a blue screen. Then nothing. I can apt-get update (using ctrl-alt-F1), etc. from a command line but to what use?

On a flash drive I waited and waited at least five times and nothing, never getting the blue screen.

I had the same issue with many daily builds, even today's. Of course 11.04 works perfectly. My hardware could be at issue with 11.10.

Any ideas?

---

### Post by wildmanne39 on 2011-06-05
Hi, I get the same message but then it boots in a few seconds.

---

### Post by floydsp on 2011-06-06
> **fjgaude said:**
> I've not been able to run, much less install, the LiveDVD or thumb drive with 11.10 Alpha 1. I get this error message: udevd{72] error cannot /run/udev, not writable. Going to use /dev/udev... or something to this effect.

Does anyone know what this is about, and how to proceed?

I get the same thing...never boots if I start the recovery
it show fallback graphic FAIL

floydsp

---

### Post by dino99 on 2011-06-06
have you the latest 171-0ubuntu3 ? (work fine here)

---

### Post by fjgaude on 2011-06-06
My Intel CPU, i5, uses the integrated graphics driver, which 10.10 and 11.04 handle nicely. 10.04 didn't and now it seems 11.04 doesn't, at least for now, after all it's Alpha 1. If no one else has any ideas I'll have to just wait and see.

Note: Okay, the issue was fixed with today's daily build. Got to Unity shell, and could see what was being done.

---

