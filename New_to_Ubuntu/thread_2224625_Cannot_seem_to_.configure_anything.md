---
title: "Cannot seem to ./configure anything"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by mastranios on 2014-05-17
I have been trying to configure a few different packages and have gotten various errors. When trying to install conky i get the following

```

root@mastranios:/home/mastranios/Desktop/conky-1.9.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking how to print strings... printf
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
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
checking how to run the C preprocessor... gcc -E
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
checking whether to build static libraries... yes
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for fopencookie... yes
checking for funopen... no
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
configure: error: required header(s) not found



```

```

mastranios@mastranios:~/Desktop/synapse-0.2.10$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
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
checking for intltool >= 0.35... 0.50.2 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.18.2
checking for XML::Parser... ok
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
checking for catalogs to be installed...  ar be bg ca ca@valencia cs da de el en_GB eo es et eu fi fr gl hi hr hu it ja ka ko la lt lv ml nb nds nl nn oc pl pt pt_BR ro ru sk sw tr uk zh_CN
checking for pkg-config... /usr/bin/pkg-config
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
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
checking whether to build static libraries... yes
checking for ANSI C header files... (cached) yes
checking for valac... /usr/bin/valac
checking /usr/bin/valac is at least version 0.14.0... yes
checking whether make supports nested variables... yes
checking pkg-config is at least version 0.9.0... yes
checking for SYNAPSE_MODULES... no
configure: error: Package requirements (  glib-2.0 >= 2.26.0   gtk+-2.0 >= 2.20.0   gtkhotkey-1.0   gobject-2.0   gee-1.0 >= 0.5.2   gio-unix-2.0   json-glib-1.0 >= 0.10.0   libnotify   unique-1.0   ) were not met:

No package 'gtk+-2.0' found
No package 'gtkhotkey-1.0' found
No package 'gee-1.0' found
No package 'json-glib-1.0' found
No package 'libnotify' found
No package 'unique-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SYNAPSE_MODULES_CFLAGS
and SYNAPSE_MODULES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
mastranios@mastranios:~/Desktop/synapse-0.2.10$ 


```

Have never come across this issue before when trying to configure.

---

### Post by steeldriver on 2014-05-17
Hello and welcome to the forums

I guess you've been lucky! I almost always find missing prerequisite packages whenever I try to build from source (unless the source package maintainers have been very diligent about listing the prerequisites, and I've installed ALL of them before trying to ./configure)

In the first case, it looks like you are missing the ncurses development package(s) - libncurses5-dev and possibly libncursesw5-dev if wide char support is required

In the second case the missing packages are listed explicitly

If you really are using Ubuntu 10.10 then you should plan to upgrade to a supported release.

---

### Post by spynappels on 2014-05-17
Well, the first one complains it cannot find ncurses headers, are you sure that ncurses is there and the headers are where they should be?

The second one gives a long list of packages which are missing, have you tried installing them and seeing if this fixes the issue?

Compiling from source is great if you want to learn how to do it, and if the version you want is not in the repos, but is there another reason why you are not installing things from the repos using aptitude or apt-get?

EDIT: Been ninja'd!

---

### Post by mastranios on 2014-05-17
Thanks for the answers! I am actually using the most recent distro, 10.10 was the recent release when I created this account on the forums.

> The second one gives a long list of packages which are missing, have you  tried installing them and seeing if this fixes the issue?

Compiling from source is great if you want to learn how to do it, and if  the version you want is not in the repos, but is there another reason  why you are not installing things from the repos using aptitude or  apt-get?

I will try installing them now. I mainly wanted to learn how to configure, make, and install them myself, but I am not above getting them from repos or the software center. I will do the above mentioned and report back if it works, if not I'll just grab it from the repo.

---

### Post by monkeybrain20122 on 2014-05-17
You need to install the -dev packages (developemental files) for the headers. So if it say xyz is missing, you would probably need libxyz-dev. synaptic would be handy to search for packages if you don't know the exact names (say it may be libxyz2.1-dev) If you don't have it install it via the Software Centre or "sudo apt-get install synaptic"

---

