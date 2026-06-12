---
title: "[SOLVED] Building personal Ubuntu from server edition"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Ru$$i@N on 2008-07-30
Hello everybody,

I'm trying to customize Ubuntu to my needs for school work and stuff, and i decided to make Ubuntu from *almost* scratch.

I installed a server edition of ubuntu 8.04.1 (32 bit) on my laptop and fluxbox on top of it (i LOVE fluxbox). However, i found several problems with that. The system runs super-fast, but conky shows that my cpu is heated up to 55-56 C all the time, so the fan never stops.

I have an averatec 2370 laptop (AMD Turion 64 x2, but i would like a 32 bit system), and i think that the processor is running on full speed all the time, even with practically no load. With desktop ubuntu edition, i think, powernowd did a lot for me.

Battery life, laptop temperature and quietness are of great importance to me.

If you could list here or point me to a tutorial or a how-to on how to build a personal system from server edition, or any ideas on what do i need to cool down my Athlon, i'd appreciate that.

Thank you,

Russkie :P

--- EDIT

I ended up installing Xubuntu, disabling some stuff there, and installing Fluxbox WM and Awesome WM on top. I think i'll be switching a lot between the sessions, so i installed SLiM login manager, and uninstalled GDM (cause i don't need it anymore). With SLiM i can just press F1 to change what session i want to login into (the default theme is really nice too :)) 

For those, who want to build ubuntu from server edition, i'd say look up all the *must-have* packages that come with desktop editions and go ahead and install them. Sorry that i can't be of a greater help.

---

### Post by tuxxy on 2008-07-30
Try the server doucmentation

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

As for the processor can you not open up your processes and see which process is hogging the CPU.

---

### Post by eightmillion on 2008-07-30
You can install powernowd from the repos.
> sudo apt-get install powernowd

---

### Post by Ru$$i@N on 2008-07-30
Thank you for such quick replies! :)

I'm sorry if i didn't make it clear, the processor is not loaded at all!! that's the thing :( i think it's just running on full 1.6 GHz instead of dropping to 800 MHz when not loaded.

---

### Post by Ru$$i@N on 2008-08-02
> **eightmillion said:**
> You can install powernowd from the repos.

yup, that did it. i'm surprised i didn't do it right away. the laptop still heats up pretty badly, but at least the fan switches off every now and then.

I edited the top post for those who want to know what i did.

---

