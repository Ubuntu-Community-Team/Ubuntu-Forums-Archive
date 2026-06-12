---
title: "Making a .deb out of C code"
date: 2011-10-08
forum: Packaging and Compiling Programs
---

### Post by Michael-Siu on 2011-10-08
Hi, 

I want to know if it is possible to make a .deb package out of any C source code. I wonder if it is possible to make a simple console program written in C but to be able to install it as a .deb package and when I go to the applications menu it appears in there and has an icon also. If it is possible how can I do that, i've been reading a lot about some rules I gotta follow to create the .deb package, but I don't finish to understand how to, if somebody could give me a hand I would appreciate it so much. I've been reading a lot from many sites but I still haven't gotten it to work.

So if someone could give me a simple example with a Hello World! program and how to package it would be a lot better, I am aware that every program is different therefore the process should be different but just to have a more concrete example.

thanx alot in advance. :):):)

---

### Post by Bachstelze on 2011-10-09
Since I'm bored...

Code:

```
firas@itsuki helloworld-1.0 % cat hello.c 
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
        printf("Hello, world!\n");
        return EXIT_SUCCESS;
}
firas@itsuki helloworld-1.0 % cat Makefile 
CC=gcc
CFLAGS=-std=c99 -pedantic -Wall -Wextra -Werror
OBJFILES=hello.o
OUTFILE=hello

INSDIR=/usr/local/bin
ifdef DESTDIR
        INSDIR=/usr/bin
endif

$(OUTFILE): $(OBJFILES)
        $(CC) -o $@ $<

install: $(OUTFILE)
        install -d -o root -m 0755 $(DESTDIR)$(INSDIR)
        install -o root -m 0755 $< $(DESTDIR)$(INSDIR)

clean:
        rm -f $(OUTFILE) $(OBJFILES)


```

Directory can be anything you want, but projectname-version is common. Compress directory as packagename_version.orig.tar.gz. Here packagename is helloworld so:

```
firas@itsuki helloworld % tar czvf helloworld_1.0.orig.tar.gz helloworld-1.0
helloworld-1.0/
helloworld-1.0/hello.c
helloworld-1.0/Makefile

```

Then go back into the source directory and run dh_make:

```
firas@itsuki helloworld % cd helloworld-1.0 
firas@itsuki helloworld-1.0 % dh_make

Type of package: single binary, indep binary, multiple binary, library, kernel module, kernel patch?
 [s/i/m/l/k/n] s

Maintainer name : Firas Kraiem
Email-Address   : firas@fkraiem.org 
Date                            : Sun, 09 Oct 2011 08:38:41 +0200
Package Name     : helloworld
Version                 : 1.0
License                 : blank
Type of Package : Single
Hit <enter> to confirm: 
Skipping creating ../helloworld_1.0.orig.tar.gz because it already exists
Done. Please edit the files in the debian/ subdirectory now. You should also
check that the helloworld Makefiles install into $DESTDIR and not in / .

```

It will create and populate the debian/ directory. There's a lot of junk in there so do some cleaning up:

```
firas@itsuki helloworld-1.0 % cd debian 
firas@itsuki debian % ls 
changelog  docs                helloworld.cron.d.ex    manpage.1.ex     postinst.ex  README.Debian  watch.ex
compat     emacsen-install.ex  helloworld.default.ex   manpage.sgml.ex  postrm.ex    README.source
control    emacsen-remove.ex   helloworld.doc-base.EX  manpage.xml.ex   preinst.ex   rules
copyright  emacsen-startup.ex  init.d.ex               menu.ex          prerm.ex     source
firas@itsuki debian % rm *ex *EX
firas@itsuki debian % ls
changelog  compat  control  copyright  docs  README.Debian  README.source  rules  source
firas@itsuki debian % rm README.*

```

You can keep the READMEs if you want to use them, though... Then modify changelog, control and copyright:

```
firas@itsuki debian % cat changelog 
helloworld (1.0-1) natty; urgency=low

  * Well, hello, world!

 -- Firas Kraiem <firas@fkraiem.org>  Sun, 09 Oct 2011 08:38:41 +0200
firas@itsuki debian % cat control 
Source: helloworld
Section: misc
Priority: extra
Maintainer: Firas Kraiem <firas@fkraiem.org>
Build-Depends: debhelper (>= 7.0.50~)
Standards-Version: 3.9.1

Package: helloworld
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: A friendly program
 This friendly program is an example for Ubuntu forums
 user Michael-Siu.
firas@itsuki debian % cat copyright 
No copyright.

```

Then get back in the source dir, run debuild and hope for the best.

```
firas@itsuki debian % cd ..
firas@itsuki helloworld-1.0 % debuild
[...lots of text...]
firas@itsuki helloworld-1.0 % sudo dpkg -i ../helloworld_1.0-1_i386.deb 
(Reading database ... 138355 files and directories currently installed.)
Preparing to replace helloworld 1.0-1 (using ../helloworld_1.0-1_i386.deb) ...
Unpacking replacement helloworld ...
Setting up helloworld (1.0-1) ...
firas@itsuki helloworld-1.0 % rehash
firas@itsuki helloworld-1.0 % hello 
Hello, world!

```

No menu icon cause I don't care about them and they're useless for a console program anyway. You'll have to find that out yourself.

---

### Post by Bachstelze on 2011-10-09
Note that if you ever want to get your package in the archive, you will have to write a proper debian/copyright with all the legal gobbledygook.

---

### Post by Michael-Siu on 2011-10-09
Thank you very much my friend it helped me a lot.

---

