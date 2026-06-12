---
title: "Anyone using Mojo SDK in Jaunty x64?"
date: 2009-07-29
forum: Programming Talk
---

### Post by gtr32 on 2009-07-29
Palm seems to have Debian x32 package available but I can't install it on my x64 machine. Anyone using it in x64 or know how to install x32 packages on x64 system?

---

### Post by ljoslin on 2009-08-02
I would like help with this as well!  Thanks!

-=ljoslin=-

---

### Post by Xerran on 2009-08-09
> **gtr32 said:**
> Palm seems to have Debian x32 package available but I can't install it on my x64 machine. Anyone using it in x64 or know how to install x32 packages on x64 system?


Make that three of us that need that info. It is 2009 and you would think that Palm would get with the damn program, I had the same issue in vista x64 but found a workaround.

---

### Post by Xerran on 2009-08-09
Once you have the "SDK" and "Novacom" downloaded go to terminal and install like so:

sudo dpkg --force-architecture -i palm_mojo_sdk-Ubuntu-1.1.0-sdk62-hud25_i386.deb

sudo dpkg --force-architecture -i palm-novacom_0.3-svn177284-hud9_i386.deb



You can thank destinal and JackRipper over at the #webos-internals IRC. :guitar:

---

### Post by henryjuan on 2009-08-11
My Palm Emulator(sdk62) is no sound, though I have enabled Audio settings on VirtualBox. Do you have the same situation?

---

