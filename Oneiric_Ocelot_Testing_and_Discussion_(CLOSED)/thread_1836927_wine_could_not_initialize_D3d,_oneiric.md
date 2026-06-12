---
title: "wine could not initialize D3d, oneiric"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-08-31
Hmmm, I've been playing DDO in wine for about 2 releases now, and it plays great.  In fact it still plays great in Natty, 

but.,.,
since oneiric it's not working.  i've even tried the xorg-edgers ppa and still no dice, although i do get a slightly different error.

```
err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory

err:wgl:has_opengl OpenGL support is disabled.

err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.

err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
```

kwin 3d effects works just fine.

```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 

```

---

### Post by rockorequin on 2011-09-03
I think it's because oneiric x86_64 has changed how it handles 32 bit libraries (the new 'multiarch' architecture) , and libGL has been removed from ia32-libs - see [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/821100](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/821100).

---

