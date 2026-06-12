---
title: "[SOLVED] compiled kernel way too big!"
date: 2008-01-10
forum: Packaging and Compiling Programs
---

### Post by Totzo on 2008-01-10
I just compiled a custom kernel (with the raid45 patch so I can mount my fakeraid 5 ntfs partition). All went very smoothly and now dmraid is behaving.

A weird thing happened though- I used the .config file for the normal ubuntu kernel and just added the raid45 as a module and ended up with a 550mb kernel! The build directory is about 2.5gb.

Does anyone have any ideas why this might have happened? I tried it with a vanilla kernel & an ubuntu patched one- same results.

This was my build command:

 fakeroot make-kpkg --revision=dmraid45 --initrd kernel_image kernel_headers

---

### Post by Totzo on 2008-01-10
just noticed that kernel debugging was enabled so compiling with that off now- hopefully this should make a diference?

Yep- that did it- 59mb deb now

---

### Post by greg_g on 2008-01-10
It would be helpful if you set this thread to "Solved" (under "Thread Tools" select "mark as solved" or something similar).

Glad you got it working though!

---

### Post by Totzo on 2008-01-10
> **greg_g said:**
> It would be helpful if you set this thread to "Solved" (under "Thread Tools" select "mark as solved" or something similar).

Glad you got it working though!

ta for pointing that out- fixed now :)

---

