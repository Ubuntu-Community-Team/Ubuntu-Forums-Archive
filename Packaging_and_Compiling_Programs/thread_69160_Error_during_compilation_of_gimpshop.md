---
title: "Error during compilation of gimpshop"
date: 2005-09-25
forum: Packaging and Compiling Programs
---

### Post by Blue1k on 2005-09-25
When trying to compile gimpshop in Breezy I keep getting a list of errors during "make" like this:

gimp-composite-mmx.c:94: error: unknown register name ‘%mm0’ in ‘asm’

I found somewhere that this is an inherent bug with gcc4 and I'm wondering if it is wise to install 3.4 in conjuctions with 4? Am I right on this?

Or should I uninstall gcc 4 and install 3.4?

Thanks!!

---

### Post by jlapier on 2005-09-27
I'm just shootin from the hip here (not at home where my ubuntu machine is patiently waiting) - I believe you should be able to have multiple major releases of gcc installed - ie, both 3.4 and 4. If you want to force it to compile with gcc3.4 you probably have to specify that option when you run ./configure (by using a command-line argument - try "./configure --help")

---

### Post by Blue1k on 2005-10-22
Any ideas with this one? I have both 3.4 and 4 installed. Configure works perfectly but make doesn't.

What do I have to specify in configure?

---

### Post by Hookki on 2005-11-17
I had the same problem, this should fix it:

export CC=gcc-3.4
./configure
make

---

### Post by metasquier on 2005-12-02
Ive just done all that, and the compilation went fine, but now when I try to do make install, it give me this:

```
libtool: link: unable to infer tagged configuration
libtool: link: specify a tag with `--tag'
libtool: install: error: relink `libgimpmodule-2.0.la' with the above command before installing it

```

Could someone please help me with this?  I believe it has somthing to do with the fact that gcc-3.4 was used instead of gcc-4.0, and now libtool, and autoconf are the wrong versions.  Could someone please help to rectify this problem?
Thanks

---

