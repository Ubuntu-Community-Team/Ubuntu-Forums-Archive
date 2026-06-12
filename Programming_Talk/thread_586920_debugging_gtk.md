---
title: "debugging gtk"
date: 2007-10-22
forum: Programming Talk
---

### Post by dchenbecker on 2007-10-22
Quick question. Is there a way to install a package for debug-enabled GTK? I'm tracking down a problem with GTK key handling (launchpad: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/154912](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/154912)) and I can only find the debug symbols. I'm really looking for a way to get the gtk-debug and gdk-debug options to work.

Thanks,

Derek

---

### Post by dchenbecker on 2007-10-22
Well, I've given up on finding a package. I went ahead and downloaded the GTK source ,built it with debug enabled and now I'm using the debug libs via LD_LIBRARY_PATH.

Derek

---

### Post by sdbtietz on 2009-06-12
How did you accomplish that?  I'm facing a similar situation, needing to step into GTK.  I tried this:

export LD_LIBRARY_PATH="/home/btietz/src/gtk+-2.15.3/btietz_bld/gtk/.libs /home/btietz/src/gtk+-2.15.3/btietz_bld/gdk/.libs /lib64 /lib"

And ran my app, but cat /proc/7833/maps | grep gtk (with 7833 being the PID assigned to my app) still shows:

etc etc /usr/lib64/libgtk-x11-2.0.so.0.1400.4

So then I tried this, hoping to break the loader and at least see what's missing as a starting point to fill in the blanks:

export LD_LIBRARY_PATH="/home/btietz/src/gtk+-2.15.3/btietz_bld/gtk/.libs /home/btietz/src/gtk+-2.15.3/btietz_bld/gdk/.libs"

But when I ran my app, the loader ignored LD_LIBRARY_PATH and still went to /usr/lib64 and /usr/lib

I sure wish there was a static library version of GTK to make this sort of exercise easier...

---

### Post by dchenbecker on 2009-06-14
Hmmm. It's been a while since I did this, but IIRC, LD_LIBRARY_PATH just worked for me. The other thing you could try is an explicit LD_PRELOAD set to the exact libraries you want to use, but that may not work since there are a lot of intertwined GTK libs and version mismatches don't always play nice.

---

