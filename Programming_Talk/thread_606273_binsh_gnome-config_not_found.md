---
title: "/bin/sh: gnome-config: not found"
date: 2007-11-07
forum: Programming Talk
---

### Post by Mark Grice on 2007-11-07
If this has been answered elsewhere, I apologize... but I looked and can't find it.

I'm trying to come up to speed on GNOME development. I found this tutorial:

[http://www.ibm.com/developerworks/library/l-gnomenclature/]("http://www.ibm.com/developerworks/library/l-gnomenclature/")

And downloaded the source and makefile. I *THINK* I have all of the development files installed. But when I run the makefile, I get an error:

```
***/bin/sh: gnome-config: not found***
```

And then of course, it can't find anything. In poking around on Google, it seems like the gnome-config is no longer used? Is that right?

Does anyone know how I can change the makefile to work?

---

### Post by geirha on 2007-11-08
gnome-config is installed by the package libgnome-dev, the older gnome library.

---

### Post by Mark Grice on 2007-11-08
> **geirha said:**
> gnome-config is installed by the package libgnome-dev, the older gnome library.

So... what is the best thing to do. Install the older gnome library? Or change the makefile.

Is there a current preferred config to run?

---

### Post by arcadeus on 2010-01-10
[FONT=monospace]Currently supported config is [/FONT][FONT=monospace]pkg-config.
Simply replace [/FONT][FONT=monospace]"gnome-config"[/FONT] with "[FONT=monospace]pkg-config"[/FONT] in [FONT=monospace]command lines.[/FONT]

---

