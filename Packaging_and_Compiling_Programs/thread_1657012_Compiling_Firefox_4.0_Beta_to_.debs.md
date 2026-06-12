---
title: "Compiling Firefox 4.0 Beta to .debs"
date: 2010-12-31
forum: Packaging and Compiling Programs
---

### Post by beastrace91 on 2010-12-31
Everything goes smoothly during the packaging processor except for when I try to finally build the .deb files the builder fails out with a pile of errors along the lines of:

```
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/alsa/pcm.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/alsa/asoundlib.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/fusion/shm/pool.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/fusion/shm/shm_internal.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/fusion/shm/shm.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/IOKit/pwr_mgt/IOPMLib.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/Xft/Xft.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/extensions/Xcomposite.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/extensions/Xdamage.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/extensions/Xrender.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/extensions/XShm.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/extensions/XIElib.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/extensions/scrnsaver.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/extensions/shape.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/X11/extensions/Print.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/wx/xrc/xmlres.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers_js/sys/sparc/frame.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/Xft/Xft.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/extensions/Xcomposite.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/extensions/Xdamage.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/extensions/Xrender.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/extensions/XShm.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/extensions/XIElib.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/extensions/scrnsaver.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/extensions/shape.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/X11/extensions/Print.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/wx/xrc/xmlres.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/sys/sparc/frame.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/IOKit/pwr_mgt/IOPMLib.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/fusion/shm/pool.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/fusion/shm/shm_internal.h: Cannot open: Not a directory
tar: firefox-4.0b8/obj-i686-pc-linux-gnu/dist/system_wrappers/fusion/shm/shm.h: Cannot open: Not a directory
tar: Exiting with failure status due to previous errors
dpkg-source: error: tar --no-same-owner --no-same-permissions -xf - gave error exit status 2
dpkg-buildpackage: error: dpkg-source -b firefox-4.0b8 gave error exit status 29

```

What is wrong and how can I fix it?

~Jeff

---

### Post by SevenMachines on 2011-01-02
Hi. It looks like its trying to add header files that are part of other libraries used for the build, you shouldn't add these to the package. Are you using custom packaging or basing it on the ubuntu firefox beta packaging? I'd look at your debian/rules file. The headers mentioned shouldn't be included in the main firefox package anyway, by the looks of it they should all be covered by debian/control's build-deps.

---

