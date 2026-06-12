---
title: "Compile can't find include files"
date: 2007-03-18
forum: Programming Talk
---

### Post by josesanders on 2007-03-18
I'm trying to compile a patched version of GATOS in a (probably futile) attempt to get tv out to work for my old ATI video card.  I use xmkmf to create a makefile, but when I try to compile it, it can't find a bunch of include files.  I have located the files, but I don't know how to get the compiler to look in the right place.  I've tried setting the path variable with the following:

$ export PATH=$PATH:/usr/include/X11

This has no effect.  I'm experienced with programming in Windows, but I'm new to compiling things in Linux, so it's probably something very obvious.  I appreciate any help.

---

### Post by phossal on 2007-03-18
Here is a pretty awesome explanation: [http://www.network-theory.co.uk/docs/gccintro/gccintro_22.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_22.html). You'll get *easy* answers too, but reading a few pages of the site above will broaden your understanding. 

Regards.

---

### Post by lloyd_b on 2007-03-18
First off, PATH has no effect on whether gcc will find include files or not.  It's strictly used for the shell to find executables.

You need to change the gcc command line you're using, adding "-I /usr/include/X11" to the command. 

the "-I {dir}" tells gcc to add the specified directory to the list of directories it searches to find included files.

(Note: that "dash capital eye", not "dash ell".)

Lloyd B.

---

### Post by rplantz on 2007-03-18
> **phossal said:**
> Here is a pretty awesome explanation: [http://www.network-theory.co.uk/docs/gccintro/gccintro_22.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_22.html). You'll get *easy* answers too, but reading a few pages of the site above will broaden your understanding. 

Regards.

Thank you for the reference. As a long time user of gcc, I really appreciate the approach taken in this book. I have not had a chance to read the entire book, but it seems to cut right to the chase and cover the important issues without getting bogged down in all the seldom-used options.

---

### Post by josesanders on 2007-03-20
Thanks for the responses.  I'm not actually using gcc directly, though, so I can't specify included directories directly on the command line.  The source code uses an Imakefile, from which I create a makefile using xmkmf.  What I had to do, then, was modify the Imakefile.  There was a section there for included directories.  Maybe there's a better way to do this, but I couldn't find it.

---

### Post by JoxBG on 2007-03-22
For your process you need to set the extra include directories in Imakefile, using the directive:

   EXTRA_INCLUDES = -I/some/dir.

That way it gets cascaded to the Makefile created by xmkmf

---

