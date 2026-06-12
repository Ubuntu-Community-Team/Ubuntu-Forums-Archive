---
title: "defining evironment variable LDFLAGS"
date: 2007-12-20
forum: Packaging and Compiling Programs
---

### Post by legatek on 2007-12-20
Hello helpful people!

I just received a new Samsung YP-T10 mp3 player and am trying to get it working in Feisty. Since is a Windows compatible MTP device, I have to install libmtp to recognize it. It is not recognized by the current build of libmtp, but the closely related YP-T9 is. I added a line in the appropriate source file to hopefully recognize the YP-T10 player and am now trying to compile it, and this is where I am running into difficulties. Running ./configure exits with the following error:

> configure: error: I can't find the libusb libraries on your system. You
        may need to set the LDFLAGS environment variable to include the
        search path where you have libusb installed before running
        configure (e.g. setenv LDFLAGS=-L/usr/local/lib)

I'm new at this, I have never altered source files before, so I don't know how to set the LDFLAGS variable. My usblib library is in /lib, but I don't know how to point LDFLAGS in this direction. setenv is not a recognized command in the Gnome terminal. 

Thanks for any help.

---

### Post by christhemonkey on 2007-12-20
If you are compiling you will need the library libusb*-dev*

```
sudo apt-get install libusb-dev
```

---

### Post by legatek on 2007-12-20
Thanks a lot, that did the trick. Now my system can recognize the device when I type "mtp-detect" into the terminal, but it's still not recognized by Gnomad2. I used the following thread to help me along:
[http://ubuntuforums.org/showthread.php?t=540577](http://ubuntuforums.org/showthread.php?t=540577)

However, this is no longer a packaging or compiling issue so I'll start a new thread in the appropriate place.

Thanks again.

---

