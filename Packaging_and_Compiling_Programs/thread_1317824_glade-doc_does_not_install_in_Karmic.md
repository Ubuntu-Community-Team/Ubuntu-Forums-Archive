---
title: "glade-doc does not install in Karmic"
date: 2009-11-07
forum: Packaging and Compiling Programs
---

### Post by Piscium on 2009-11-07
I cannot install glade-doc in Karmic, get the following error:

glade-doc: Depends: libscrollkeeper0  but it is not installable

The libscrollkeeper0 package is available in Jaunty, but appears to have been forgotten in Karmic, or there was some other packaging problem.

[http://packages.ubuntu.com/jaunty/libscrollkeeper0]("http://packages.ubuntu.com/jaunty/libscrollkeeper0")

Any ideas how to solve this? Should I download it from Jaunty to use on Karmic?

---

### Post by SevenMachines on 2009-11-07
This isnt really the forum for this, you might want to try one of the other support forums. rarian-compat has replaced scrollkeeper, thats why scrollkeeper is no longer available. the glade-doc dependency is a bug so you might want to file a bug in launchpad about this

---

### Post by Piscium on 2009-11-07
> **SevenMachines said:**
> This isnt really the forum for this, you might want to try one of the other support forums. rarian-compat has replaced scrollkeeper, thats why scrollkeeper is no longer available. the glade-doc dependency is a bug so you might want to file a bug in launchpad about this

Thanks 7Mach, I have filed a bug in Launchpad.

A.

---

