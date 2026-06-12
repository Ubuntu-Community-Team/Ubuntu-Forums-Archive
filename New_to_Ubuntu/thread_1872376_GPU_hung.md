---
title: "GPU hung"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by Southern Gent on 2011-10-30
First-timer installing ubuntu on cleaned hard drive. Proceeded O.K. to point on WHO ARE YOU screen where files are loaded and "ready when you are" message appears - then CONTINUE button won't work. Last message at bottom of screen is:"Ubuntu kernel [192.288547] [drm:i915_wait_request] *ERROR* 15_wait_request returns-11 (awaiting 93 at 88, next 94)". Two messages above that one mentions "GPU HUNG".

Where do I go from here?  Thanks.

---

### Post by Silent Warrior on 2011-10-30
While waiting for someone who might actually know, here's what my mighty grey matter interprets from your question:
The Ubuntu installer (Ubiquity) detects your GPU as an Intel i915 (or is it called Intel 915?), and this is apparently a problem.

If this is in fact your GPU (which is quite likely) I suggest you read up on your GPU in the community Wiki until you get another reply - you might find some clue. Maybe a dab of GRUB-voodoo, specific workarounds, etc.
To be honest, though: You're probably better off trying a distribution geared more towards older hardware. Intel's IGPs aren't usually considered even proper graphics hardware, and Ubuntu is moving towards a desktop that requires 3D acceleration. That said, Lubuntu or Xubuntu might be just the thing(s) for you. I'd recommend anything without Gnome Shell (GNOME 3 Fallback?) and Unity - KDE's compositing can actually be toggled on the fly, though I strongly suspect the i915 will be under severe strain even then.

---

### Post by Southern Gent on 2011-11-05
Thanks for the info. CPU is over 8 years old and is probably the problem. Guess I'll try another OS.

---

### Post by Browncoyote on 2012-01-22
I experience gpu hang on an old box (Dell 2400) that is running 10.04, it ran fine on 8.04. Mostly, just sharing the story for beans and to bump this thread as it may effect average users and the answer is kinda hard to find.

---

