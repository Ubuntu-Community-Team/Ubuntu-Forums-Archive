---
title: "Media issues in Hardy and others"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by amgc5 on 2008-05-22
Several issues to address....

1. DVD doesn't get recognized. I installed vlc, kaffine, used mediabuntu, w32codecs for vlc and when I insert a DVD nothing shows up on the desktop. Further, any attempt to access the DVD drives results in the following error " Unable to mount location...can't mount file". MP3 CD's got recognized and play just fine. I have some wma clips which worked as well. So not sure where to start?

2. What is the equivalent of "disk fragment" and  "device manager" in ubuntu hardy.

3. Need some s/w to burn media...

4. lastly, any simple way to shrink the size of the icons on the desktop. I did try "appearance preferences> fonts", is that the only way?

Thanks!

---

### Post by lswest on 2008-05-22
to shrink the size of the icons you can right-click and choose "stretch icon" and then shrink them, or you can change the zoom level by doing: ```
gconf-editor
``` and going to /-->apps-->nautilus-->icon_view and changing "default_zoom_level to "small" instead of "standard".

for DVDs, have you installed libdvdcss2? ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``` (run each line as one command) and then do ```
sudo apt-get install libdvdcss2
``` and see if that works.

burning software: Brasero (applications-->sound and video-->Brasero Disc Burning)

you don't need to defragment ext3 filesystems (they do it automatically, and fragmentation is hardly a concern in Linux) and for device manager i do ```
lshw
``` in the terminal.

**note: all my commands are meant to be run in the terminal (applications-->accessories-->terminal) and i assume you're running Ubuntu 8.04 with GNOME**

---

