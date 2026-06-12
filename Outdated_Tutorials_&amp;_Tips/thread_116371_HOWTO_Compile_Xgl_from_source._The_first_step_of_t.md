---
title: "HOWTO: Compile Xgl from source. The first step of the Future of the Linux Desktop."
date: 2006-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Azriphale on 2006-01-12
HOWTO (incomplete): Compile Xgl from the freedesktop.org CVS to run with your current Xorg libraries.

This is my first ever howto, so any feedback will be welcome.

This was not done on a clean Ubuntu install. I am busy installing Ubuntu Breezy in VMWare to set it all up there, then I should have all the deps listed here.

------------------------

First, in order to build xserver, you are going to need the following dependencies:

```

build-essential
m4
autoconf
automake-1.9
autotools-dev
libtool

libx11-dev
libxau-dev
libxext-dev
libxi-dev

libxfont1


x11proto-core-dev
x11proto-input-dev
x11proto-kb-dev
x11proto-xext-dev
x11proto-randr-dev
x11proto-render-dev
x11proto-fixes-dev
x11proto-damage-dev
x11proto-fonts-dev
x11proto-composite-dev
x11proto-resource-dev
x11proto-record-dev

x11proto-bigreqs-dev
x11proto-xcmisc-dev
x11proto-video-dev
x11proto-scrnsaver-dev

x11proto-gl-dev
x11proto-trap-dev
x11proto-xinerama-dev

libxfont-dev
xtrans-dev


libxrandr-dev
libxrender-dev
libxfixes-dev
libxdamage-dev
libxext-dev
libxres-dev

libxdmcp-dev

libfreetype6-dev
zlib1g-dev

libgl1-mesa-dev

```

I am not sure if this list is complete, or if there are unrequired deps on there. As I said, I am not currently on a clean system, but I am bust setting one up. I'll update the list as soon as I can.

You should be able to install all of this by running the command
```

sudo apt-get install build-essential m4 autoconf automake-1.9 autotools-dev libtool libx11-dev libxau-dev libxext-dev libxi-dev libxfont1 x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-randr-dev x11proto-render-dev x11proto-fixes-dev x11proto-damage-dev x11proto-fonts-dev x11proto-composite-dev x11proto-resource-dev x11proto-record-dev x11proto-bigreqs-dev x11proto-xcmisc-dev x11proto-video-dev x11proto-scrnsaver-dev x11proto-gl-dev x11proto-trap-dev x11proto-xinerama-dev libxfont-dev xtrans-dev libxrandr-dev libxrender-dev libxfixes-dev libxdamage-dev libxext-dev libxres-dev libxdmcp-dev libfreetype6-dev zlib1g-dev libgl1-mesa-dev

```

If you require deps not listed there, post the error here and I will tell you what to get. Or, if you know what you need, just post the dep here.

The next requirement is a package called glitz. The version in the breezy repos is too old, so we need to fetch the CVS source from freedesktop.org and build that:

```

$ cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/cairo co glitz glitzinfo
$ cd glitz
$ ./autogen.sh
$ make
$ sudo make install
$ cd ../glitzinfo
$ make -f Makefile.glx
$ ./glitzinfo
$ cd ..

```

Run glitzinfo. Its not required by anything, but it gives you info on available features:
> 
glitzinfo should report some info about available features, drawable formats and surface formats. The following set of features are important and if one of them is missing it is likely that it will give you performance problems.

```

texture rectangle
texture border clamp
multitexture
texture environment combine

```


Now we can start with the actual xserver package that provides Xgl. Again we fetch the source from freedesktop.org CVS:

```

$ cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xserver co xserver
$ cd xserver
$ ./autogen.sh --enable-xglserver --enable-xglxserver
$ make

```

**NOTE: There is no "sudo make install" because if you install this, it will most probably break the xserver from the breezy repos, stopping your normal X from running.**

You can give autogen.sh the "--prefix=/some/path" flag, which will make the "sudo make install" command install it to the location "/some/path". I have **not** done this on my machine. If you try this, make sure that the path does not conflict with installed software (i.e. try "/opt/xglserver")

If it built without any problems, there will be a binary called "Xglx" in the "hw/xgl/glx" subdirectory of xserver. Go to that directory and run Xglx with the following command:

```

$ cd hw/xgl/glx
$ ./Xglx :1 -ac -nolisten tcp -screen 1024x768

```

The "-ac" flag disables access control (otherwise clients will not be able to connect to the Xglx server at all because the access control is normally set up by scripts such as startx). The "-nolisten tcp" flag offsets this security hazard by not allowing remote connections. 

To change the resolution the Xglx server runs at, simply change the "1024x768" after "-screen" to your required resolution.

I don't think I have hardware acceleration correctly enabled. When I try the autogen.sh flag "--enable-glx" (which I did not include above), I get an error when I compile, saying that the file "glcore.h" cannot be found, and I have not managed to fix that yet. If anybody can help, it will be greatly appreciated by everybody, I'm sure.

You can then start up a gnome desktop (or something) in there like so

```

$ export DISPLAY=:1
$ nautilus &
$ metacity &
$ xcompmgr &
$ transset &
$ gnome-panel &
$ gnome-settings-daemon &

```

I am not sure the xcompmgr plays nicely with Xglx, and I have not managed to compile glxcompmgr yet (I get the same cannot find "glcore.h" error when compiling).

In theory you now have Xglx running in a window.

I hope at least somebody finds this guide useful...
Please let me know what I can improve.

ADDED:
I have just finished setting up the clean system. Now to start getting everything....

ADDED:
I have updated the dependecy list for building --enable-xglserver
I have not got a list of all the deps for building --enable-xglxserver (I have only been able to do that on a non-clean system (owing to the fact that my clean system is a virtual machine without a 3d-card)

I have corrected a few negligent and inexcusable errors in my original post

---

### Post by Rob2687 on 2006-01-27
Nice but it doesn't compile Xglx.

If I try 
 ./autogen.sh --enable-xglxserver --enable-xglserver
it still gives me the same errors described in the other thread.
```
make[4]: Entering directory `/home/robert/xserver/hw/xgl/glx'
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../hw/xgl/glx  -I../../../hw/xgl  -I../../../miext/damage -I../../../miext/shadow -I../../../Xext -I../../../record -I../../../render -I../../../randr -I../../../xfixes -I../../../damageext -I../../../composite                 -I../../../fb -I../../../mi -Wall -Wpointer-arith -Wstrict-prototypes   -Wmissing-prototypes -Wmissing-declarations        -Wnested-externs -fno-strict-aliasing -D_BSD_SOURCE -DHAS_FCHOWN -DHAS_STICKY_DIR_BIT -I/usr/include/freetype2   -D_BSD_SOURCE -I../../../include -I../../../Xext -I/usr/local/include -I/usr/local/include -I/usr/X11R6/include      -O2 -march=pentium3m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions -MT xglx.lo -MD -MP -MF ".deps/xglx.Tpo" -c -o xglx.lo xglx.c; \
then mv -f ".deps/xglx.Tpo" ".deps/xglx.Plo"; else rm -f ".deps/xglx.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../hw/xgl/glx -I../../../hw/xgl -I../../../miext/damage -I../../../miext/shadow -I../../../Xext -I../../../record -I../../../render -I../../../randr -I../../../xfixes -I../../../damageext -I../../../composite -I../../../fb -I../../../mi -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -D_BSD_SOURCE -DHAS_FCHOWN -DHAS_STICKY_DIR_BIT -I/usr/include/freetype2 -D_BSD_SOURCE -I../../../include -I../../../Xext -I/usr/local/include -I/usr/local/include -I/usr/X11R6/include -O2 -march=pentium3m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions -MT xglx.lo -MD -MP -MF .deps/xglx.Tpo -c xglx.c  -fPIC -DPIC -o .libs/xglx.o
In file included from ../../../include/dixfont.h:33,
                 from ../../../mi/mi.h:57,
                 from ../../../hw/xgl/xgl.h:43,
                 from xglx.h:29,
                 from xglx.c:26:
/usr/X11R6/include/X11/fonts/fontstruct.h:293:23: error: fontproto.h: No such file or directory
make[4]: *** [xglx.lo] Error 1
make[4]: Leaving directory `/home/robert/xserver/hw/xgl/glx'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/robert/xserver/hw/xgl/glx'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/robert/xserver/hw/xgl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/robert/xserver/hw'
make: *** [all-recursive] Error 1

```

---

### Post by kaamos on 2006-01-27
This looks **very** nice! Got to try this soon.. Thanks for the howto!

---

### Post by One Quick Question on 2006-01-28
```
$ cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/cairo glitz glitzinfo
```
should be
```
$ cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/cairo co glitz glitzinfo
```

"Run glitzinfo."
There doesn't seem to be a glitzinfo executable!

```
$ ./glitzinfo
./glitzinfo: symbol lookup error: ./glitzinfo: undefined symbol: glitz_glx_find_window_format
```
Is that normal output?

And finally, the xserver make compiles without errors, but I don't get any Xglx executable in hw/xgl/glx!
:-\

I'll start checking it out myself, but just to let you know, there deffinitely is some things missing so far!

---

### Post by One Quick Question on 2006-01-28
> I don't think I have hardware acceleration correctly enabled. When I try the autogen.sh flag "--enable-glx" (which I did not include above), I get an error when I compile, saying that the file "glcore.h" cannot be found, and I have not managed to fix that yet. If anybody can help, it will be greatly appreciated by everybody, I'm sure.

I also did *--enable-xglserver --enable-xglxserver --enable-glx --enable-xkb*.

glcore.h, as well as some other missing includes that it will later complain about, can be found in the *mesa-swrast-source* package, which you then will need to link to the xserver source.  
(note: don't bother following this code)
```
$ sudo apt-get mesa-swrast-source
$ ln -s /usr/share/mesa-source/include/GL ~/src/xserver/GL/glx/GL
```
(where ~/src is where ever you're stashing this stuff)
It will then complain about a missing glapitable.h, so what I did was 
```
$ ln -s /usr/share/mesa-source/src/mesa/glapi/glapitable.h ~/src/xserver/GL/glx/glapitable.h
```
But after that it exploded in no less than 815 errors saying the *error: field 'whatever' declared as a function*

So...

I'm still not sure how this xglx server is supposed to compile.


EDIT: At the end of the errors, it also says 
**** [libglx_la-g_render.lo] Error 1*
which to me looks alot like "lol Error 1"
:mad:  It's laughing at me.

---

### Post by zasf on 2006-01-28
[QUOTE=Azriphale] [..]
In theory you now have Xglx running in a window.

I hope at least somebody finds this guide useful...
Please let me know what I can improve.

ADDED:
I have just finished setting up the clean system. Now to start getting everything....[/QUOTE]

Hey, this subject is soo cool!

I tried myself but I get errors, some of them I got rid installing other packages

[LIST]
[*]automake, otherwise it complains about aclocal wich is not present when compiling glitz
[*]libtool otherwise it says "./autogen.sh: line 40: libtoolize: command not found"
[/LIST]

but still I can't even compile glitz

```
matteo@ubuntu:~/download/xgl/glitz$ ./autogen.sh
./autogen.sh:   Note: `./configure' will be run with no arguments.
                If you wish to pass any to it, please specify them on the
                `./autogen.sh' command line.

./autogen.sh: running `libtoolize --copy --force'
Putting files in AC_CONFIG_AUX_DIR, `config'.
./autogen.sh: running `aclocal'
./autogen.sh: running `autoheader'
./autogen.sh: running `automake --add-missing'
automake: src/glx/Makefile.am: warning: automake does not support libglitz_glx_la_LDFLAGS being defined conditionally
automake: src/agl/Makefile.am: warning: automake does not support libglitz_agl_la_LDFLAGS being defined conditionally
automake: src/egl/Makefile.am: warning: automake does not support libglitz_egl_la_LDFLAGS being defined conditionally
automake: src/wgl/Makefile.am: warning: automake does not support libglitz_wgl_la_LDFLAGS being defined conditionally
```

When will you update this howto?

Thanks!

---

### Post by zasf on 2006-01-28
ok, in some way I got xserver to be compiled

```
PKG_CONFIG_PATH=/opt/fdo/lib/pkgconfig/ ./autogen.sh --prefix=/opt/fdo --enable-composite --enable-xglserver

[...]

Xgl will be compiled with the following ddx modules:
  xglx: yes
  xegl: no

the following stand-alone servers:
  Xglx: no
  Xegl: no

and the following extension modules:
  glx: no
```

but then I have no Xglx command.. what am i missing?

---

### Post by yanns on 2006-01-28
@ zasf: how did you get rid of the automake warnings?

---

### Post by Rob2687 on 2006-01-28
[QUOTE=zasf]ok, in some way I got xserver to be compiled

...

but then I have no Xglx command.. what am i missing?[/QUOTE]

Did you run 'make' after doing autogen?

---

### Post by One Quick Question on 2006-01-28
Hey!  I got it to compile! ```
/autogen.sh --enable-composite --enable-xglxserver --prefix=/opt/xglxserver
```
and then suid-ing the relevent executables.
It behaves pretty hairy, but I haven't played around with much or fixed up the other options to enable; I'll be doing that for the next few hours.  
But it DOES compile!  Woohoo!

---

### Post by Rob2687 on 2006-01-28
Yeah, so I finally got it to compile.
I had to symlink fontproto.h to fix my previous problem and install Xfont from cvs.

---

### Post by Iandefor on 2006-01-28
interesting. I've got some issues compiling xgl. Here's the error it returns when I run  "./autogen.sh --enable-glserver --enable-glxserver": ```
checking for XSERVER... configure: error: Package requirements (randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the XSERVER_CFLAGS and XSERVER_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

---

### Post by dabear on 2006-01-28
Ok.. I would reallt like some more info what Xgl is, and maybe some screenshots?

---

### Post by Rob2687 on 2006-01-28
look through this thread near the end.
[http://ubuntuforums.org/showthread.php?t=75527&page=40&highlight=xgl](http://ubuntuforums.org/showthread.php?t=75527&page=40&highlight=xgl)

---

### Post by RaptorRaider on 2006-01-28
I don't see a satisfying answer to that question there.

And while I "know" what Xgl is, I too am not sure what to expect and would like to know a bit more about stability beside, like dabear requested, a few clarifying screenshots.

---

### Post by Rob2687 on 2006-01-28
It's requires xorg 7.0 anyways...so yeah. THis really shouldn't be in 5.10 Howtos. 

[http://www.linuxedge.org/index.php?q=node/39](http://www.linuxedge.org/index.php?q=node/39)

---

### Post by One Quick Question on 2006-01-28
Xglx is an X server that renders everything through hardware.
So far I've been able to compile in the composite extension, but the mesa libraries are very confusing to me and I can't actually compile in the glx extensions. 

Meaning what I've made is that it acts the same as the normal X server but with the composite extension built-in (which I've not found any stability issues with as long as I don't use kompmgr)

For you guys who want to still tamper with it and are getting dependency errors, what I did was installed kpackage and apt-file and searched the repo for the individual files that I needed.

But yeah, it's just as well to wait 2 1/2 months and install this madness when Dapper is finished.

---

### Post by Rob2687 on 2006-01-28
For GLX  use --with-mesa-source=/home/user/Mesa

Point that to the Mesa CVS. Still get errors with the make process though.
> /home/robert/Mesa/src/mesa/main/state.c: In function '_mesa_init_exec_table':
/home/robert/Mesa/src/mesa/main/state.c:787: error: 'struct _glapi_table' has no member named 'GetQueryObjecti64vEXT'
/home/robert/Mesa/src/mesa/main/state.c:788: error: 'struct _glapi_table' has no member named 'GetQueryObjectui64vEXT'
make[2]: *** [libglcore_la-state.lo] Error 1
make[2]: Leaving directory `/home/robert/xserver/GL/mesa'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/robert/xserver/GL'
make: *** [all-recursive] Error 1


---

### Post by vnbuddy2002 on 2006-01-29
Try to compile without --enable-glx

it should not complain about missing GL core. but for me, I compiled I ran it. However, I don't see any acceleration. It seems much slower instead.I could barely play any movie.

My Desktop is:
AMD64 3800+ X2 ( overlocked to 2.34ghz )
Nvidia Geforce4 6600
1 GIG Mem
400 Gigz Harddrive.

---

### Post by zasf on 2006-01-29
[QUOTE=yanns]@ zasf: how did you get rid of the automake warnings?[/QUOTE]

I compiled and installed automake from source since you need a newer version than the one from repos

[QUOTE=http://www.freedesktop.org/wiki/Software_2fXserver_2fInstallGuide]Before You Build
[list]
[*] autoconf --version must report 2.59 or later
[*] automake --version must report 1.7.x
[*] libtool --version must report 1.5 (available from [http://ftp.gnu.org/gnu/libtool/](http://ftp.gnu.org/gnu/libtool/) if your distribution doesn't have it)
[*] pkg-config --version must report 0.9.0 or later
[/list]
[/QUOTE]

I installed 1.9.1, please ask if this wasn't enough.

---

### Post by zasf on 2006-01-29
[QUOTE=Rob2687]Did you run 'make' after doing autogen?[/QUOTE]

yes :), but I don't have Xglx executable.. maybe I need to specify --enablexglx in autogen.sh? Did you guys also followed this [script]("http://www.freedesktop.org/wiki/XserverBuildScript")?

---

### Post by vnbuddy2002 on 2006-01-29
I use 

./autogen.sh --enable-xglserver --enable-xglxserver --prefix=/path/to/somewhere

Once it is finished, Xglx should be in /path/to/somewhere/bin

---

### Post by zasf on 2006-01-29
[QUOTE=vnbuddy2002]I use 

./autogen.sh --enable-xglserver --enable-xglxserver --prefix=/path/to/somewhere

Once it is finished, Xglx should be in /path/to/somewhere/bin[/QUOTE]

ok I got it to work, I still don't understand the difference between Xgl and Xglx, anyway I have Xglx in /hw/xgl/glx, since I made no 'sudo make install' as suggested.. did you? I need to reboot and then I can take a screenshot!

---

### Post by vnbuddy2002 on 2006-01-29
:).. I have no clue about the differences. but it seems like it is not doing any hardware acceleration. I've read somewhere that we need Xorg 7.0 because it supports moduling. 

[http://www.linuxedge.org/index.php?q=node/39](http://www.linuxedge.org/index.php?q=node/39)

I want to my desktop like that.. but it seems like I have to wait.. Compile X0rg  from scratch is the pain in the a**. :)

---

### Post by zasf on 2006-01-29
here you go:

[LIST]
[*] This shows the use of xcompmgr for shadows
[[IMG]http://ubuntuforums.org/gallery/files/5/7/5/0/6/xgl1_thumb.png[/IMG]]("http://ubuntuforums.org/gallery/files/5/7/5/0/6/xgl1_original.png")
[*] This shows the use of transset
[[IMG]http://ubuntuforums.org/gallery/files/5/7/5/0/6/xgl2_thumb.png[/IMG]]("http://ubuntuforums.org/gallery/files/5/7/5/0/6/xgl2_original.png")
[/LIST]

what I would like to do now is:

[LIST]
[*]enable GLX extensions, they work in my normal configuration, what should I do to let them work in xgl?
[*]set a 2nd grub configuration to load xgl as primary display at boot
[/LIST]

how you do this?

---

### Post by vnbuddy2002 on 2006-01-29
Try to play a movie and see if the movie is playable. I tested mine.. but the video is not playable. It seems very slow.

without xgl, it is very fast, with xgl, the system is around ~50% load each time I move a window.. 

:) I am not sure what I did wrong!

---

### Post by benplaut on 2006-01-31
what the *hell* do you think you're doing making this HOWTO without screenshots?!

---

### Post by Azriphale on 2006-01-31
Sorry about this... I have been away for the past five days without a computer or internet connection. I will get to answering everybody as soon as I possibly can.

---

### Post by zasf on 2006-02-04
I freshly installed dapper.. but I'm stuck at the first step: glitz does't want to compile, when I issue 'make' I get

```

[cut]
In file included from glitz_glx_drawable.c:30:
glitz_glxint.h:34:19: error: GL/gl.h: No such file or directory
glitz_glxint.h:35:20: error: GL/glx.h: No such file or directory
In file included from glitz_glxint.h:37,
                 from glitz_glx_drawable.c:30:
glitz_glxext.h:110: error: syntax error before 'GLXDrawable'
glitz_glxext.h:111: warning: function declaration isn't a prototype
glitz_glxext.h:113: error: syntax error before 'GLXDrawable'
glitz_glxext.h:113: warning: function declaration isn't a prototype
glitz_glxext.h:114: error: syntax error before '*' token
glitz_glxext.h:116: error: syntax error before 'GLXContext'
glitz_glxext.h:116: warning: type defaults to 'int' in declaration of 'GLXContext'
glitz_glxext.h:116: warning: function declaration isn't a prototype
glitz_glxext.h:116: error: 'GLXContext' declared as function returning a function
glitz_glxext.h:116: warning: function declaration isn't a prototype
In file included from glitz_glx_drawable.c:30:
glitz_glxint.h:60: error: syntax error before 'glitz_glx_create_new_context_t'
glitz_glxint.h:60: warning: no semicolon at end of struct or union
glitz_glxint.h:61: warning: type defaults to 'int' in declaration of 'glitz_glx_static_proc_address_list_t'
glitz_glxint.h:61: warning: data definition has no type or storage class
glitz_glxint.h:86: error: field 'context' declared as a function
glitz_glxint.h:103: error: field 'root_context' declared as a function
glitz_glxint.h:106: error: syntax error before 'glitz_glx_static_proc_address_list_t'
glitz_glxint.h:106: warning: no semicolon at end of struct or union
glitz_glxint.h:108: error: syntax error before '}' token
glitz_glxint.h:115: error: syntax error before 'GLXDrawable'
glitz_glxint.h:115: warning: no semicolon at end of struct or union
glitz_glxint.h:116: warning: type defaults to 'int' in declaration of 'pbuffer'
glitz_glxint.h:116: warning: data definition has no type or storage class
glitz_glxint.h:119: error: syntax error before '}' token
glitz_glx_drawable.c:36: error: syntax error before 'GLXDrawable'
glitz_glx_drawable.c:40: warning: function declaration isn't a prototype
glitz_glx_drawable.c: In function '_glitz_glx_create_drawable':
glitz_glx_drawable.c:43: error: invalid application of 'sizeof' to incomplete type 'glitz_glx_drawable_t'
glitz_glx_drawable.c:47: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:47: error: 'screen_info' undeclared (first use in this function)
glitz_glx_drawable.c:47: error: (Each undeclared identifier is reported only once
glitz_glx_drawable.c:47: error: for each function it appears in.)
glitz_glx_drawable.c:48: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:48: error: 'context' undeclared (first use in this function)
glitz_glx_drawable.c:49: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:49: error: 'glx_drawable' undeclared (first use in this function)
glitz_glx_drawable.c:50: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:50: error: 'glx_pbuffer' undeclared (first use in this function)
glitz_glx_drawable.c:51: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:52: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:54: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:55: error: 'format' undeclared (first use in this function)glitz_glx_drawable.c: In function '_glitz_glx_drawable_update_size':
glitz_glx_drawable.c:80: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:82: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:82: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:83: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:83: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:84: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:85: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:87: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:91: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:92: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function '_glitz_glx_create_pbuffer_drawable':
glitz_glx_drawable.c:124: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_create_pbuffer':
glitz_glx_drawable.c:135: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_create_drawable_for_window':
glitz_glx_drawable.c:156: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:159: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:173: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_create_pbuffer_drawable':
glitz_glx_drawable.c:191: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:194: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_destroy':
glitz_glx_drawable.c:209: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:210: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:217: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:218: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:219: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:223: warning: implicit declaration of function 'glXGetCurrentDrawable'
glitz_glx_drawable.c:223: warning: nested extern declaration of 'glXGetCurrentDrawable'
glitz_glx_drawable.c:223: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:224: warning: implicit declaration of function 'glXMakeCurrent'
glitz_glx_drawable.c:224: warning: nested extern declaration of 'glXMakeCurrent'glitz_glx_drawable.c:224: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:227: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:228: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:228: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c: In function 'glitz_glx_swap_buffers':
glitz_glx_drawable.c:239: warning: implicit declaration of function 'glXSwapBuffers'
glitz_glx_drawable.c:239: warning: nested extern declaration of 'glXSwapBuffers'glitz_glx_drawable.c:239: error: dereferencing pointer to incomplete type
glitz_glx_drawable.c:240: error: dereferencing pointer to incomplete type
make[3]: *** [glitz_glx_drawable.lo] Error 1
make[3]: Leaving directory `/home/matteo/xgl/glitz/src/glx'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matteo/xgl/glitz/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matteo/xgl/glitz'
make: *** [all] Error 2

```

any ideas?

---

### Post by hornett on 2006-02-04
> In file included from glitz_glx_drawable.c:30:
glitz_glxint.h:34:19: error: GL/gl.h: No such file or directory
glitz_glxint.h:35:20: error: GL/glx.h: No such file or directory


Looks like you're missing some development files there... Did you install the dev packages in the first post?

---

### Post by Azriphale on 2006-02-04
Those files are located in the package 
```
libgl1-mesa-dev
```

I have added is to the dep list in the howto.
Thanks.

Sorry, I have limited time to try this with Mesa CVS and Xorg 7 because I am busy with 3rd year electrical engineering at university. Very limited time. 

I am, however, currently trying to pull the mesa source from CVS to give it all another run.

---

### Post by Rob2687 on 2006-02-04
Well I got xglserver to compile with glx enabled but it just won't run >.<
Get closer, I can feel it. Haha

Anyways...back to studying for me too.

> 
robert@ubuntu:~/Desktop/Xserver-6.6.1/hw/xgl$ ./Xgl :1 -ac -accel xv -accel glx:pbuffer
dlopen: /usr/local/lib/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

Fatal server error:
No GLX modules loaded
dlopen: /usr/local/lib/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

FatalError re-entered, aborting
No GLX modules loaded
Aborted


Do not use --enable-xglxserver 
Only --enable-xglserver --enable-glx

I don't know why but it just won't compile with xglxserver. Everything seems to compile properly but I just can't get it to run. I don't even know if I'm on the right track though. I'm just a noob reading through the Freedesktop mailing list and these forums. ;)

---

### Post by terrax on 2006-02-04
This xgl version you are talking about. Is that the xgl version with all the cool stuff?

I mean, is it developed so much, it actallu will run WITH the nice effekts etc.

---

### Post by Rob2687 on 2006-02-04
I think it is...otherwise what the hell am I trying to compile with for. Haha.

---

### Post by terrax on 2006-02-05
Cool Im gonna try it then :)

---

### Post by bluebyt on 2006-02-05
Is it possible to have just the above border windows transparent like those screenshots?

[http://www.linuxedge.org/index.php?q=node/39](http://www.linuxedge.org/index.php?q=node/39)

---

### Post by terrax on 2006-02-05
Anyone got it compiling with --enable-xglxserver --enable-xglserver --enable-glx ?

When I compile with just --enable-xglxserver --enable-xglserver, no glx extensions is avalible?

Can it has something about we need xorg 7.0?

---

### Post by terrax on 2006-02-05
I can only compile it, with --enable-xglserver --enable-xglxserver

But when I try running it, its just starts as normal with the nvidia logo. And then there is inly a grey screen, with my mousepointer?

I use kubuntu. Has it something todo with that?

---

### Post by imranj on 2006-02-08
can we have the lastest version of this how to written and update with all the fixes and new instructions which work and how do we handle and install it for dudes who use Kubuntu.

thanks

---

### Post by terrax on 2006-02-08
I wrote a new howto, which work for kde and gnome:
[http://www.ubuntuforums.org/showthread.php?p=715136#post715136](http://www.ubuntuforums.org/showthread.php?p=715136#post715136)

---

### Post by EstevaoSoares on 2006-02-08
Thanks a lot. I'll take a lot at it.

---

### Post by thiagopanda on 2007-01-06
can someone help me.... im stuck here:

./autogen.sh --enable-composite --enable-xglxserver --prefix=/opt/xglxserver


with this error:

autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.ac: 34: macro `AM_PROG_AS' not found in library
autoreconf: aclocal failed with exit status: 1


what should i do to make this thing work correct ?

---

