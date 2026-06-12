---
title: "Help,the error when I compile the cheese."
date: 2011-05-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xustblb on 2011-05-10
After I configure the cheese , when I make it .there are one error as follow.

xmllint --noout --noent --path zh_CN:./zh_CN --xinclude --postvalid ./zh_CN/cheese.xml
xsltproc -o cheese-C.omf --stringparam db2omf.basename cheese --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.3//EN" --stringparam db2omf.lang C --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/administrator/desk/cheese-2.32.0/help/cheese.omf.in"  `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` C/cheese.xml || { rm -f "cheese-C.omf"; exit 1; }
db2omf: Could not construct the OMF subject element.
  Add a subject element to /home/administrator/desk/cheese-2.32.0/help/cheese.omf.in.
make[1]: *** [cheese-C.omf] error 1
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/home/administrator/desk/cheese-2.32.0/help'
make: *** [check-recursive] error 1

---

### Post by cgroza on 2011-05-10
Cheese it's in the repos. Why do you need to compile it?

---

### Post by xustblb on 2011-05-11
> **cgroza said:**
> Cheese it's in the repos. Why do you need to compile it?
Because I want to add some function to it!but now I can't compile it !

---

### Post by MadCow108 on 2011-05-11
are you compiling the upstream source or the package?
if the package file a bug. If upstream check if the package applies some patches to make it compile.
you compile a package with: 
```
apt-get build-dep package
apt-get source --compile package
```

---

### Post by xustblb on 2011-05-11
I get the source with 'apt-get source:cheese' and I 'apt-get build-dep' before I compile it.
I don't know why!

---

### Post by xustblb on 2011-05-11
> **xustblb said:**
> I get the source with 'apt-get source:cheese' and I 'apt-get build-dep' before I compile it.
I don't know why!
I get the source with 'apt-get source:cheese' and I 'apt-get build-dep' before I compile it.
I don't know why!

---

### Post by MadCow108 on 2011-05-11
it builds fine on my machine.

can you build it in a clean chroot?
```
sudo pbuilder --create --distribution oneiric
sudo pbuilder --build cheese_2.32.0-0ubuntu2.dsc
```

---

### Post by mc4man on 2011-05-11
Why don't you post your ./configure line (and if inclined complete configure output) and  any other 'changes' if any.
The error, (db2omf: Could not construct the OMF subject element) is not completely unknown

(I don't see this anywhere - xmllint ...

---

### Post by xustblb on 2011-05-12
sorry!I don't know chroot! now I won't use it because I have no enough time to hack it! 
Thank you all the same !

---

### Post by xustblb on 2011-05-12
> **MadCow108 said:**
> it builds fine on my machine.

can you build it in a clean chroot?
```
sudo pbuilder --create --distribution oneiric
sudo pbuilder --build cheese_2.32.0-0ubuntu2.dsc
```
sorry!I don't know chroot! now I won't use it because I have no enough time to hack it! 

Thank you all the same !

---

### Post by xustblb on 2011-05-12
> **mc4man said:**
> Why don't you post your ./configure line (and if inclined complete configure output) and  any other 'changes' if any.
The error, (db2omf: Could not construct the OMF subject element) is not completely unknown

(I don't see this anywhere - xmllint ...
The ./configure line is as the follow


```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu                                                                                                                                   
checking for a sed that does not truncate output... /bin/sed                                                                                                                     
checking for fgrep... /bin/grep -F                                                                                                                                               
checking for ld used by gcc... /usr/bin/ld                                                                                                                                       
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gtkdoc-check... no
checking for gtkdoc-rebase... no
checking for gtkdoc-mkpdf... no
checking whether to build gtk-doc documentation... no
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking gnome-doc-utils >= 0.3.2... yes
checking for UDEV... yes
checking operating system... Linux
checking sys/videoio.h usability... no
checking sys/videoio.h presence... no
checking for sys/videoio.h... no
checking X11/extensions/XTest.h usability... yes
checking X11/extensions/XTest.h presence... yes
checking for X11/extensions/XTest.h... yes
checking for XTestFakeKeyEvent in -lXtst... yes
checking for CHEESE... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: creating ./config.status
config.status: creating Makefile
config.status: creating cheese-gtk.pc
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/version.xml
config.status: creating data/Makefile
config.status: creating data/cheese.desktop.in
config.status: creating data/effects/Makefile
config.status: creating data/icons/Makefile
config.status: creating data/icons/16x16/Makefile
config.status: creating data/icons/22x22/Makefile
config.status: creating data/icons/24x24/Makefile
config.status: creating data/icons/32x32/Makefile
config.status: creating data/icons/48x48/Makefile
config.status: creating data/icons/256x256/Makefile
config.status: creating data/icons/scalable/Makefile
config.status: creating data/icons/16x16/actions/Makefile
config.status: creating data/icons/22x22/actions/Makefile
config.status: creating data/icons/24x24/actions/Makefile
config.status: creating data/icons/32x32/actions/Makefile
config.status: creating data/icons/48x48/actions/Makefile
config.status: creating data/icons/scalable/actions/Makefile
config.status: creating data/pixmaps/Makefile
config.status: creating help/Makefile
config.status: creating libcheese/Makefile
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating po/Makefile.in
config.status: creating cheese-config.h
config.status: cheese-config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
```

---

