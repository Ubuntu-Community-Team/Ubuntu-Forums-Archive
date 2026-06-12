---
title: "Installing Florence keyboard?"
date: 2012-02-03
forum: Packaging and Compiling Programs
---

### Post by loganbell45 on 2012-02-03
Hi, I'm having trouble installing Florence keyboard - [http://florence.sourceforge.net/english/install.html](http://florence.sourceforge.net/english/install.html)

When I try and use the code they've supplied for Ubuntu it says I need the dependencies, but when I use the code for the dependencies it says 

Package libpanel-applet2-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgnome-desktop-dev

E: Package 'libpanel-applet2-dev' has no installation candidate

I don't really know where to go from here...

---

### Post by searchfgold6789 on 2012-02-03
Install the package libgnome-desktop-dev and try again.

---

### Post by loganbell45 on 2012-02-03
Awesome - that helped a lot but  now I've come across a new hurdle. After trying the ./configure command it tells me:

checking for DEPS... configure: error: Package requirements (gmodule-2.0 cairo librsvg-2.0 libxml-2.0 gconf-2.0 gtk+-2.0 >= 2.12.0) were not met:

No package 'librsvg-2.0' found
No package 'libxml-2.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

It asked me to install a couple more things which I did, but I'm unable to just apt-get install the packages it mentions...

---

### Post by searchfgold6789 on 2012-02-03
I think the packages you want are: librsvg2-dev libxml2-dev libgconf2-dev

---

### Post by loganbell45 on 2012-02-04
That worked too - but there are more things I need to install, it wants me to install at-spi, which I did, but it still tells me to install it. If I run configure --without-at-spi it tells me to install libgnomeapplet2, but the package that has replaced it (apparently) is already fully updated... I'm trying to do this as independently as possible but I literally have no idea where to go :P

sudo apt-get install libgnome-desktop-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnome-desktop-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
****-Inspiron-1090:~/Downloads/florence-0.5.1$ ./configure
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
checking for intltool >= 0.23... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.12.4
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
checking for catalogs to be installed...  fr ru
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for grep that handles long lines and -e... (cached) /bin/grep
checking for a sed that does not truncate output... /bin/sed
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking whether ln -s works... yes
checking gnome-doc-utils >= 0.3.2... yes
checking for scrollkeeper-config... /usr/bin/scrollkeeper-config
checking for DEPS... yes
checking for GNOME_DOC_UTILS... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.14.0... yes (version 2.24.6)
checking for LIBNOTIFY... yes
checking for LIBNOTIFY_ICON... no
configure: Notification icon disabled.
checking for XTST... yes
checking for AT_SPI2... no
checking for AT_SPI... no
configure: error: Could not configure at-spi. Please either install at-spi or disable it: --without-at-spi configure option
logan@logan-Inspiron-1090:~/Downloads/florence-0.5.1$ sudo apt-get install at-spi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
at-spi is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by oldos2er on 2012-02-04
Thread moved to Packaging and Compiling Programs.

---

### Post by loganbell45 on 2012-02-05
Does anybody know where I'm going wrong? I'd really like to get this working.

Edit: Got it sorted, i did the ./configure thing without at-spi and libgnome (./configure --prefix=/usr --without-at-spi --without-libgnome...) seeing as both the packages where installed i thought it wouldnt make a huge difference, and it didn't. The keyboard is working exactly as described. Thanks for the help searchfgold~

---

### Post by Agrouf on 2012-02-05
You need to install libatspi2.0-dev (on natty or later) or libatspi-dev for previous versions of Ubuntu.
I advise to configure with the --without-panelapplet option. Indeed, the panel applet is pointless as of now.
Use this command:
./configure --prefix=/usr --without-panelapplet

If you disable at-spi, the auto-hide feature of Florence will be disabled.
The auto-hide feature makes the keyboard appear when an editable widget is focused and disappear when it looses the focus.

Note you have to enable auto-hide in the configuration panel of Florence too for it to work.

---

### Post by loganbell45 on 2012-02-05
Oh awesome - thanks! I'll re do the installation tomorrow :)

---

