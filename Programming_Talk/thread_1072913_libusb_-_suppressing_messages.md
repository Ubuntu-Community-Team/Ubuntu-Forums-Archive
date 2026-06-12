---
title: "libusb - suppressing messages"
date: 2009-02-17
forum: Programming Talk
---

### Post by anewguy on 2009-02-17
I have a cross-platform app that I use libusb and GTK in.  In Linux (Ubuntu 8.04 and 8.10) my GTK window is the only window that shows, as it should be.  In Windows, using libusb-win32, GTK for Windows, mingw and msys, I get an "extra" window besides the application window.  This window appears to be stdout or something used by the libusb calls, in particular the call to find usb busses.  All that ever appears in that windows is found xxxx busses.

I have done some research, some indicated going to libusb-1.12 in place of libusb-1.10 in Windows would fix it - it didn't.  Others indicated a problem with debugging code in libusb and suggest using an environment variable of USB_DEBUG set to a value of 0.  I have done that as well with no difference.

Does anyone know what is causing this and how to fix it?  I'm almost thinking I'm going to have to redirect stdout to null somehow in the program right before it gets the usb busses, then redirect it back to normal right afterwards, but that seems like a rather dumb way of doing things.

Since I don't have this problem in Linux, I have to assume it must have something to do with the Windows port of libusb, but I have no idea what.

Thanks in advance!

Dave :)

---

### Post by anewguy on 2009-02-18
By redirecting stdout via freopen just prior to the call to get the busses, and then redirecting back right afterwards, I am able to eliminate the text in the extra window, however the extra window still remains - it just stays blank the entire time.

Any help/insight would be greatly appreciated!

dave :)

---

### Post by anewguy on 2009-02-18
Found the solution - had to add -mwindows to the gcc line so it knows to generate a windows based app and therefore not generate the extra window.

Dave :)

---

