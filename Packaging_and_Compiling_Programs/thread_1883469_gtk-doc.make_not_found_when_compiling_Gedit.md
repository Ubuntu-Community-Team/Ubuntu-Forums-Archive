---
title: "gtk-doc.make not found when compiling Gedit"
date: 2011-11-19
forum: Packaging and Compiling Programs
---

### Post by notgary on 2011-11-19
When I try to run autoconf on the Gedit source, I get the following error:

```
automake: cannot open < gtk-doc.make: No such file or directory
```

Googling has told me that I need to have **gtk-doc-tools** installed, which I did by installing **gnome-core-devel**. Does anyone know what I need to do to fix this?

---

### Post by gmargo on 2011-11-20
Try using apt-get to pull in the build dependencies:
```

apt-get build-dep gedit

```

---

### Post by notgary on 2011-11-20
Thanks for the suggestion, but that hasn't helped.

---

### Post by gmargo on 2011-11-20
Not sure what to tell you... I was able to compile the gedit source from 11.10 Oneiric.  Running autoconf on it works silently.  

Are you trying to compile that version?  Or the bleeding edge?

---

### Post by notgary on 2011-11-20
Ah, that's what my problem was. I was trying to compile the git branch hosted at Gnome itself, rather than the source from the Ubuntu repo. That's the the assist.

---

