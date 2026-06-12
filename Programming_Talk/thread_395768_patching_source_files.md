---
title: "patching source files"
date: 2007-03-28
forum: Programming Talk
---

### Post by josephus on 2007-03-28
Hi, can someone explain to me how to patch source files.

I'm trying to modify the gnome-panel (reduce the size of the black arrow under the main menu) and know how to do that for the most part.  I'm stuck however trying to apply the patches to the source.

I've downloaded from [http://packages.ubuntu.com/edgy/gnome/gnome-panel](http://packages.ubuntu.com/edgy/gnome/gnome-panel) the .dsc, .orig.tar.gz and the diff.gz files.

I would like to generate a new set of source files with all the patches applied.  So far I've used dpkg-source -x gnome-panel_2.16.1-0ubuntu3.dsc and it appears to extract the original source files plus creates the debian subdirectory which includes a set of patches.  Where do I go from there?  Thanks.

---

### Post by Mr. C. on 2007-03-29
Do you have the "patch" utility ?

```
apt-get install patch
```

if not.  And then,
```

man patch
```

Basically, you run
```

patch -p0 < patchfile
```

but the "p0" depends on what the paths are inside the patch file.

MrC

---

### Post by josephus on 2007-03-29
Thanks.  I managed to get the files more or less patched, but still find the whole system confusing.  The patches don't consistently refer to the same version of gnome-panel.  I'm sure that I'll eventually figure it out, and there will be a certain logic to the system.

---

### Post by Mr. C. on 2007-03-29
Not having seen the patches, nor the source, I can't tell you what is going on.

It is typical for a package program (apt, rpm) to have a script that drives the order of source code patching.  Out of context, a series of patches won't make much sense to you.  You need to examine the script that drives the building of that debian package.

MrC

---

### Post by josephus on 2007-03-30
ok. makes sense to me now.  i just didn't know how the ./debian/rules file worked.  all i needed to do was call ./debian/rules apply-patches from the base directory.

---

### Post by Mr. C. on 2007-03-30
Nice work, thanks for the update.

Cheers,
MrC

---

