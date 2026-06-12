---
title: "emerald rebuilding package from source. compile fails. help needed"
date: 2011-10-31
forum: Packaging and Compiling Programs
---

### Post by deepclutch on 2011-10-31
I am rebuilding emerald theme from debian source(from a ppa). I've edited accordingly the files in debian/ directory particularly, adjusting the dependency "compiz-dev" to match the installed compiz-dev version(compiz-dev (>= 0.8.4) ) . I am totally clueless what I need to do now. I tried going to the debian/patches directory and tried patching the source! never worked!
the compile errors about some undeclared variables. Can anyone Help Me?

Now I tried building package after installing build dependencies. but, it errors as below:

```
make[3]: Leaving directory `/home/meow/emerald/emerald-0.8.8/libengine'
Making all in src
make[3]: Entering directory `/home/meow/emerald/emerald-0.8.8/src'
gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I../include -DLOCALEDIR="\"/usr/share/locale"\" -DENGINE_DIR=\"/usr/lib/emerald/engines\"    -march=native -O2 -pipe -pthread -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c main.c
main.c: In function 'decor_update_window_property':
main.c:508:8: warning: passing argument 5 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:508:8: warning: passing argument 6 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:508:8: error: too many arguments to function 'decor_quads_to_property'
/usr/include/compiz/decoration.h:176:1: note: declared here
main.c: In function 'decor_update_switcher_property':
main.c:1940:8: warning: passing argument 5 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:1940:8: warning: passing argument 6 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:1940:8: error: too many arguments to function 'decor_quads_to_property'
/usr/include/compiz/decoration.h:176:1: note: declared here
main.c: In function 'update_default_decorations':
main.c:2368:5: warning: passing argument 5 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:2368:5: warning: passing argument 6 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:2368:5: error: too many arguments to function 'decor_quads_to_property'
/usr/include/compiz/decoration.h:176:1: note: declared here
main.c:2427:5: warning: passing argument 5 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:2427:5: warning: passing argument 6 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:2427:5: error: too many arguments to function 'decor_quads_to_property'
/usr/include/compiz/decoration.h:176:1: note: declared here
main.c:2436:5: warning: passing argument 5 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:2436:5: warning: passing argument 6 of 'decor_quads_to_property' makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:176:1: note: expected 'int' but argument is of type 'struct decor_extents_t *'
main.c:2436:5: error: too many arguments to function 'decor_quads_to_property'
/usr/include/compiz/decoration.h:176:1: note: declared here
main.c: In function 'main':
main.c:5515:47: error: 'DECOR_INPUT_FRAME_ATOM_NAME' undeclared (first use in this function)
main.c:5515:47: note: each undeclared identifier is reported only once for each function it appears in
main.c:5621:12: error: 'WINDOW_DECORATION_TYPE_PIXMAP' undeclared (first use in this function)
main.c:5621:12: error: too many arguments to function 'decor_set_dm_check_hint'
[B]/usr/include/compiz/decoration.h:379:1: note: declared here
make[3]: *** [main.o] Error 1
make[3]: Leaving directory `/home/meow/emerald/emerald-0.8.8/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/meow/emerald/emerald-0.8.8'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/meow/emerald/emerald-0.8.8'
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2[/B]
 
```

I have emerald source debianized and it built successfully using dpkg-buildpackage. it compiles fine. but, only the version from ppa complains of weird errors.

---

### Post by SevenMachines on 2011-11-01
decor_quads_to_property is missing 2 decor_extents_t arguments which need to be added for compilation to succeed with newer version of compiz. You can add them yourself, it'll run, but you might want to check out emeralds git repository or something first.

---

### Post by deepclutch on 2011-11-01
Hi,
How to set those variables? and what are the values. 

TIA+

---

### Post by SevenMachines on 2011-11-01
In short, i dont know, without spending time going through the code. As a guess...
decor_quads_to_property used to require 2 decor_extents_t, input and maxinput, now it also needs frame_input and frame_max_input. Perhaps you can get away with mirroring the input and maxinput values, you'd need to go investigate libdecoration and its use further to know. Now method sig is

```
void
decor_quads_to_property (long    *data,
       Pixmap    pixmap,
       decor_extents_t *frame_input,
       decor_extents_t *input,
       decor_extents_t *frame_max_input,
       decor_extents_t *max_input,
       int     min_width,
       int     min_height,
       decor_quad_t    *quad,
       int     nQuad);
```So for instance, in main.cpp:507 we have
```
decor_quads_to_property(data, GDK_PIXMAP_XID(d->pixmap),
          &extents, &maxextents, 0, 0, quads, nQuad);
```So the following would possible work
 ```
decor_quads_to_property(data, GDK_PIXMAP_XID(d->pixmap),
          &extents, &extents, &maxextents, &maxextents, 0, 0, quads, nQuad);
```

---

### Post by deepclutch on 2011-11-04
Thanks for the tip. but, before that I tried copying a latest version(0.9-2) /usr/include/compiz/decoration.h from libdecoration0-dev(only this file extracted). it compiled fine and built packages albeit throwing up some warning messages.

Original /usr/include/compiz/decoration.h is ere(the version I've installed) : [http://paste.ubuntu.com/728637/](http://paste.ubuntu.com/728637/)
Here is the diff output comparing (1)original (2) new :
```
$ diff /home/meow/Desktop/decoration.h decoration.h 
46a47,55
> #define DECOR_INPUT_FRAME_ATOM_NAME             "_COMPIZ_WINDOW_DECOR_INPUT_FRAME"
> #define DECOR_OUTPUT_FRAME_ATOM_NAME            "_COMPIZ_WINDOW_DECOR_OUTPUT_FRAME"
> 
> #define DECOR_TYPE_ATOM_NAME                    "_COMPIZ_WINDOW_DECOR_TYPE"
> #define DECOR_TYPE_PIXMAP_ATOM_NAME             "_COMPIZ_WINDOW_DECOR_TYPE_PIXMAP"
> #define DECOR_TYPE_WINDOW_ATOM_NAME             "_COMPIZ_WINDOW_DECOR_TYPE_WINDOW"
> 
> #define WINDOW_DECORATION_TYPE_PIXMAP (1 << 0)
> #define WINDOW_DECORATION_TYPE_WINDOW (1 << 1)
168c177,178
< #define BASE_PROP_SIZE 12
---
> #define WINDOW_PROP_SIZE 12
> #define BASE_PROP_SIZE 21
177a188
>              decor_extents_t *frame_input,
178a190
>              decor_extents_t *frame_max_input,
184a197,203
> void
> decor_gen_window_property (long           *data,
>                decor_extents_t *input,
>                decor_extents_t *max_input,
>                int           min_width,
>                int           min_height);
> 
189,196c208,228
< decor_property_to_quads (long         *data,
<              int         size,
<              Pixmap         *pixmap,
<              decor_extents_t *input,
<              decor_extents_t *max_input,
<              int         *min_width,
<              int         *min_height,
<              decor_quad_t    *quad);
---
> decor_property_get_type (long *data);
> 
> int
> decor_pixmap_property_to_quads (long         *data,
>                 int         size,
>                 Pixmap         *pixmap,
>                 decor_extents_t  *frame_input,
>                 decor_extents_t  *input,
>                 decor_extents_t  *frame_max_input,
>                 decor_extents_t  *max_input,
>                 int         *min_width,
>                 int         *min_height,
>                 decor_quad_t    *quad);
> 
> int
> decor_window_property (long           *data,
>                int           size,
>                decor_extents_t *input,
>                decor_extents_t *max_input,
>                int           *min_width,
>                int           *min_height);
380c412,413
<              int     screen);
---
>              int     screen,
>       

```Here's the build log:
```
 dh_shlibdeps
dpkg-shlibdeps: warning: dependency on libfontconfig.so.1 could be  avoided if "debian/emerald/usr/bin/emerald-theme-manager  debian/emerald/usr/bin/emerald" were not uselessly linked against it  (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libatk-1.0.so.0 could be avoided  if "debian/emerald/usr/bin/emerald-theme-manager  debian/emerald/usr/bin/emerald" were not uselessly linked against it  (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on librt.so.1 could be avoided if  "debian/emerald/usr/bin/emerald-theme-manager  debian/emerald/usr/bin/emerald" were not uselessly linked against it  (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgio-2.0.so.0 could be avoided  if "debian/emerald/usr/bin/emerald-theme-manager  debian/emerald/usr/bin/emerald" were not uselessly linked against it  (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgmodule-2.0.so.0 could be  avoided if "debian/emerald/usr/bin/emerald-theme-manager  debian/emerald/usr/bin/emerald" were not uselessly linked against it  (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgthread-2.0.so.0 could be  avoided if "debian/emerald/usr/bin/emerald-theme-manager  debian/emerald/usr/bin/emerald" were not uselessly linked against it  (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libfreetype.so.6 could be avoided  if "debian/emerald/usr/bin/emerald-theme-manager  debian/emerald/usr/bin/emerald" were not uselessly linked against it  (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangoft2-1.0.so.0 could be  avoided if "debian/emerald/usr/bin/emerald-theme-manager  debian/emerald/usr/bin/emerald" were not uselessly linked against it  (they use none of its symbols).
dpkg-shlibdeps: warning: symbol dlopen used by  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 found in none  of the libraries.
dpkg-shlibdeps: warning: symbol dlclose used by  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 found in none  of the libraries.
dpkg-shlibdeps: warning: symbol dlerror used by  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 found in none  of the libraries.
dpkg-shlibdeps: warning: symbol dlsym used by  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 found in none  of the libraries.
dpkg-shlibdeps: warning: dependency on libdecoration.so.0 could be  avoided if  "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libXrender.so.1 could be avoided  if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libfontconfig.so.1 could be  avoided if  "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libatk-1.0.so.0 could be avoided  if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on librt.so.1 could be avoided if  "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpthread.so.0 could be avoided  if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgio-2.0.so.0 could be avoided  if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgmodule-2.0.so.0 could be  avoided if  "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libwnck-1.so.22 could be avoided  if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgthread-2.0.so.0 could be  avoided if  "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangocairo-1.0.so.0 could be  avoided if  "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libfreetype.so.6 could be avoided  if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangoft2-1.0.so.0 could be  avoided if  "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so  debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0  debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so  debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so  debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so  debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so  debian/libemeraldengine0/usr/lib/emerald/engines/libline.so  debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were  not uselessly linked against it (they use none of its symbols).
   dh_installdeb
   dh_gencontrol
dpkg-gencontrol: warning: Depends field of package libemeraldengine-dev: unknown substitution variable ${shlibs:Depends}
   dh_md5sums
   dh_builddeb
dpkg-deb: warning: 'debian/emerald/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `emerald' in `../emerald_0.8.8-0+sid1_amd64.deb'.
dpkg-deb: warning: 'debian/libemeraldengine0/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `libemeraldengine0' in `../libemeraldengine0_0.8.8-0+sid1_amd64.deb'.
dpkg-deb: warning: 'debian/libemeraldengine-dev/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `libemeraldengine-dev' in `../libemeraldengine-dev_0.8.8-0+sid1_amd64.deb'.
 dpkg-genchanges -b >../emerald_0.8.8-0+sid1_amd64.changes
dpkg-genchanges: binary-only upload - not including any source code
 dpkg-source --after-build emerald-0.8.8
dpkg-buildpackage: binary only upload (no source included      int     supports); 
```The Warning Messages more due to the failing of symlinking of known libraries. I guess? I haven't installed the packages as I know, dpkg will complain of symlinks not found.

---

### Post by SevenMachines on 2011-11-05
The type of change I mentioned before allows emerald to compile and run on the current oneiric version of libdecoration0, 0.9.6. Copying an older decoration.h header to somewhere to allow something to compile will likely come back to bite you, stick with headers and libraries of the same version, otherwise errors are likely to ensue somewhere along the line.
The dpkg-shlibdeps warnings are not unusual, sometimes there a sign of something that should be fixed, sometimes a sign of something that dpkg-shlibsdeps just can't an answer to. Theres a section in 
```
 $ man dpkg-shlibsdep 
```
that covers what all the warnings and errors mean.

---

### Post by deepclutch on 2011-11-05
Yes. it was an idiotic try, I did. the Compiz version in this system is: 0.8.4-4 , libdecoration0-dev: 0.8.4-5
obsolete versions?  since the current version reached 0.9.6 for both. 
I checked [http://paste.ubuntu.com/728637/](http://paste.ubuntu.com/728637/) (the version of /usr/include/compiz/decoration.h in the system) and it has "decor_quads_to_property" only once declared:
```

int
decor_version (void);

void
decor_quads_to_property (long            *data,
                         Pixmap          pixmap,
                         decor_extents_t *input,
                         decor_extents_t *max_input,
                         int             min_width,
                         int             min_height,
                         decor_quad_t    *quad,
                         int             nQuad);


```am confused if it'll work. since My understanding of Programming is almost Nil :( .

the distro carries this old version. I am trying to compile from git the latest available compiz at 0.9.5 as a better option.

---

### Post by SevenMachines on 2011-11-05
You shouldnt need to change emerald to use the version of emerald on the libdecoration0 version you're using. Judging from your versions are you using lucid? I'll install a virtual machine and see if I get the same problem

---

### Post by deepclutch on 2011-11-05
sorry that I haven't posted about the distro- I am trying this in My Debian Testing/unstable distro. 

while Oneric compiz/emerald works fine in Dell Laptop. the rebuilding scene came because of this problem.

---

### Post by SevenMachines on 2011-11-05
Building emerald 0.8.8 from 
[http://cgit.compiz.org/fusion/decorators/emerald/](http://cgit.compiz.org/fusion/decorators/emerald/)

On up to date debian sid gives me no problems. Did you accidently install newer libdecoration0-dev, patches or something? Maybe the ppa is a bit non-standard, see how you go with the 0.8.8 archive or an newer version from the git repository above

---

### Post by deepclutch on 2011-11-05
Yes. I've dropped the idea of messing with the old version compiz and emerald of ubuntu from source.
But, I have emerald engine working fine as I have already built successfully emerald debian packages from scratch. posted here because of curiousity why the ubuntu emerald sources fails to build. 
I have used [http://releases.compiz-fusion.org/components/emerald/emerald-0.8.8.tar.bz2](http://releases.compiz-fusion.org/components/emerald/emerald-0.8.8.tar.bz2)
for the build as I failed to find later versions.
```
apt-cache show emerald
Package: emerald
Status: install ok installed
Priority: extra
Section: x11
Installed-Size: 1801
Maintainer: Owner <meow@dcbox>
Architecture: amd64
Version: 0.8.8-1
Depends: compiz-plugins, libdecoration0 (>= 0.8.4), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.2.5), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.24.0), libgtk2.0-0 (>= 2.24.0), libpango1.0-0 (>= 1.14.0), libwnck22 (>= 2.30.0-3), libx11-6, libxrender1
Description: Decorator for compiz-fusion
 Emerald is a window decorator for the Compiz window manager, using a custom
 theme format (*.emerald). It is highly customizable and supports different
 theme engines, with transparency and precise placement of borders and window
 title elements.
 .
 This package provides a decorator for compiz-fusion and a themer application.
Homepage: http://releases.compiz-fusion.org/components/emerald
```> **SevenMachines said:**
> Building emerald 0.8.8 from 
[http://cgit.compiz.org/fusion/decorators/emerald/](http://cgit.compiz.org/fusion/decorators/emerald/)

On up to date debian sid gives me no problems. Did you accidently install newer libdecoration0-dev, patches or something? Maybe the ppa is a bit non-standard, see how you go with the 0.8.8 archive or an newer version from the git repository above
Yes. there is a problem. I am using Debian testing+Gnome 2.30.2 and not upgraded to Gnome-3 although, uses gdm3 and few gnome/gtk3 applications.

Now, the Compiz/libdecoration0 version default in Debian Testing is 0.8.4-4 .

Libdecoration0-dev is  0.8.4-5 as I inadvertently upgraded. but, compiz remains at  0.8.4-4. if I upgrade compiz to 0.8.4-5, it'll break dependencies.
```
    apt-cache policy compiz-core
compiz-core:
  Installed: 0.8.4-4
  Candidate: 0.8.4-4
  Version table:
     0.8.4-5 0
        300 http://ftp.debian.org/debian/ unstable/main amd64 Packages
 *** 0.8.4-4 0
        990 http://ftp.debian.org/debian/ testing/main amd64 Packages
        100 /var/lib/dpkg/status

:~$ apt-get -t unstable install compiz-core -s
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-settings-daemon : Breaks: gdm3 (< 3.0) but 2.30.5-11 is to be installed
 libglib2.0-0 : Breaks: gdm3 (< 3.0.3) but 2.30.5-11 is to be installed
E: Broken packages

:~$ apt-cache policy libdecoration0-dev 
libdecoration0-dev:
  Installed: 0.8.4-5
  Candidate: 0.8.4-5
  Version table:
 *** 0.8.4-5 0
        300 http://ftp.debian.org/debian/ unstable/main amd64 Packages
        100 /var/lib/dpkg/status
**     0.8.4-4 0**
        990 http://ftp.debian.org/debian/ testing/main amd64 Packages     
```Do You think if I downgrade libdecoration0 and headers(dev) to 0.8.4-4 so that it matches compiz version will work?

[COLOR=Red]**EDIT:**[/COLOR] I downgraded libdecoration0 to match compiz version, but the make failed with the same errors:
```
main.c: In function &#8216;main&#8217;:
main.c:5515:47: error: &#8216;DECOR_INPUT_FRAME_ATOM_NAME&#8217; undeclared (first use in this function)
main.c:5515:47: note: each undeclared identifier is reported only once for each function it appears in
main.c:5621:12: error: &#8216;WINDOW_DECORATION_TYPE_PIXMAP&#8217; undeclared (first use in this function)
main.c:5621:12: error: too many arguments to function &#8216;decor_set_dm_check_hint&#8217;
/usr/include/compiz/decoration.h:379:1: note: declared here
make[3]: *** [main.o] Error 1
make[3]: Leaving directory `/home/meow/emerald/emerald-0.8.8/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/meow/emerald/emerald-0.8.8'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/meow/emerald/emerald-0.8.8'
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
 
```Thanks for the Support.

---

### Post by SevenMachines on 2011-11-05
>  Do You think if I downgrade libdecoration0 and headers(dev) to 0.8.4-4 so that it matches compiz version will work?

Thanks for the Support.
Shouldnt cause the errors you originally got, the version in unstable is fine. My concern would be that you've got some other version of decoration.h somewhere, either somewhere in the /usr/local tree or have accidentally copied over the system version. try reinstalling

$ apt-get install --reinstall libdecoration0-dev
$ updatedb
$ locate decoration.h

Also, try compiling emerald from one of the archives in the link i gave previously and see if that works

---

### Post by deepclutch on 2011-11-05
> **SevenMachines said:**
> Shouldnt cause the errors you originally got, the version in unstable is fine. My concern would be that you've got some other version of decoration.h somewhere, either somewhere in the /usr/local tree or have accidentally copied over the system version. try reinstalling

$ apt-get install --reinstall libdecoration0-dev
$ updatedb
$ locate decoration.h

Also, try compiling emerald from one of the archives in the link i gave previously and see if that works
I am sure I have reverted decoration.h as well as reinstalled just now. it is not the problem, I guess.
Here is the source where where I got the emerald source which is failing to compile:

[https://launchpad.net/ubuntu/+source/emerald/0.8.8-0ubuntu1](https://launchpad.net/ubuntu/+source/emerald/0.8.8-0ubuntu1)

Otherwise, I can compile fine from Vanilla Emerald sources. No Issues. 
Why I chose Ubuntu sources is as You know, rebuilding from Debian Source is hassle free(supposedly). but, this source has some Ubuntu specific fixes or what. :confused: from the debian/ directory it feels so.

a futile exercise, I guess, if that source package is tuned for compiz version much differ from the compiz version in Debian?

---

### Post by SevenMachines on 2011-11-05
Ah, I see. Yes, the ubuntu ppa contains a patch to adjust for the newer compiz version ubuntu uses called 06_adjust_to_new_compiz.patch. Just comment this patch out in debian/patches/series

Unfortunately, at least here, the package seems to have this patch accidently pre-applied to the source :( so you might need to test for this and unpatch if needed

```
$ grep -r DECOR_INPUT_FRAME_ATOM_NAME *

debian/patches/06_adjust_to_new_compiz.patch:+    frame_window_atom = XInternAtom(xdisplay, DECOR_INPUT_FRAME_ATOM_NAME, FALSE);

src/main.c:    frame_window_atom = XInternAtom(xdisplay, DECOR_INPUT_FRAME_ATOM_NAME, FALSE);
```# Shouldnt be in main.c, patch is pre-applied to the source, doh... so
```
$ patch -p1 -R < debian/patches/06_adjust_to_new_compiz.patch 
patching file src/main.c

$ grep -r DECOR_INPUT_FRAME_ATOM_NAME *
debian/patches/06_adjust_to_new_compiz.patch:+    frame_window_atom = XInternAtom(xdisplay, DECOR_INPUT_FRAME_ATOM_NAME, FALSE);
```You should find the ppa version will now build on debian testing/unstable

---

### Post by deepclutch on 2011-11-05
Thank You.  Will Check and reply. 

Sorry for being unclear from start itself. I would've posted the emerald ppa details earlier itself.

---

### Post by SevenMachines on 2011-11-05
My fault for skim reading :)

---

### Post by deepclutch on 2011-11-05
Yup. it compiles and builds package. yet, some warning messages as I got while testing with replacement "decoration.h"(note that I've reinstalled/reversed everything to intact).
for eg:
```

dpkg-shlibdeps: warning: dependency on libfontconfig.so.1 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols). dpkg-shlibdeps: warning: dependency on libatk-1.0.so.0 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols). 
```

dpkg-deb warnings are because I casually just ran "dpkg-source --commit" 
```
ake[1]: Leaving directory `/home/meow/emerald/emerald-0.8.8'
   dh_install
   dh_installdocs
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_pysupport
dh_pysupport: This program is deprecated, you should use dh_python2 instead. Migration guide: http://deb.li/dhs2p
   dh_installinit
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_installgsettings
   dh_bugfiles
   dh_ucf
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_usrlocal
   dh_link
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
   dh_shlibdeps
dpkg-shlibdeps: warning: dependency on libfontconfig.so.1 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libatk-1.0.so.0 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on librt.so.1 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgio-2.0.so.0 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgmodule-2.0.so.0 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgthread-2.0.so.0 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libfreetype.so.6 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangoft2-1.0.so.0 could be avoided if "debian/emerald/usr/bin/emerald-theme-manager debian/emerald/usr/bin/emerald" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: symbol dlopen used by debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlclose used by debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlerror used by debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlsym used by debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: dependency on libdecoration.so.0 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libXrender.so.1 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libfontconfig.so.1 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libatk-1.0.so.0 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on librt.so.1 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpthread.so.0 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgio-2.0.so.0 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgmodule-2.0.so.0 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libwnck-1.so.22 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgthread-2.0.so.0 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangocairo-1.0.so.0 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libfreetype.so.6 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangoft2-1.0.so.0 could be avoided if "debian/libemeraldengine0/usr/lib/emerald/engines/liboxygen.so debian/libemeraldengine0/usr/lib/libemeraldengine.so.0.0.0 debian/libemeraldengine0/usr/lib/emerald/engines/libpixmap.so debian/libemeraldengine0/usr/lib/emerald/engines/liblegacy.so debian/libemeraldengine0/usr/lib/emerald/engines/libvrunner.so debian/libemeraldengine0/usr/lib/emerald/engines/libzootreeves.so debian/libemeraldengine0/usr/lib/emerald/engines/libline.so debian/libemeraldengine0/usr/lib/emerald/engines/libtruglass.so" were not uselessly linked against it (they use none of its symbols).
   dh_installdeb
   dh_gencontrol
dpkg-gencontrol: warning: Depends field of package libemeraldengine-dev: unknown substitution variable ${shlibs:Depends}
   dh_md5sums
   dh_builddeb
dpkg-deb: warning: 'debian/emerald/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `emerald' in `../emerald_0.8.8-0ubuntu1_amd64.deb'.
dpkg-deb: warning: 'debian/libemeraldengine0/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `libemeraldengine0' in `../libemeraldengine0_0.8.8-0ubuntu1_amd64.deb'.
dpkg-deb: warning: 'debian/libemeraldengine-dev/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `libemeraldengine-dev' in `../libemeraldengine-dev_0.8.8-0ubuntu1_amd64.deb'.
 dpkg-genchanges  >../emerald_0.8.8-0ubuntu1_amd64.changes
dpkg-genchanges: including full source code in upload
 dpkg-source --after-build emerald-0.8.8
dpkg-buildpackage: full upload (original source is included)

```So, This stands Resolved. :)

---

### Post by SevenMachines on 2011-11-05
Some of the 'needlessly linked against' errors are due to the use of pkg-config I believe. pkg-config generates a lot of linking, see 
$ pkg-config --libs gtk+-2.0
for example
Therefore you can end up linking against a lot of libraries that are not used, you just have to kind of ignore it just now, it's an issue that goes quite deeply into a lot of packages. Theres probably a good explanation about it somewhere!

---

