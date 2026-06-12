---
title: "What is gvfs-fuse-daemon?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Stunt Double on 2008-06-30
I just completed a clean install of 8.04, and then added a lot of software from Add/Remove and Synaptic Package Manager.
  When I checked with GtkDiskFree, the total hard drive capacity is doubled from 18.5 GB to 37 GB. The error also appears in Disk Usage Analyzer. Only Gparted gets it right.
   As shown in DiskFree:
Filesystem~~~~~~~~~~Size~~~~Used Space~~Free Space~~~~~~~Mount dir.

lrm~~~~~~~~~~~~315.02M~~~~37.28M~~~~~277.74M~~~/lib/modules/2.6.24-19-g...
/dev/sda1~~~~~~~~~17.68G~~~~~3.71G~~~~~~13.98G~~~~/
gvfs-fuse-daemon~~~~17.68G~~~~~3.71G~~~~~~13.98G~~~~/home/stuntdbl/.gvfs
All mounted~~~~~~~36.91G~~~~~7.45G~~~~~~29.46G~~~~None

  Gvfs doesn't appear on any of my other Ubuntu computers, and I have no idea what it is or what it does. Can I safely remove it ? And, if so, how ?
  Thanks

---

### Post by sdennie on 2008-06-30
It's a userspace filesystem that gnome uses.  For instance, if you mount network drives via nautilus, they are accessable from ~/.gvfs.  I don't recommend removing it and you can safely ignore it on outputs that show it.

---

### Post by Stunt Double on 2008-06-30
Thanks for the help.

---

### Post by Stunt Double on 2008-06-30
gvfs = Gnome Virtual File System

---

