---
title: "Minimal Linux for superfast boot"
date: 2008-02-12
forum: Other OS Talk
---

### Post by [h2o] on 2008-02-12
For a certain project I need to use a really slimmed Linux distribution inside a virtual machine.

There is no need for X.

What I want is something that:
1. Boots really really really fast. Preferably as close to 0 seconds as possible. But to be realistic I am aiming around 2-5 seconds from boot to login.
2. Can still run quite complex programs like GCC, octave, python, ... I.e there is probably some services that need to start and some libraries that need to load.
3. Preferably have some kind of package management. APT, RPM or whatever.

Does anyone have any suggestions on where to start looking?

---

### Post by Don S on 2008-02-12
Have you looked at Damn Small Linux? And removing all unnecessary stuff?

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

I have totally no idea where you should start looking, if you want anything smaller.

---

### Post by GeneralZod on 2008-02-12
> For a certain project I need to use a really slimmed Linux distribution inside a virtual machine.

Can you tell us more? If it is to run only in a VM, then you might look into taking memory "snapshots" of a fully-booted session (Qemu, at least, can do this) which circumvent the whole "booting" process entirely.

---

### Post by K.Mandla on 2008-02-12
Moved to Other OS Talk.

---

### Post by [h2o] on 2008-02-13
> **GeneralZod said:**
> Can you tell us more? If it is to run only in a VM, then you might look into taking memory "snapshots" of a fully-booted session (Qemu, at least, can do this) which circumvent the whole "booting" process entirely.

Well, I want to run stuff (often calculations) inside a virtual machine. The superfast boot is needed to not have me having to wait 20 extra seconds for each run.

So what I really want is to do run something like "run-vm myosdisk indata" and have it do stuff. If there is indeed a way to go directly to a fully booted session then that would be really nice.

Any other suggestions?

---

### Post by tdrusk on 2008-02-13
[http://www.machboot.com/](http://www.machboot.com/)

---

### Post by init1 on 2008-02-13
I've gotten 3 or so second boot by running a floppy linux on a hard drive. You'll get a bash shell and busybox, but not much else. 
[http://www.toms.net/rb/](http://www.toms.net/rb/)
Another option is FreeDOS. It's DOS not Linux, but it boots in a few seconds and has quite a few applications availible for it.  
[http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/)
[http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/pkgs/](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/pkgs/)

---

### Post by Shazaam on 2008-02-13
+1 on tomsrtbt from floppy. VERY fast.

---

### Post by [h2o] on 2008-02-14
Thanks for the help. Using saved states/sessions seem to be what I need.

Now I am just going to try to reduce the system size. I am not sure how much one can strip down Debian. I'd really like to use APT, but ordinary Debian is just too big.

---

### Post by jseiser on 2008-02-14
have you though of using crux? I mean, its minimal, and you compile the kernel so strip everything out that you dont need.  The package manager is a ports system that is nice.  As far as speed and boot speed, you wont get a udev hang or anything, so i would try it.  Def faster than a debian system.

---

