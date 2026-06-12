---
title: "Howto use dkms to fix broken kernel module bug 582809"
date: 2010-10-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Paul S on 2010-10-06
It's possible to use dkms to build the psmouse module for the buttonless synaptics touchpad on some newer netbooks.  See bug 582809 at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809")

First make sure dkms package is installed.

Next download this patched source archive for the psmouse module from kernel 2.6.35-22-generic on maverick.  It's called psmouse-2.6.35-22-generic-patched.tar.bz2 and attached to this thread.

In a terminal, unpack the source archive in /usr/src

Next, in a terminal, enter these commands:

```
sudo dkms add -m psmouse -v 2.6.35-22-generic
sudo dkms build -m psmouse -v 2.6.35-22-generic
sudo dkms install -m psmouse -v 2.6.35-22-generic

```
This should install the psmouse.ko module in /lib/modules/<kernel version>/updates/dkms.  Reboot to load it.

If the mouse doesn't function properly, use this command to check if it's installed.

```
sudo dkms status -m psmouse -v 2.6.35-22-generic

```
If it's not, then try rebuilding it with

```
sudo dkms build -m psmouse -v 2.6.35-22-generic
sudo dkms install -m psmouse -v 2.6.35-22-generic

```
Once a new kernel is issued with a fix, then you can remove it with:

```
sudo dkms uninstall -m psmouse -v 2.6.35-22-generic
sudo dkms remove -m psmouse -v 2.6.35-22-generic --all

```
I also believe that dkms will automatically build and install it on any kernel upgrade, but haven't tested that yet.

After installing any kernel update, you can test with

```
sudo dkms status -m psmouse -v 2.6.35-22-generic

```
and if it's not built, use the above commands to build and install it.

Reboot to make it effective.

For more info, see man dkms for the official documents.

---

