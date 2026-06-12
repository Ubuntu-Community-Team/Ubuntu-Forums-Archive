---
title: "libEGL warning: DRI2: failed to authenticate"
date: 2011-12-12
forum: Programming Talk
---

### Post by t1497f35 on 2011-12-12
Hi,
The warning/error from the title gets printed when calling eglInitialize(...), does anyone know what it means or how to fix it?

```

Display *xDisplay = XOpenDisplay(getenv("DISPLAY"));
EGLDisplay eglDisplay = eglGetDisplay(xDisplay);
if (!eglDisplay) {
    printf("Error: eglGetDisplay() failed\n");
    return;
}

EGLint egl_major, egl_minor;
if(!eglInitialize(eglDisplay, &egl_major, &egl_minor)) {//THIS LINE GENERATES THE ERROR/WARNING
      printf("Error: eglInitialize() failed\n");
      return;
}

```Running on: Ubuntu 11.10 amd64, Nvidia GTX 560Ti, both the Nvidia binary driver & libgles2-mesa-dev are installed.

---

### Post by SchighSchagh on 2012-07-03
*bump*

Pretty much same problem here. Slightly different system:
Ubuntu 12.04 x64, GeForce GTX 260. NVidia drivers and libgles2-mesa-dev installed.

---

### Post by cedeon on 2012-08-15
I believe that DRI2 is not implemented in the proprietary Nvidia Drivers.  Source: [http://www.chaosreigns.com/wayland/hardware/](http://www.chaosreigns.com/wayland/hardware/)

You might have to switch over to the Nouveau drivers

---

