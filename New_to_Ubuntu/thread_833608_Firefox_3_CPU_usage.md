---
title: "Firefox 3 CPU usage"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by lesjohn on 2008-06-18
When Firefox 3 is trying to load a page (from a very slow server, for example), Xorg CPU usage goes up to ~40-45% and Firefox itself reaches ~30-35% for upwards of ten seconds, and as a result everything else on the computer (most noticeably Rhythmbox playback) runs slowly.  Is there anything I can do about this?  I'm running the powerpc port, but I'm not sure if this is powerpc-specific.

---

### Post by Corrupt3d on 2008-06-18
Hi,

you might want to try this and see if it works.


System>Admin>Sys Monitor

Right-Click on the Nice Values & select 'Priority', from there modify firefox. Higher value will make firefox play nicer and ask for less system resources.

Its faster to do it from the command line.

<use top to find the PID of your process>
$ top
<use 'q' to quit>

$renice <new nice value> <PID>

ex: $renice 10 24900 # changes process number 12365 to 10 
24900: old priority 0, new priority 2

---

### Post by lesjohn on 2008-06-18
Great, that seemed to do the trick (or else I've just had good luck the last couple minutes).  Is there any way to make it so firefox processes automatically get low priority?

---

### Post by danf_1979 on 2009-01-08
> **lesjohn said:**
> Great, that seemed to do the trick (or else I've just had good luck the last couple minutes).  Is there any way to make it so firefox processes automatically get low priority?

Sure, you can use the "nice" program. Edit the menu launcher for firefox, with something like this:

```

nice -n NUMBER firefox %u

```

and replace NUMBER with the priority you want. For more info: $ man nice.

---

