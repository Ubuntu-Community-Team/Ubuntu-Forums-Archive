---
title: "[SOLVED] gvfs-fuse-daemon"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by anthropoidster on 2008-05-27
In my Hardy 'System Monitor' --> 'File Systems' there is the listing:

Device: gvfs-fuse-daemon
Directory: /home/xx/.gvfs
Type: fuse.gvfs-fuse-daemon

The other columns regarding size are the same as the / Directory which is also listed.
In the /home/xx/ directory is the .gvfs directory which is empty.

What is this?  I don't have it in either Gutsy or Feisty.
Any ideas?

---

### Post by bodhi.zazen on 2008-05-27
It is a new feature, gnome-vfs (AKA gvfs)

[http://library.gnome.org/devel/gnome-vfs-2.0/stable/](http://library.gnome.org/devel/gnome-vfs-2.0/stable/)

[https://wiki.ubuntu.com/GvfsInHardy](https://wiki.ubuntu.com/GvfsInHardy)

Basically it integrates various filesystems with gnome, for example if you mount samba or nfs shares via Places -> Network the share will be mounted in ~/.gvfs

---

### Post by anthropoidster on 2008-05-27
Thanks for that. Interesting.
And thanks also for some of your other great work here which has saved me on more then one occasion, especially your How to Fstab.
Thanks again.

---

### Post by bodhi.zazen on 2008-05-28
You are most welcome, glad it helped.

---

