---
title: "Compiling VICE with glxWaitVideoSyncSGI"
date: 2017-10-23
forum: Packaging and Compiling Programs
---

### Post by spaceforum on 2017-10-23
Greetings.  I'm trying to compile VICE, a Commodore emulator, with vsync enabled, on Ubuntu 17.04.  I can compile the package just fine, even with hardware scaling support, but it won't compile with vsync enabled.  When checking the configure output, it says the reason is because it can't find the glxWaitVideoSyncSGI() feature in libGL, or "-lGL" as the output says.  I have all the standard Mesa GL dev packages installed... as I said, I can even get the hardware scaling to work, which requires the GL dev packages... but for some reason the configure script says that feature isn't available.  I even tried it with both the Mesa libGL and the nVidia libGL (with a "make clean" in between) and got the same result.

Is this feature just not supported on Ubuntu, or is there some extra dev package that needs to be installed to make that feature available?  Thank you.

---

### Post by #&amp;thj^% on 2017-10-23
You have not said what you have done yet so this might be something to look at,
```
sudo apt-get  install build-essential  libvte-dev libasound2-dev libgtk2.0-dev libgnome2-dev
```
This is an old method used so some packages may be not be found...so show us the return form the terminal.

---

### Post by spaceforum on 2017-10-23
Of all those packages the only two that weren't installed were libvte-dev and libgnome2-dev, and the other packages associated with them, but it didn't seem to make a difference.

The configure command I'm using:

```
./configure --enable-gnomeui --disable-realdevice --disable-ipv6 --disable-ssi2001 --disable-catweasel --disable-hardsid --disable-parsid --disable-lame --with-uithreads --with-x --prefix=/usr
```

The relevant bit of the configure output:

```

checking for GTK... yeschecking for VTE... yes
checking for PANGO... yes
checking for CAIRO... yes
checking for GTKGL... yes
checking for GL/glx.h... yes
checking for glXWaitVideoSyncSGI in -lGL... no

```

```

SCREEN/UI
---------
Fullscreen support             : yes (--enable/disable-fullscreen)
Hardware scaling support       : yes
OpenGL sync support            : no 
Cairo rendering support        : yes
Pango support                  : yes
XF86 extensions support        : yes
MITSHM extensions support      : no 
XF86 VidMode extensions support: yes
XVideo support                 : no 
XRandR support                 : yes
Multithreaded UI support       : yes (--with/without-uithreads)
LibXpm support                 : no 
VTE support                    : yes (--enable/disable-vte)

```

---

