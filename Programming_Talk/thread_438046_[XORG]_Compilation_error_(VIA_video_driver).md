---
title: "[XORG] Compilation error (VIA video driver)"
date: 2007-05-09
forum: Programming Talk
---

### Post by bLUEbYTE on 2007-05-09
Hello,
Since the default Xorg 7.2 drivers for my videocard(on-board via Uichrome) have severe problems,  I decided to try their official drivers source from their site.
I installed all the necessary -dev packages (xorg-dev xorg-server-dev, libdrm-dev etc...), and the [FONT="Courier New"]./configure[/FONT] doesn't complain. However, [FONT="Courier New"]make[/FONT] gives this error:
[FONT="Courier New"]
make  all-recursive
make[1]: Entering directory `/home/gokalp/via_drv'
Making all in src
make[2]: Entering directory `/home/gokalp/via_drv/src'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -I/usr/include/X11  -I/usr/include/X11/extensions -I.. -I.  -g -O2 -MT hw.lo -MD -MP -MF ".deps/hw.Tpo" -c -o hw.lo hw.c; \
        then mv -f ".deps/hw.Tpo" ".deps/hw.Plo"; else rm -f ".deps/hw.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -I/usr/include/X11 -I/usr/include/X11/extensions -I.. -I. -g -O2 -MT hw.lo -MD -MP -MF .deps/hw.Tpo -c hw.c  -fPIC -DPIC -o .libs/hw.o
In file included from /usr/include/xorg/sarea.h:40,
                 from via_driver.h:70,
                 from hw.c:32:
/usr/include/xf86drm.h:569: error: expected declaration specifiers or '...' before 'drm_drawable_info_type_t'
In file included from /usr/include/xf86drm.h:661,
                 from /usr/include/xorg/sarea.h:40,
                 from via_driver.h:70,
                 from hw.c:32:
/usr/include/xf86mm.h:106: error: expected specifier-qualifier-list before 'drm_bo_type_t'
/usr/include/xf86mm.h:128: error: expected specifier-qualifier-list before 'drm_bo_arg_t'
/usr/include/xf86mm.h:176: error: expected declaration specifiers or '...' before 'drm_bo_type_t'
make[2]: *** [hw.lo] Error 1
make[2]: Leaving directory `/home/gokalp/via_drv/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gokalp/via_drv'
make: *** [all] Error 2[/FONT]

Help please.

---

