---
title: "Anjuta DevStudio 2.0.2- latest version!"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by weijie90 on 2006-06-14
Hi,
frustrated with the old version of anjuta in the dapper repos, i compiled my own.

Please try this deb i compiled on an i386. I hope it works.

[http://www.esnips.com/doc/1dba599c-39b6-4cec-870f-24fd6464f162/anjuta_2.0.2-1-ubuntu_i386.deb]("http://www.esnips.com/doc/1dba599c-39b6-4cec-870f-24fd6464f162/anjuta_2.0.2-1-ubuntu_i386.deb")

thanks!

---

### Post by weijie90 on 2006-06-16
Please comment, thanks!

---

### Post by schoene on 2006-06-16
it installed correctly, however I also needed to install autogen, autoconf and automake
and when I start anjuta, I can create a new project,
however I cannot open files to edit them, and cannot make the project

When I rightclick on main.cpp and choose 'Open with' - 'Document Manager', I get the error
'Failed to activate plugin: anjuta-document-manager:DocmanPlugin'

this is how anjuta looks like:
[IMG]http://users.telenet.be/schoene/screenshots/anjuta.png[/IMG]

output from creating project:
```

Creating /home/koen/Projects/foobar/ChangeLog ... Ok
Creating /home/koen/Projects/foobar/Makefile.am (using AutoGen)... Ok
Creating /home/koen/Projects/foobar/NEWS ... Ok
Creating /home/koen/Projects/foobar/README ... Ok
Creating /home/koen/Projects/foobar/autogen.sh (using AutoGen)... Ok
Creating /home/koen/Projects/foobar/configure.in (using AutoGen)... Ok
Creating /home/koen/Projects/foobar/foobar.anjuta ... Ok
Creating /home/koen/Projects/foobar/.cvsignore ... Ok
Creating /home/koen/Projects/foobar/src/Makefile.am (using AutoGen)... Ok
Creating /home/koen/Projects/foobar/src/main.cpp (using AutoGen)... Ok
Creating /home/koen/Projects/foobar/src/.cvsignore ... Ok
Creating /home/koen/Projects/foobar/po/ChangeLog ... Ok
Creating /home/koen/Projects/foobar/po/POTFILES.in (using AutoGen)... Ok
Creating /home/koen/Projects/foobar/po/.cvsignore ... Ok
New project has been created successfully
Executing: sh -c 'cd /home/koen/Projects/foobar && ./autogen.sh'
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
configure.in: installing `./install-sh'
configure.in: installing `./missing'
src/Makefile.am: installing `./depcomp'
Makefile.am: installing `./INSTALL'
Makefile.am: installing `./COPYING'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
Now type `make' to compile.

```

---

### Post by vasdee on 2006-06-20
Cheers for the package :)

I have to say that anjuta2 is a lot different from the current stable version, it seems very stripped back and from what i can tell alot of the features are now implemented as plugins. Maybe it's how the package was built or the version but was anyone able to find a way to change the linking librarys? (eg. GL, SDL etc)
I thought it might be in the 'projects' plugin but for whatever reason anjuta wouldn't let me enable that plugin :(

---

### Post by kendase3 on 2007-12-20
I just wanted to affirm that I'm having the same problem.

---

### Post by Biased turkey on 2007-12-20
I'm having that problem too but in my case it's even worse.

1) There is no compiler options submenu so I can't link a C++ program to the SDL libraries. It's not a problem if I create a new C project because one has the option to create a new C project with SDL libraries but there is no such option when creating a C++ new project.

If I create a new C project ( with the SDL option ) I can set a 640x480 screen and start SDL BUT SDL is unable to load a bitmap file ( with the SDL_LoadBMP() instruction ).

However, using exactly the same source code and compiling manually ( creating a makefile by hand ) works nicely.

My only conclusion so far is that the current stable Anjuta version is buggy.

Jacques

---

### Post by kendase3 on 2007-12-21
Yep, that sounds awfully familiar.  I wonder if the aptitude package is 2.2.3, the latest stable.  I should check on it now but I will tomorrow, hopefully someone knows of either an update or a work-around, I'm excited to get started with SDL.

---

