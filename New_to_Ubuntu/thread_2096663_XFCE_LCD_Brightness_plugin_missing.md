---
title: "XFCE LCD Brightness plugin missing"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by lumop on 2012-12-20
Ubuntu 12.04 LTS
Memory: 8 Gib
Intel® Core™ i5-2450M CPU @ 2.50GHz × 4
Disk: 500gb

I recently installed XFCE 4.10. The power manager works but there's no LCD brightness plugin. There's no icon or shortcut to adjust brightness. I started following the steps to install the package manager from here [http://goodies.xfce.org/projects/applications/xfce4-power-manager#lcd-brightness-plugin]("http://goodies.xfce.org/projects/applications/xfce4-power-manager#lcd-brightness-plugin") since it comes with the LCD plugin. The command 'make' didn't work.

Out put of '~/Documents/xfce4-power-manager-1.0.10$ ./configure --prefix=/usr --sysconfdir=/etc'
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking how to print strings... printf
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether NLS is requested... yes
checking for intltool >= 0.31... 0.50.2 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.14.2
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ANSI C header files... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for string.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for unistd.h... (cached) yes
checking for round in -lm... yes
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
checking for catalogs to be installed...  ast ca cs da de el en_GB es et eu fi fr gl hu id it ja kk nb nl pa pt_BR pt ru si sk sv tr ug uk ur_PK ur zh_CN
checking for bind_textdomain_codeset... (cached) yes
checking for locales directory... ${datarootdir}/locale
checking for additional xgettext flags... --keyword=Q_ --from-code=UTF-8
checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config >= 0.9.0... 0.26
checking for gtk+-2.0 >= 2.12.0... not found
*** The required package gtk+-2.0 was not found on your system.
*** Please install gtk+-2.0 (atleast version 2.12.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

```

Output of 'make'
```
make: *** No targets specified and no makefile found.  Stop.
```

I just want a shortcut to adjust my brightness. Help much appreciated. Thank you.

---

### Post by pqwoerituytrueiwoq on 2012-12-20
```
sudo apt-get install xfce4-power-manager
```then you can add the applet to the panel

---

### Post by lumop on 2012-12-20
Just did that. There's still no brightness applet to add to the panel.

---

### Post by pqwoerituytrueiwoq on 2012-12-20
```
sudo apt-get install xfce4-power-manager-plugins
```
now why does the other one say it is in it :?

---

### Post by lumop on 2012-12-20
Yay! Got it now. Thanks for the quick response.

---

### Post by cougar4u on 2013-05-06
I've run into the same problem and added the plugins from the repository. Still don't have a brightness plugin. Any ideas? :confused:

[IMG]http://i.imgur.com/bB2eo5v.png[/IMG]

Best Regards

---

