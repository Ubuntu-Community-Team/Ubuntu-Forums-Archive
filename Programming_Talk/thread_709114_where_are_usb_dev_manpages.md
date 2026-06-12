---
title: "where are usb dev manpages?"
date: 2008-02-27
forum: Programming Talk
---

### Post by Bart van Deenen on 2008-02-27
I'm playing with usb user space programming, and have some working code (mostly copied from [http://code.google.com/p/iosolution-libusb/]("http://code.google.com/p/iosolution-libusb/")).

What bugs me though, is that I can't find the usb library call man pages (like man usb_claim_interface or similar). I do have the regular development manpages installed

```
core:~$ sudo apt-get install manpages-dev manpages-posix libcorelinux-dev manpages-posix-dev libcorelinux-doc libcorelinux-examples
core:~$ man pthread_create             shows manpage
core:~$ man usb_claim_interface
No manual entry for usb_claim_interface

```

So where is the usb development documentation?

Thanks

Bart

---

### Post by supirman on 2008-02-27
I can't seem to find any man pages either, but if you go to the libusb web page, the (minimal) documentation is there.  See: [http://libusb.sourceforge.net/doc/](http://libusb.sourceforge.net/doc/)

Also, you can sudo apt-get install libusb-dev and it will install that same html documentation to your system at /usr/share/doc/libusb-dev/html

---

### Post by Bart van Deenen on 2008-02-27
Thanks, I've found them.

I didn't realize the calls were from libusb, I thought they were directly from the kernel. Well, at least I discovered the use of usbmon in the kernel Documentation directory. That's a nice plus of all this looking around:)

---

