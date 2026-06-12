---
title: "GLFW Problem Installing"
date: 2007-02-04
forum: Programming Talk
---

### Post by OracleUK on 2007-02-04
Hi,

I am having trouble installing GLFW-2.5, when trying the "make x11" command I get the following error:

```
tim@tim-desktop:~/Games/glfw-2.5$ make x11
make[1]: Entering directory `/home/tim/Games/glfw-2.5/lib/x11'
gcc -c -I. -I..  -I/usr/X11R6/include -Os -Wall -o enable.o ../enable.c
In file included from ../internal.h:65,
                 from ../enable.c:36:
./platform.h:48:22: error: X11/Xlib.h: No such file or directory
./platform.h:49:24: error: X11/keysym.h: No such file or directory
./platform.h:50:23: error: X11/Xatom.h: No such file or directory
In file included from ./platform.h:51,
                 from ../internal.h:65,
                 from ../enable.c:36:
/usr/include/GL/glx.h:24:23: error: X11/Xutil.h: No such file or directory
/usr/include/GL/glx.h:25:21: error: X11/Xmd.h: No such file or directory
/usr/include/GL/glx.h:27:26: error: GL/glxtokens.h: No such file or directory
In file included from ./platform.h:51,
                 from ../internal.h:65,
                 from ../enable.c:36:
/usr/include/GL/glx.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXContextID’
/usr/include/GL/glx.h:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXPixmap’
/usr/include/GL/glx.h:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXDrawable’
/usr/include/GL/glx.h:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXPbuffer’
/usr/include/GL/glx.h:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXWindow’
/usr/include/GL/glx.h:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXFBConfigID’
/usr/include/GL/glx.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/GL/glx.h:70: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:73: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:76: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreateGLXPixmap’
/usr/include/GL/glx.h:79: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:81: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:83: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXGetCurrentDrawable’
/usr/include/GL/glx.h:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXIsDirect’
/usr/include/GL/glx.h:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXMakeCurrent’
/usr/include/GL/glx.h:95: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQueryExtension’
/usr/include/GL/glx.h:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQueryVersion’
/usr/include/GL/glx.h:99: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:101: error: expected ‘)’ before ‘font’
/usr/include/GL/glx.h:111: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:113: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:115: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/GL/glx.h:127: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:130: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreatePbuffer’
/usr/include/GL/glx.h:137: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreatePixmap’
/usr/include/GL/glx.h:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreateWindow’
/usr/include/GL/glx.h:143: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:145: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:147: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXGetCurrentReadDrawable’
/usr/include/GL/glx.h:151: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:154: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:156: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:159: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/GL/glx.h:161: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXMakeContextCurrent’
/usr/include/GL/glx.h:164: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:167: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:170: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:184: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:186: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXGetContextIDEXT’
/usr/include/GL/glx.h:188: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXGetCurrentDrawableEXT’
/usr/include/GL/glx.h:190: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:192: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:223: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXJoinSwapGroupNV’
/usr/include/GL/glx.h:226: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXBindSwapBarrierNV’
/usr/include/GL/glx.h:228: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQuerySwapGroupNV’
/usr/include/GL/glx.h:231: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQueryMaxSwapGroupsNV’
/usr/include/GL/glx.h:234: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQueryFrameCountNV’
/usr/include/GL/glx.h:236: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXResetFrameCountNV’
/usr/include/GL/glx.h:243: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:246: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:249: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:252: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:254: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:259: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:269: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:272: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:276: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreateGLXPixmapWithConfigSGIX’
/usr/include/GL/glx.h:280: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:286: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/GL/glx.h:289: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:295: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreateGLXPbufferSGIX’
/usr/include/GL/glx.h:300: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:302: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:305: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:308: error: expected ‘)’ before ‘*’ token
/usr/include/GL/glx.h:322: error: expected specifier-qualifier-list before ‘Bool’
In file included from ./platform.h:52,
                 from ../internal.h:65,
                 from ../enable.c:36:
./../../include/GL/glfw.h:168:21: error: GL/glu.h: No such file or directory
In file included from ../internal.h:65,
                 from ../enable.c:36:
./platform.h:202: error: expected specifier-qualifier-list before ‘Window’
./platform.h:269: error: expected specifier-qualifier-list before ‘Display’
./platform.h:406: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_glfwCreateNULLCursor’
./platform.h:413: error: expected ‘)’ before ‘keysym’
make[1]: *** [enable.o] Error 1
make[1]: Leaving directory `/home/tim/Games/glfw-2.5/lib/x11'
make: *** [x11] Error 2

```

---

### Post by blanky on 2007-02-05
Try executing the compile.sh script by doing **sh compile.sh** or just typing **make**, to me it looks like you're missing some libraries/headers from x11, which the script should tell you about. I downloaded GLFW and it worked fine for me. Let me know how it goes. Once it 'works', it should create libglfw.a inside /lib/x11 inside the glfw directory, you then should copy that to /lib. All of this information and more is found in the readme.html, which you should've read.

---

