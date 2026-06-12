---
title: "USB Device Insertion Notification and libusb"
date: 2009-03-18
forum: Programming Talk
---

### Post by BillRebey on 2009-03-18
I'm using libusb with C/C++ to interact with USB devices, but the libusb documentation clearly states that it does not provide notification of USB devices being inserted/removed.

Can anyone point me to a way to get some sort of event or interrupt or signal or something when a USB device is inserted?

---

### Post by WitchCraft on 2009-03-18
Take a look at the source of autofs (kernel-based automounter for Linux).

apt-get build-dep autofs
apt-get source autofs

---

### Post by cabalas on 2009-03-18
Doesn't the hal emit a signal via D-Bus whenever a usb device is inserted/removed?  If you hook into that you should be fine.

---

### Post by DominaDoom on 2009-04-09
After running 

> apt-get source autofs

I get 

> E: You must put some 'source' URIs in your sources.list

---

### Post by BillRebey on 2009-04-24
Cabalas,

Thanks for the D-Bus pointer.  That sounds like the ticket I'm looking for.  However, I've scoured the Web for information and instruction on the use of D-Bus and GLib, and the only place I'm getting is frustrated.

I've installed dbus and glib, but the only binding header I get is "usr/include/dbus-1.0/dbus/dbus-pygthon.h".  I need a "...dbus-glib.h", but it's not anywhere to be found.

I found several links to various versions of the dbus-glib.h header file, but they are all different, and all include various other g???? files that I don't have.

Can you point me to a resource that clearly explains how to get started with D-Bus and Glib from installation to "Hello World"?  Nothing I'm coming across starts from scratch, and I'm apparently missing something in the translation.

Thanks for your help!

---

