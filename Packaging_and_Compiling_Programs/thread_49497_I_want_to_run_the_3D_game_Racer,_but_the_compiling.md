---
title: "I want to run the 3D game Racer, but the compiling process failed."
date: 2005-07-16
forum: Packaging and Compiling Programs
---

### Post by RJARRRPCGP on 2005-07-16
I'm trying to compile Racer under Ubuntu "Hoary". Here's what I got:

root@ubuntu:~/Desktop/rr050src# make
/usr/bin/make -C src/libs/qlib
make[1]: Entering directory `/home/rjarrrpcgp/Desktop/rr050src/src/libs/qlib'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/l inux -Wall -c q3ddlg.cpp
In file included from ../../../include/qlib/object.h:6,
from ../../../include/qlib/dialog.h:6,
from q3ddlg.cpp:9:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
In file included from ../../../include/qlib/bitmap.h:8,
from ../../../include/qlib/image.h:6,
from ../../../include/qlib/dialog.h:8,
from q3ddlg.cpp:9:
../../../include/qlib/drawable.h:12:20: GL/glx.h: No such file or directory
In file included from ../../../include/qlib/bitmap.h:8,
from ../../../include/qlib/image.h:6,
from ../../../include/qlib/dialog.h:8,
from q3ddlg.cpp:9:
../../../include/qlib/drawable.h:37: error: ISO C++ forbids declaration of `
GLXDrawable' with no type
../../../include/qlib/drawable.h:37: error: `GLXDrawable' declared as a
`virtual' field
../../../include/qlib/drawable.h:37: error: parse error before `(' token
../../../include/qlib/drawable.h:39: error: ISO C++ forbids declaration of `
Drawable' with no type
../../../include/qlib/drawable.h:39: error: `Drawable' declared as a `virtual'
field
../../../include/qlib/drawable.h:39: error: parse error before `(' token
In file included from ../../../include/qlib/dialog.h:9,
from q3ddlg.cpp:9:
../../../include/qlib/window.h:17:57: X11/X.h: No such file or directory
In file included from ../../../include/qlib/dialog.h:9,
from q3ddlg.cpp:9:
../../../include/qlib/window.h:41: error: syntax error before `;' token
../../../include/qlib/window.h:66: error: syntax error before `*' token
../../../include/qlib/window.h:69: error: 'QWindowRef' is used as a type, but
is not defined as a type.
../../../include/qlib/window.h:90: error: parse error before `)' token
../../../include/qlib/window.h:91: error: parse error before `)' token
../../../include/qlib/window.h:96: error: syntax error before `*' token
../../../include/qlib/window.h:104: error: semicolon missing after declaration
of `QXWindow'
../../../include/qlib/window.h:104: error: two or more data types in
declaration of `PrefWM'
../../../include/qlib/window.h:104: error: invalid return type for function `
QXWindow PrefWM(bool)'
../../../include/qlib/window.h:104: error: because the following virtual
functions are abstract:
../../../include/qlib/drawable.h:45: error: virtual int QDrawable::GetWidth( )
../../../include/qlib/drawable.h:46: error: virtual int QDrawable::GetHeight ()
../../../include/qlib/window.h: In function `QXWindow* GetParent()':
../../../include/qlib/window.h:123: error: `parent' undeclared (first use this
function)
../../../include/qlib/window.h:123: error: (Each undeclared identifier is
reported only once for each function it appears in.)
../../../include/qlib/window.h: At global scope:
../../../include/qlib/window.h:128: error: parse error before `)' token
../../../include/qlib/window.h:134: error: parse error before `)' token
../../../include/qlib/window.h:150: error: virtual outside class declaration
../../../include/qlib/window.h:153: error: parse error before `}' token
../../../include/qlib/window.h:364: error: type specifier omitted for parameter
`Window'
../../../include/qlib/window.h:364: error: parse error before `=' token
../../../include/qlib/window.h:369: error: `Window' was not declared in this
scope
../../../include/qlib/window.h:369: error: parse error before `,' token
../../../include/qlib/window.h:370: error: `Window' was not declared in this
scope
../../../include/qlib/window.h:370: error: parse error before `)' token
In file included from ../../../include/qlib/font.h:6,
from ../../../include/qlib/edit.h:8,
from ../../../include/qlib/dialog.h:11,
from q3ddlg.cpp:9:
../../../include/qlib/app.h:15:22: X11/Xlib.h: No such file or directory
../../../include/qlib/app.h:16:23: X11/Xutil.h: No such file or directory
../../../include/qlib/app.h:17:19: X11/X.h: No such file or directory
../../../include/qlib/app.h:18:27: X11/Intrinsic.h: No such file or directory
In file included from ../../../include/qlib/bc.h:10,
from ../../../include/qlib/app.h:26,
from ../../../include/qlib/font.h:6,
from ../../../include/qlib/edit.h:8,
from ../../../include/qlib/dialog.h:11,
from q3ddlg.cpp:9:
../../../include/qlib/alphabuf.h:60: error: parse error before `)' token
In file included from ../../../include/qlib/font.h:6,
from ../../../include/qlib/edit.h:8,
from ../../../include/qlib/dialog.h:11,
from q3ddlg.cpp:9:
../../../include/qlib/app.h:117: error: parse error before `[' token
../../../include/qlib/app.h:148: error: `Window' was not declared in this scope
../../../include/qlib/app.h:148: error: parse error before `)' token
../../../include/qlib/app.h:169: error: parse error before `)' token
In file included from ../../../include/qlib/edit.h:8,
from ../../../include/qlib/dialog.h:11,
from q3ddlg.cpp:9:
../../../include/qlib/font.h:9:22: X11/Xlib.h: No such file or directory
In file included from ../../../include/qlib/edit.h:8,
from ../../../include/qlib/dialog.h:11,
from q3ddlg.cpp:9:
../../../include/qlib/font.h:75: error: parse error before `)' token
In file included from q3ddlg.cpp:9:
../../../include/qlib/dialog.h:18:57: X11/X.h: No such file or directory
In file included from q3ddlg.cpp:14:
../../../include/linux/bstring.h:9:7: warning: no newline at end of file
q3ddlg.cpp:18:22: X11/Xlib.h: No such file or directory
In file included from ../../../include/qlib/error.h:7,
from ../../../include/qlib/debug.h:21,
from q3ddlg.cpp:20:
../../../include/qlib/opengl.h:17:55: X11/Xlib.h: No such file or directory
../../../include/qlib/opengl.h:35:19: GL/gl.h: No such file or directory
../../../include/qlib/opengl.h:36:20: GL/glu.h: No such file or directory
../../../include/qlib/opengl.h:39:20: GL/glx.h: No such file or directory
In file included from ../../../include/qlib/error.h:7,
from ../../../include/qlib/debug.h:21,
from q3ddlg.cpp:20:
../../../include/qlib/opengl.h:104: error: 'GLXContext' is used as a type, but
is not defined as a type.
../../../include/qlib/opengl.h:118: error: type specifier omitted for parameter
`XVisualInfo'
../../../include/qlib/opengl.h:118: error: parse error before `*' token
../../../include/qlib/opengl.h:122: error: parse error before `ctx'
../../../include/qlib/opengl.h:140: error: parse error before `)' token
In file included from ../../../include/qlib/debug.h:21,
from q3ddlg.cpp:20:
../../../include/qlib/error.h:48: error: parse error before `,' token
../../../include/qlib/error.h:50: error: parse error before `,' token
../../../include/qlib/error.h:52: error: parse error before `,' token
../../../include/qlib/error.h:54: error: parse error before `,' token
q3ddlg.cpp:41: warning: `int orgX' defined but not used
q3ddlg.cpp:41: warning: `int orgY' defined but not used
make[1]: *** [q3ddlg.o] Error 1
make[1]: Leaving directory `/home/rjarrrpcgp/Desktop/rr050src/src/libs/qlib'
make: *** [_subdir_src/libs/qlib] Error 2
root@ubuntu:~/Desktop/rr050src#

What is the cause?

---

### Post by kalle314 on 2005-07-29
One thing is probably that the headerfiles simply is missing - I was just looking in /usr/include/X11, and found that there was no Xlib.h, Xutil.h etc.
Maybe the headerfiles can be found somewhere and installed?

I also got a lot of parse errors when compiling a program that g++ compiled without problem in cygwin, so I don't know the cause for that.

edit: there was a package with X11 headers - libX11-something.
My parse error trouble was solved to - I am not sure how - maybe it helps writing "sudo make" instead of "make".

---

### Post by black hole sun on 2005-08-02
[QUOTE=kalle314]One thing is probably that the headerfiles simply is missing - I was just looking in /usr/include/X11, and found that there was no Xlib.h, Xutil.h etc.
Maybe the headerfiles can be found somewhere and installed?

I also got a lot of parse errors when compiling a program that g++ compiled without problem in cygwin, so I don't know the cause for that.

edit: there was a package with X11 headers - libX11-something.
My parse error trouble was solved to - I am not sure how - maybe it helps writing "sudo make" instead of "make".[/QUOTE]
 you need the -dev packages of  the X11 binaries. there are quite a few x11 packages so I am not sure which you need exactly -- try the libmesa devs for sure

---

### Post by mun3kh on 2005-11-06
You will need the:
"X11 toolkit intrinsics library"
try "libxt6" in synaptic

This will cover you for Intrinsic.h: no such file or directory

I found this was a dependency when compiling firefox 1.5 rc2

---

