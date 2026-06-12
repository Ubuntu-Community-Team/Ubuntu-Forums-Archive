---
title: "Compiling, need to know how to apply patches, etc."
date: 2007-03-20
forum: Programming Talk
---

### Post by Mateo on 2007-03-20
I'm attempting to modify the gnome-panel and compile it from source.  Here is the source I am working with:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/2.18.0-0ubuntu2](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/2.18.0-0ubuntu2)

Modifying the parts I need is no problem.  However, I don't know how to apply the patches that come with it and such. I have no experience doing this.  So if I download the source and do a simple compile (./configure, make, make install), it doesn't turn out right because of the ubuntu patches.  How do I apply these?  there are 2, one is a "diff" and another is a "dsc".  thanks.

---

### Post by lnostdal on 2007-03-20
use the patch-program .. see man 1 patch

---

### Post by Mateo on 2007-03-29
what about the DSC file.  what do you do with that?

---

