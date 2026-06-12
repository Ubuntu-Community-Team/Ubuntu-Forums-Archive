---
title: "Control System Volume progammatically"
date: 2010-01-02
forum: Programming Talk
---

### Post by tsg on 2010-01-02
Hi does someone know how I can set the computers Volume from my own C++ programm?

A C++ code snipped would be great, but a simple cli command would be ok too.
So I could do a system call. But I don't even know how to set the volume using the command line.

Also I'm not sure if this is a gnome thing, or a system level problem. But it would be nice if the little gnome popup would appear

Thank you for any hint.

---

### Post by ssam on 2010-01-02
looking at the gnome volume control source [http://git.gnome.org/browse/gnome-applets/tree/mixer/applet.c?h=gnome-2-28](http://git.gnome.org/browse/gnome-applets/tree/mixer/applet.c?h=gnome-2-28) it seems to use GstMixer [http://www.gstreamer.net/data/doc/gstreamer/head/gst-plugins-base-libs/html/gst-plugins-base-libs-gstmixer.html](http://www.gstreamer.net/data/doc/gstreamer/head/gst-plugins-base-libs/html/gst-plugins-base-libs-gstmixer.html)

i am sure it can also be done with d-bus, but you will have to hunt around.

---

