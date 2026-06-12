---
title: "Datestamp changes when copying from USB drive"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by silkstone on 2008-06-05
Using Hardy to copy files from a USB drive using Nautilus (flash or external HD, formatted FAT32) the date and time on all files changes to the current date/time. This never used to happen with Feisty - the original datestamp would be retained.

I can get over this by using Grsync or the cp -p command, but that's a nuisance and I'd like to be able to drag-and-drop files in Nautilus without the file date changing.

Any ideas. or am I doing something wrong?

---

### Post by philinux on 2008-06-05
This is a current bug.

Use cp and preserve timestamp or use gnome-commander from synaptic.

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/215499](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/215499)

---

### Post by silkstone on 2008-06-05
Thanks philinux.

EDIT/ I've installed gnome-commander and (although it doesn't replace drag-and-drop) it looks like a great application - so thanks again!

---

