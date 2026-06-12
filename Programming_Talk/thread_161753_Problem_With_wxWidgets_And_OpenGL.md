---
title: "Problem With wxWidgets And OpenGL"
date: 2006-04-17
forum: Programming Talk
---

### Post by lkz on 2006-04-17
I am having problems with opengl samples which come with wxWidgets, all the other samples work fine.

The first problem with the opengl cube sample was, that the linker couldn't find libwx_gtk_gl, after investigating this a bit I figured that it had to link against libwx_gtk2u_gl-2.6 and this made it compile, however I then got this error when running the program

```

The program 'cube' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 268 error_code 8 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

My linux skills are not great enough to dive into debugging this problem. The next thing I tried was to download the 2.6.3 source of wxwidgets and build it myself, however it seems to install itself into /usr/local/ and I am unable to compile any of the examples, getting alot of undefined references

So my last resort is that some one might have gotten wxwidgets with opengl to work, with either the wxwidgets package thats availabe through apt or by building wxwidgets 2.6.3 themselves, and would like to spread some light on what I could possibly be doing wrong.

---

### Post by lkz on 2006-04-18
I managed to finally find a solution, which explains howto build and make wxwidgets 2.6.3 work in ubuntu.

First thing I did was remove all wxwidgets packages with Synpatic (otherwise I encountered conflicts).

Next thing I did was switch to using g++3.3 instead of g++4.0, g++4.0 will build however the samples will not and you will get alot of warnings with g++4.0. You learn how to switch between the two versions of g++/gcc here : [http://ubuntuforums.org/showthread.php?t=80145](http://ubuntuforums.org/showthread.php?t=80145)

Now, I downloaded wxWidget 2.6.3 and followed the instructions in install.txt, but added --with-opengl and --enable-debug to the configure flags.

Now everything is installed in /usr/local/

So I tried the samples, which compiled nicely, however they wouldn't run because the shared libraries couldn't be found. So i created the file /etc/ld.so.conf and added the line : /usr/local/lib and ran **ldconfig** in a console. And now everything worked as should.

A note is that the makefiles which are used for the samples are quite complex, and you can use the makefile.unx which is availabe in the samples directory of the original wxWidgets 2.6.3 instead (they use wx-config), like so **make -f makefile.unx**. However the opengl samples don't work with this method, as they link directly to libwx_gtk_gl, to fix this open the makefile.unx and edit the rules for $(PROGRAM) to this:

```

$(PROGRAM):	$(OBJECTS)
	$(CXX) -o $(PROGRAM) $(OBJECTS) `wx-config --libs gl` $(OPENGL_LIBS)

```

Now everything should work correctly and makefile shouldnt be such a pita to create.

---

