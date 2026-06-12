---
title: "[SOLVED] FTGL issues"
date: 2008-07-20
forum: Programming Talk
---

### Post by Senesence on 2008-07-20
Ok, before I say anything else I should probably mention that FTGL is a library for rendering text in OpenGL (using FreeType 2):

Link: [http://ftgl.sourceforge.net/docs/html/](http://ftgl.sourceforge.net/docs/html/)

I have a problem with this library under ubuntu:

I used Synaptic to get the "ftgl-dev" package, but there seems to be a discrepancy between the files found in /usr/include/FTGL, and the specification outlined in the doxygen generated documentation. (namely: I noticed that doing "#include <FTGL/ftgl.h>" (as is specified in this small "tutorial": [http://ftgl.sourceforge.net/docs/html/ftgl-tutorial.html](http://ftgl.sourceforge.net/docs/html/ftgl-tutorial.html)) is wrong, because the header file installed through getting the "ftgl-dev" package is actually "FTGL.h" - in caps. 

So, having figured that out, I thought doing "#include <FTGL/FTGL.h>" would do the trick, but even though the header file was now found by the compiler, my FTGL calls were being marked as "undefined", and the program would still not compile.

Is there something wrong with the "ftgl-dev" package, or am I doing something wrong here?

Any help would be greatly appreciated.

TIA.

---

### Post by WW on 2008-07-20
Could you show the command that you use to compile your program, and the errors that you get?

EDIT: The latest version of ftgl is 2.1.3~rc5.  I downloaded this version from sourceforge, and the main header is, in fact, FTGL/ftgl.h (lower case).   Ubuntu has version 2.1.2.  Perhaps this has changed between versions, and the tutorial is for the latest version.  The NEWS file in the source tarball for version 2.1.3~rc5 says "Stable API. Public headers are now frozen.", which suggests that up until this version, the headers had been changing.

The Ubuntu package [ftgl-dev](http://packages.ubuntu.com/hardy/ftgl-dev) includes HTML documentation (see the file list [here](http://packages.ubuntu.com/hardy/i386/ftgl-dev/filelist); note that this list shows FTGL/FTGL.h), so it might be better to use /usr/share/doc/ftgl-dev/html/index.html as a reference instead of the sourceforge web page.

---

### Post by Senesence on 2008-07-21
> **WW said:**
> Could you show the command that you use to compile your program, and the errors that you get?

g++ program.cpp -o program.bin -lfreetype -lGL -lftgl

> so it might be better to use /usr/share/doc/ftgl-dev/html/index.html as a reference instead of the sourceforge web page.

Not much of a reference there...Isn't there an example program that demonstrates proper usage, along with the required compile command in reference to the "ftgl-dev" package.

If it's not too much trouble, could you put together a minimal program using "ftgl-dev", and see if you can get it to compile?

---

### Post by WW on 2008-07-21
I'm on a Mac right now, and my Ubuntu server is "headless" (no X), so I can't really build an FTGL program like you might.

Again looking at [this list of files](http://packages.ubuntu.com/hardy/i386/ftgl-dev/filelist), you can see that the ftgl-dev package includes the file /usr/lib/pkgconfig/ftgl.pc.  This is a configuration file for the **pkg-config** command.  This command will give you the command line options to compile and link a program with FTGL.

To see the options, try this:
```

$ pkg-config --cflags ftgl
$ pkg-config --libs ftgl

```
You can use more than one option at once:
```

$ pkg-config --cflags --libs ftgl

```
To use this in your g++ command, use pkg-config with back-ticks.  This should compile and link your program:
```

g++ program.cpp -o program.bin `pkg-config --cflags --libs ftgl`

```

But this won't fix the problem of an API change between versions 2.1.2 and 2.1.3~rc5.  For that, you'll have to find 2.1.2 documentation.  There are more files /usr/share/doc/ftgl-dev/html/.  If those don't help, you could try contacting the developers to see if there is a 2.1.2 tutorial somewhere.

Or, you could remove the package ftgl-dev, and instead install version 2.1.3~rc5 from source.

---

### Post by Senesence on 2008-07-22
Ahh, I see.

So `pkg-configure --cflags --libs ftgl` will just dump the proper -I and -l options for the compiler.

Great, I have it working now....although, I think I may opt out to build the latest version from source, and use that, because I can't seem to find detailed docs for 2.1.2.

---

