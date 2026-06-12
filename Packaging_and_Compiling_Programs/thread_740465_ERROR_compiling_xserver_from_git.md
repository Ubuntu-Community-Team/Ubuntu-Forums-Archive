---
title: "ERROR compiling xserver from git"
date: 2008-03-30
forum: Packaging and Compiling Programs
---

### Post by WiNeOS on 2008-03-30
I'm trying to compile latest xserver and mesa from git, but build fails with the following compilation error :

```

 gcc -DHAVE_CONFIG_H -I. -I../../include -I../../hw/xfree86/os-support -I../../hw/xfree86/os-support/bus -I../../hw/xfree86/common -I../../hw/xfree86/dri -I../../hw/xfree86/dri2 -I../../mi -I/usr/src/vga/mesa/include -DHAVE_DIX_CONFIG_H -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -D_BSD_SOURCE -DHAS_FCHOWN -DHAS_STICKY_DIR_BIT -DDBUS_API_SUBJECT_TO_CHANGE -I/opt/gfx-test/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I../../include -I../../include -I../../Xext -I../../composite -I../../damageext -I../../xfixes -I../../Xi -I../../mi -I../../miext/shadow -I../../miext/damage -I../../render -I../../randr -I../../fb -I/opt/gfx-test/include -I/usr/local/include -I/usr/local/include/drm -I/usr/include/X11/dri -I/usr/src/vga/mesa/src/mesa/glapi -I/usr/src/vga/mesa/src/mesa/main -DXFree86Server -g -O2 -MT glcontextmodes.lo -MD -MP -MF .deps/glcontextmodes.Tpo -c glcontextmodes.c  -fPIC -DPIC -o .libs/glcontextmodes.o
glcontextmodes.c: In function '_gl_copy_visual_to_context_mode':
glcontextmodes.c:190: error: '__GLcontextModes' has no member named 'bindToTextureRgb'
glcontextmodes.c:191: error: '__GLcontextModes' has no member named 'bindToTextureRgba'
glcontextmodes.c:193: error: '__GLcontextModes' has no member named 'bindToMipmapTexture'
glcontextmodes.c:194: error: '__GLcontextModes' has no member named 'bindToTextureTargets'
glcontextmodes.c:197: error: '__GLcontextModes' has no member named 'yInverted'
glcontextmodes.c: In function '_gl_get_context_mode_data':
glcontextmodes.c:330: error: '__GLcontextModes' has no member named 'bindToTextureRgb'
glcontextmodes.c:333: error: '__GLcontextModes' has no member named 'bindToTextureRgba'
glcontextmodes.c:336: error: '__GLcontextModes' has no member named 'bindToMipmapTexture'
glcontextmodes.c:339: error: '__GLcontextModes' has no member named 'bindToTextureTargets'
glcontextmodes.c:342: error: '__GLcontextModes' has no member named 'yInverted'
glcontextmodes.c: In function '_gl_context_modes_create':
glcontextmodes.c:414: error: '__GLcontextModes' has no member named 'bindToTextureRgb'
glcontextmodes.c:415: error: '__GLcontextModes' has no member named 'bindToTextureRgba'
glcontextmodes.c:416: error: '__GLcontextModes' has no member named 'bindToMipmapTexture'
glcontextmodes.c:417: error: '__GLcontextModes' has no member named 'bindToTextureTargets'
glcontextmodes.c:418: error: '__GLcontextModes' has no member named 'yInverted'
glcontextmodes.c: In function '_gl_context_modes_are_same':
glcontextmodes.c:532: error: '__GLcontextModes' has no member named 'bindToTextureRgb'
glcontextmodes.c:532: error: '__GLcontextModes' has no member named 'bindToTextureRgb'
glcontextmodes.c:533: error: '__GLcontextModes' has no member named 'bindToTextureRgba'
glcontextmodes.c:533: error: '__GLcontextModes' has no member named 'bindToTextureRgba'
glcontextmodes.c:534: error: '__GLcontextModes' has no member named 'bindToMipmapTexture'
glcontextmodes.c:534: error: '__GLcontextModes' has no member named 'bindToMipmapTexture'
glcontextmodes.c:535: error: '__GLcontextModes' has no member named 'bindToTextureTargets'
glcontextmodes.c:535: error: '__GLcontextModes' has no member named 'bindToTextureTargets'
glcontextmodes.c:536: error: '__GLcontextModes' has no member named 'yInverted'
glcontextmodes.c:536: error: '__GLcontextModes' has no member named 'yInverted'
make[1]: *** [glcontextmodes.lo] Error 1
make[1]: se sale del directorio `/usr/src/vga/xorg/xserver/GL/glx'
make: *** [all-recursive] Error 1

```

It seems to be mesa related. I tried to add missing members in include/GL/internal/glcore.h with no luck... are there already.
Any advide?

---

### Post by redlaf on 2008-05-17
I have encountered exactly the same problem as yours.
I've managed to solve it just by using alsolute path to the mesa source, ie the option --with-mesa-source when running ./configure for the xserver
Hope it will help

---

### Post by WiNeOS on 2008-05-19
> **redlaf said:**
> I have encountered exactly the same problem as yours.
I've managed to solve it just by using alsolute path to the mesa source, ie the option --with-mesa-source when running ./configure for the xserver
Hope it will help

Yes, It worked.

Thanks redlaf

---

