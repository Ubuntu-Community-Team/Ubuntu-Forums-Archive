---
title: "Anjuta won't configure help!"
date: 2007-01-16
forum: Programming Talk
---

### Post by .::welemski::. on 2007-01-16
Hi,

I'm new to Linux programming. I'm using Anjuta IDE version 2.0.2 and Glade 2.12.1.
I have problem in running my App. it shows this error:

configure: error: Package requirements (libgnome-2.0 libgnomeui-2.0 libglade-2.0    ) were not met:

I didn't do anything on my yet except trying to configure a newly created project.
All the required Libraries were installed, I am sure of it. Only that I not so familiar in linux programming. I checked and double checked libgnome-2.0, libgnomeui-2.0, libglade-2.0 all were installed.

I checked the ".pc" for both libraries there were messing. But the lib itself is installed.

Does anyone knows how to solved this problem I have?

Thanks in advance.

---

### Post by NeoLithium on 2007-01-16
How did you install it?  There's a guide at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) that helps resolve some crash issues. Apparently it's pretty picky about how it's installed :)

---

### Post by .::welemski::. on 2007-01-17
Here's how I installed my Anjuta/Glade:

I used the Add/Remove in the Applications menu and checked anjuta and glade.
I just don't seem to understand why i can't configure/build my project.

---

### Post by .::welemski::. on 2007-01-17
Here are the logs:

./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
configure: error: Package requirements (libgnome-2.0 libgnomeui-2.0 libglade-2.0    ) were not met:

No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Completed... unsuccessful
Total time taken: 6 secs

---

### Post by maubp on 2007-01-17
Have you installed the -dev versions of libgnome-2.0 libgnomeui-2.0 libglade-2.0 too?

They are needed if you want to compile anything from source which will use these libs.

---

### Post by .::welemski::. on 2007-01-19
Thanks much guys,
Sorry, not so familiar with linux or any other UNIX except OS X.
Yes, it solves the problem. By installing the dev version of the lib i am able to compile/build my project without any errors.

---

