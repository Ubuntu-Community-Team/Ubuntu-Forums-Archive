---
title: "Trouble building Ogre3D Engine and Devil (OpenIL)"
date: 2009-09-02
forum: Programming Talk
---

### Post by city-17 on 2009-09-02
Hi,

Has anyone built Ogre3D from source along with all dependencies successfully (in Ubuntu 9.04)?

I followed this excellent [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7845848#post7845848") but even though I can install Ogre successfully and run the demos, my configuration summary (that appears after ./configure) states that Ogre make is not using DEVIL.

Here take a look

```
--------=== Configuration summary ===--------
    Target platform                 : GLX
    OpenGL Ogre support             : GLX
    GUI library to use              : Xt
    Use double precision arithmetic : no
    Support for threading           : no
    Memory allocator                : ned
    Use STLport                     : no
    Use FreeType                    : yes
    Use FreeImage                   : yes
    Use DevIL                       : no
    Build OGRE demos                : yes
    Build CEGUI demos               : true
    Build the OpenEXR plugin        : no
    Build the Cg plugin             : yes
    Build the DirectX 9 plugin      : no
--------===============================--------
```

I can't figure out why is that given that I also built Devil from source succesfully. Also, I thought you needed Devil to build Ogre but apparently that is not the case.

Anyone having similar issues or any ideas?
Thanks.

---

### Post by caleb_yau on 2009-10-18
when you run ./configure look carefully and these lines should pop up

checking for FreeImage_Load in -lfreeimage... yes
configure: Freeimage is being built, disabling check for DevIL.

DevIL has been deprecated in favor of FreeImage, so devil won't be used if you have the better library :)

---

