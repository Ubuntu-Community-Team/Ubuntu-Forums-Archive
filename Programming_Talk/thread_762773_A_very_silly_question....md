---
title: "A very silly question..."
date: 2008-04-22
forum: Programming Talk
---

### Post by Metallion on 2008-04-22
Hello, I'm trying to play around a bit with USB devices here. I've got a device and I want to use C++ and libusb to see what I can do with it.

I installed both the libusb-0.1-4 and libusb++-0.1-4c2 packages. Now the problem I have is that I can't get them included in my C++ program.

I tried typing #include <usb.h> and #include <usb> but g++ always tells me that there's no such file.

Can anyone help me out here?

---

### Post by Tuna-Fish on 2008-04-22
Try installing libusb-dev and libusb++-dev.

In ubuntu, the developement headers are almost always separated to their own package.

---

### Post by WW on 2008-04-22
Install the package [libusb++-dev](http://packages.ubuntu.com/gutsy/libusb++-dev).


P.S. It's not a silly question.  I suspect everyone runs into this situtation when they first try to write a program in a Linux distribution that separates the run-time library packages from the development packages.

---

### Post by EXCiD3 on 2008-04-22
-dev packages are the ones needed for development to use with the normal packages usually. like they said try libusb++-dev.

---

### Post by Metallion on 2008-04-22
Alright this worked. :D Thanks everybody!

---

