---
title: "Trouble with installing programs"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by SillyAce on 2008-09-28
This is the second program to do this, but i followed the install file with Gnome color chooser and it first told me to do "./configure" and this is what came up.

```

james@james-laptop:~/Desktop/gnome-color-chooser-0.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libgnome-2.0 >= 2.16.0  libgnomeui-2.0 >= 2.14.0 libxml-2.0 >= 2.6.0 ) were not met:

No pacjames@james-laptop:~/Desktop/gnome-color-chooser-0.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libgnome-2.0 >= 2.16.0  libgnomeui-2.0 >= 2.14.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

kage 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

The next thing it said to do was to type in "make" and this is what it told me.

```

james@james-laptop:~/Desktop/gnome-color-chooser-0.2.4$ make
make: *** No targets specified and no makefile found.  Stop.

```

im completely lost >_<

---

### Post by Sarah L on 2008-09-29
You should satisfy all the dependencies before you compile a program :]
The configure script stops when it finds a missing dependency. Looks like you're missing the following packages:

No package 'libglademm-2.4' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

Go to the package manager (or use sudo apt-get install from the command line) and install these packages. You'll generally want the ones that end in -dev (the developer packages, for compiling from source).

Then when those are installed, run the configure script again.
Chances are you might run into more dependencies. Repeat the above process until configure finishes without errors.

THEN you should type in make
Be aware that compiling from source takes a while. (Make a sandwich.)
When it's all done, type in sudo make install to install your package, if necessary.

---

### Post by Ocxic on 2008-09-29
also try "sudo apt-get install build-essential"  that will install most of the necessary build utilities for compiling things

---

### Post by SillyAce on 2008-09-29
Thank you so much! =D lol, you guys will prolly be hearing from me often >_< im trying my best to jump on the linux bandwagon. =D

---

