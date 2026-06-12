---
title: "vis5d+ on Ubuntu dapper"
date: 2006-08-10
forum: Packaging and Compiling Programs
---

### Post by spacefizzicist on 2006-08-10
Dear Forum members,
Greetings!:-o
 
I am trying to compile the visualization package vis5d+ ([http://vis5d.sourceforge.net](http://vis5d.sourceforge.net)) on ubuntu dapper. However, I am unsuccessful (I have successfully made it to work before on debian unstable with mesa, mixkit, fltk support etc. before I switched to Ubuntu).. Umm, I am kind of hardpressed for time to troubleshoot deeper, so I'd appreciate it you could give me any advice/feedback. Thanks in advance!
~rk
---------------------
$cat /proc/version
Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
--
I have downloaded vis5d+-1.3.0-beta and on configuring I get the following error:

<stdout>

configure: error: Couldn't include header file <GL/gl.h>; you may need to specify the path to OpenGL include files in CPPFLAGS.

</stdout>

I tried:
$./configure CPPFLAGS=-I/usr/include/GL 

and also included /usr/include/FL along with other vars (CC,LDFLAGS etc) and still the same result  :(
--
I don't know if there is a problem with the libraries. I tried to pass the variables along with ./configure or define using export(bash shell) before configuring. I have libfltk1.1 and libfltk1.1-dev installed. The config.log is kinda long (I can attach a shorter version, if someone requires it) and so I haven't attached it, but the list of files in /usr/include/FL and /usr/include/GL is attached. I wish I had more time to spent on understanding the configure script. Please help.

---

### Post by mlind on 2006-08-10
These packages seem to provide GL/gl.h
```

mesa-common-dev: usr/include/GL/gl.h
mingw32-runtime: usr/i586-mingw32msvc/include/GL/gl.h
nvidia-glx-dev: usr/share/doc/nvidia-glx-dev/include/GL/gl.h
nvidia-glx-legacy-dev: usr/share/doc/nvidia-glx-legacy-dev/include/GL/gl.h

```
Do you have **mesa-common-dev** installed?

---

### Post by spacefizzicist on 2006-08-10
THanks for the reply. Yes, I do have mesa-common-dev installed. The package I am trying to install (vis5d+ --> Installation instructions at: [http://vis5d.sourceforge.net/doc/ch02sec2.html#CH02SEC2.3](http://vis5d.sourceforge.net/doc/ch02sec2.html#CH02SEC2.3)) requires the free openGL replacement mesa. I have installed the other mesa lib files also.:confused: 
--
$ dpkg --list l*mesa*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                  Version                               Description
+++-=====================================-=====================================-==========================================================================================
ii  libgl1-mesa                           6.4.1-0ubuntu8                        A free implementation of the OpenGL API -- GLX runtime
ii  libgl1-mesa-dbg                       6.3.2-0ubuntu6breezy1                 A free implementation of the OpenGL API -- debugging package
ii  libgl1-mesa-dev                       6.4.1-0ubuntu8                        A free implementation of the OpenGL API -- GLX development support files
ii  libgl1-mesa-dri                       6.4.1-0ubuntu8                        A free implementation of the OpenGL API -- DRI modules
un  libgl1-mesa-dri-dev                   <none>                                (no description available)
ii  libglu1-mesa                          6.4.1-0ubuntu8                        The OpenGL utility library (GLU)
ii  libglu1-mesa-dev                      6.4.1-0ubuntu8                        The OpenGL utility library -- development support files
---------------
THe configure script craps out and can't seem to find the openGL library?!! 
I have attached a gzipped config.log. The OS is correctly recognized and so are the compilers and such. I'd appreciate it much if any of you guys have the time to quickly glance over the file and see what mistakes I've made..
Thanks in advance.
~rk

---

### Post by mlind on 2006-08-10
I tried configuring 1.3.0-beta on a minimal chroot with --enable-gtk parameter and here's the packages (+dependencies) I needed to install.

```

libgtk1.2-dev
libglu1-mesa-dev

```

---

### Post by spacefizzicist on 2006-08-10
Thanks for the reply. But I'm still stuck with the same configure error :(
> *******************************************************
*       Congratulations! You are running Linux.       *
*******************************************************
checking whether cc accepts -malign-double... yes
checking whether cc accepts -mcpu=pentiumpro... no
checking whether cc accepts -mpentiumpro... yes
checking whether cc accepts -O3 -fomit-frame-pointer -malign-double -mpentiumpro... yes
checking for float... yes
checking size of float... 4
checking for int... yes
checking size of int... 4
checking for signed char... yes
checking size of signed char... 1
checking whether byte ordering is bigendian... no
checking for sqrt in -lm... yes
checking for zlib.h... yes
checking for deflate in -lz... yes
checking for png.h... yes
checking for png_write_image in -lpng... yes
checking for strcasecmp... (cached) yes
checking for strncasecmp... yes
checking for strdup... (cached) yes
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for glBegin in -lGL... yes
checking for gluProject in -lGLU... yes
checking for GL/gl.h... no
configure: error: Couldn't include header file <GL/gl.h>; you may need to specify the path to OpenGL include files in CPPFLAGS.

Still, the script can't find the header files <GL/gl.h> I am not sure where they are supposed to be (I guess I have to check the configure script), but as I said before, I tried with CPPFLAGS="-I /usr/include/GL"
```

$ ls /usr/include/GL
glu.h  glu_mangle.h  glxext.h  glx.h  glxint.h  glx_mangle.h  glxmd.h  glxproto.h  glxtokens.h  internal

```
Hmm, the gl.h file is inside the /usr/include/FL directory (which gets installed from libfltk1.1-dev package) and the /usr/include/GL does "NOT" have gl.h file?!!! Am I missing something?? I tried copying the gl.h from /usr/include/FL to /usr/include/GL, but still no luck?

What am I missing here? Please enlighten :)
Thanks for your time and help, I appreciate it.
~rk

---

### Post by mlind on 2006-08-10
Have you installed the build dependecies using apt-get or aptitude? Because mesa-common-dev provides /usr/include/GL/gl.h and that package is installed as dependency for libglu1-mesa-dev..

I'd suggest to rollback the steps you've done so far and start by installing those two package using aptitude. If you want to experiment, use debootstap to create minimal chroot and try building your package there <hint>or use pbuilder</hint>

---

### Post by spacefizzicist on 2006-08-11
Thank you for your helpful suggestions.
I did:
```
sudo apt-get install --reinstall mesa-common-dev
``` and that installed the gl.h and other files in /usr/include/GL, tho I still can't understand why it didn't before?!! :-o

*Anyways, I could compile and install vis5d+*, but --enable-gtk failed during make and so did compiling using mixkit libraries (with-mixkit=<location of libmix.a>) from [http://graphics.cs.uiuc.edu/~garland/software/qslim.html]("http://graphics.cs.uiuc.edu/~garland/software/qslim.html")

If any of you guys could get it to compile with GTK and MIXKIT library, I would be happy to hear from you. Again, I thank you for your help and time! 
Happy computing! 
/rk

---

### Post by mlind on 2006-08-11
I was able to compile --with-gtk using libgtk1.2-dev package.
I hope that helps for enabling that feature.

---

### Post by geologist on 2006-11-26
Dear all!
:) 

I am trying to do the same in the same environemnt, but having problem to compile the mixkit. Does anybody know how can I workaround this? I attached the make log.
](*,)

---

