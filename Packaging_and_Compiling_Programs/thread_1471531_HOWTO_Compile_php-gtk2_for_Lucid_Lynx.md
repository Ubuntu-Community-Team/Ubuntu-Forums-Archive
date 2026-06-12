---
title: "HOWTO: Compile php-gtk2 for Lucid Lynx"
date: 2010-05-03
forum: Packaging and Compiling Programs
---

### Post by martin_lindhe on 2010-05-03
This is a mini-howto i collected from various outdated sources & a little testing.

The php-gtk2 package is currently not provided in the ubuntu repositories, it also depends on the pecl extension cairo.

When finished, you should have php-gtk2 running with php 5.3.

First the dependencies:

```
sudo apt-get install build-essential subversion php5-cli php5-dev libgtk2.0-dev libglade2-dev libcairo2-dev re2c
```

Then install pecl cairo from svn:

```
svn co http://svn.php.net/repository/pecl/cairo/trunk pecl-cairo
cd pecl-cairo
phpize
./configure
make
sudo make install
```

Next, install php-gtk2 from svn:

```
svn co http://svn.php.net/repository/gtk/php-gtk/trunk php-gtk
cd php-gtk
./buildconf
./configure
make
sudo make install
```

Assuming all went well, configure the extensions to load with php5-cli.

IMPORTANT: in Ubuntu Lucid, /etc/php5/cli/conf.d/ and /etc/php5/apache2/conf.d/ is symlinks to /etc/php5/conf.d/
This means that if you install php_gtk2 in this directory, it will also load when php is ran from Apache,
causing server to crash. php_gtk2 is only meant to be run from the cli.

So first remove the symlink, make a ordinary cli/conf.d/ directory and copy the .ini files there:

```

sudo rm /etc/php5/cli/conf.d
sudo mkdir /etc/php5/cli/conf.d
sudo cp /etc/php5/conf.d/*.ini /etc/php5/cli/conf.d/

```

Then install php_gt2k + cairo extensions:

```

echo "extension=/usr/lib/php5/20090626/php_gtk2.so" | sudo tee /etc/php5/cli/conf.d/php_gtk2.ini
echo "extension=/usr/lib/php5/20090626/cairo.so" | sudo tee /etc/php5/cli/conf.d/cairo.ini
```


Finally, verify they load correctly

```
php -m | grep php-gtk
```

Good luck!

EDIT: fixes as suggested by Compyx

---

### Post by Compyx on 2010-05-04
Nice one! I finally got php-gtk working thanks to this howto.

A few comments:

You have a typo in your command to install the dependencies, it should read:
```

sudo apt-get install build-essential subversion php5-cli php5-dev libgtk2.0-dev libglade2-dev libcairo2-dev re2c

```
you had an 'l' too many in 'llibglade2-dev' and an 'l' too few in 'ibcairo2-dev'.

Echoing with sudo and IO-redirection doesn't work:
```

sudo echo "extension=/usr/lib/php5/20090626/php_gtk2.so" > /etc/php5/conf.d/php_gtk2.ini
bash: /etc/php5/conf.d/php_gtk2.ini: Permission denied

```

This can be fixed by running the command in a new shell:
```

sudo bash -c 'echo "extension=/usr/lib/php5/20090626/php_gtk2.so" > /etc/php5/conf.d/php_gtk2.ini'

```

With these fixes php-gtk installed fine. :)

---

### Post by martin_lindhe on 2010-05-04
> **Compyx said:**
> A few comments:

Thanks for your feedback! I updated the orginal post to reflect your suggestions

---

### Post by Bachstelze on 2010-05-04
> **Compyx said:**
> 
Echoing with sudo and IO-redirection doesn't work:
```

sudo echo "extension=/usr/lib/php5/20090626/php_gtk2.so" > /etc/php5/conf.d/php_gtk2.ini
bash: /etc/php5/conf.d/php_gtk2.ini: Permission denied

```

This can be fixed by running the command in a new shell:
```

sudo bash -c 'echo "extension=/usr/lib/php5/20090626/php_gtk2.so" > /etc/php5/conf.d/php_gtk2.ini'

```

Or even better, using [font=monospace]tee[/font], that's what it's for:

```
echo "extension=/usr/lib/php5/20090626/php_gtk2.so" | sudo tee /etc/php5/conf.d/php_gtk2.ini
```

---

### Post by martin_lindhe on 2010-05-04
> **Bachstelze said:**
> Or even better, using [font=monospace]tee[/font], that's what it's for

even better, thanks!

---

### Post by magicbuntu on 2010-05-08
I've installed Ubuntu 10.04 (Lucid Lynx) Desktop and followed this howto. But when I test my PHP GTK installation by typing "sudo make test" after "sudo make", every test will fail.

During the installation I can't see anything going wrong...

Any ideas?


I installed both packages to /opt.

---

### Post by -VladV- on 2010-05-08
> **magicbuntu said:**
> I've installed Ubuntu 10.04 (Lucid Lynx) Desktop and followed this howto. But when I test my PHP GTK installation by typing &quot;sudo make test&quot; after &quot;sudo make&quot;, every test will fail.

During the installation I can't see anything going wrong...
  On my machine all the tests fail as well, however, the installation goes fine and PHP GTK actually works.  So, I assume, something is wrong with the test suite itself.

---

### Post by Compyx on 2010-05-09
All tests failed with my install too, but php-gtk worked. Unfortunately I had to disable the extensions because none of my local websites would display anything with them enabled. In /var/log/apache2/error.log I noticed messages like these:
```

(page=mail&action=test:1238): GLib-GObject-CRITICAL **: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
(index.php:1239): GLib-GObject-CRITICAL **: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed

```

I'm guessing not everything is working as it should. When compiling php-gtk I noticed some nasty compiler warnings about integers and pointers having different sizes and functions expecting pointers but getting integers, so perhaps php-gtk isn't 64-bit ready or not including the proper headers. I'll try to look into those issues when I can find the time.

---

### Post by martin_lindhe on 2010-05-10
> **Compyx said:**
> All tests failed with my install too, but php-gtk worked. Unfortunately I had to disable the extensions because none of my local websites would display anything with them enabled. In /var/log/apache2/error.log I noticed messages like these:
```

(page=mail&action=test:1238): GLib-GObject-CRITICAL **: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
(index.php:1239): GLib-GObject-CRITICAL **: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed

```

I'm guessing not everything is working as it should. When compiling php-gtk I noticed some nasty compiler warnings about integers and pointers having different sizes and functions expecting pointers but getting integers, so perhaps php-gtk isn't 64-bit ready or not including the proper headers. I'll try to look into those issues when I can find the time.

Hello, I updated the first post with explanation & instructions how to install php_gtk2 for php5-cli only.
Your problem is the symlink that ubuntu has installed between apache's php extensions and php-cli extensions, so apache loads the php_gtk2 extension and crashes.
php5_gtk2 can of course not run from the webserver

---

### Post by Compyx on 2010-05-10
> **martin_lindhe said:**
> Hello, I updated the first post with explanation & instructions how to install php_gtk2 for php5-cli only.
Your problem is the symlink that ubuntu has installed between apache's php extensions and php-cli extensions, so apache loads the php_gtk2 extension and crashes.
php5_gtk2 can of course not run from the webserver

After removing the symlink and creating a cli/conf.d directory everything works as expected. Thanks!

---

### Post by farruinn on 2010-05-17
Thanks for posting this and getting me past those annoying build errors.  Has anyone tried building using --with-mozembed or --with-html?  I see directories for gtkhtml and mozembed in the ext directory, but when I run configure it says gtkhtml not found.  I installed libgtkhtml3.14-dev but it still says not found.  Does anyone know a solution for this?

EDIT: found the solution for this myself:

Install libgtkhtml3.14-dev, then edit php-gtk/configure and change every reference of libgtkhtml-3.8 to libgtkhtml-3.14 and voila!

---

### Post by nickcloy on 2010-05-26
when i try this it works fine until trying to make php-gtk where i get the error

```
/home/nick/src/php-gtk/main/phpg_support.c: In function ‘phpg_read_property’:
/home/nick/src/php-gtk/main/phpg_support.c:66: error: too many arguments to function ‘zend_get_std_object_handlers()->read_property’
/home/nick/src/php-gtk/main/phpg_support.c: In function ‘phpg_write_property’:
/home/nick/src/php-gtk/main/phpg_support.c:105: error: too many arguments to function ‘zend_get_std_object_handlers()->write_property’
/home/nick/src/php-gtk/main/phpg_support.c: In function ‘phpg_get_property_ptr_ptr’:
/home/nick/src/php-gtk/main/phpg_support.c:147: error: too many arguments to function ‘zend_get_std_object_handlers()->get_property_ptr_ptr’
make: *** [main/phpg_support.lo] Error 1
```i currently using php version 5.3.2-1ubuntu4, is this the right version? any help would be greatly appreaciated

---

### Post by skeetre on 2010-05-30
I have the same error. 

I tried following these instructions: [http://wiki.birth-online.de/_export/pdf/know-how/software/linux/compiling-php-gtk](http://wiki.birth-online.de/_export/pdf/know-how/software/linux/compiling-php-gtk)

---

### Post by nickcloy on 2010-05-31
after chatting to some very helpful people on irc this problem has been solved, the problem was in recent changes made to the source code, but it works again now

---

### Post by gu4rdi4n on 2010-05-31
hi,

after following the speps in first post, i'll get:

```

PHP Warning:  PHP Startup: php-gtk: Unable to initialize module
Module compiled with module API=20060613
PHP    compiled with module API=20090626
These options need to match
 in Unknown on line 0

```

it doesn't look like anyone else is getting this,
so i must have done something wrong, but what?

```

PHP 5.2.12 (cli) (built: Feb 15 2010 17:04:13) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2009 Zend Technologies

```

I would be pleased if someone can help me solving this.

---

### Post by nickcloy on 2010-05-31
it seems to me that php-gtk is needs a more recent version of php than the one you have

php-gtk 200_**60613**_
php        200**_90626_**

you say you are using php version 5.2.12, this post is for lucid lynx (ubuntu 10.04 lts) which comes with a newer version (5.3.2-1ubuntu4.2)

which version of ubuntu are you running?

---

### Post by gu4rdi4n on 2010-05-31
WTF, my paket-manager is lying to me:

```

azubi@azubi-desktop:~$ dpkg -l | grep php5
ii  libapache2-mod-php5                        5.3.2-1ubuntu4.2                                         server-side, HTML-embedded scripting languag
ii  php5                                       5.3.2-1ubuntu4.2                                         server-side, HTML-embedded scripting languag
ii  php5-cli                                   5.3.2-1ubuntu4.2                                         command-line interpreter for the php5 script
ii  php5-common                                5.3.2-1ubuntu4.2                                         Common files for packages built from the php
ii  php5-curl                                  5.3.2-1ubuntu4.2                                         CURL module for php5
ii  php5-dev                                   5.3.2-1ubuntu4.2                                         Files for PHP5 module development
ii  php5-gd                                    5.3.2-1ubuntu4.2                                         GD module for php5
ii  php5-gtk2                                  0.11                                                     GTK2 support for PHP5.
ii  php5-mcrypt                                5.3.2-0ubuntu1                                           MCrypt module for php5
ii  php5-mysql                                 5.3.2-1ubuntu4.2                                         MySQL module for php5
ii  php5-pgsql                                 5.3.2-1ubuntu4.2                                         PostgreSQL module for php5
ii  php5-sqlite                                5.3.2-1ubuntu4.2                                         SQLite module for php5
ii  php5-xdebug                                2.0.5-1ubuntu1                                           Xdebug Module for PHP 5
azubi@azubi-desktop:~$ php --version
PHP 5.2.12 (cli) (built: Feb 15 2010 17:04:13) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2009 Zend Technologies
azubi@azubi-desktop:~$

```

dpkg tells me that 5.3.2 is installed, but php itself tells me its 5.2.12

Reinstalling the package did not changed anything, What now?

EDIT:

i've found a solution:

the binarys under /usr/local/bin/php* were 5.2.12,
while the binarys under /ust/bin are 5.3.2

and the binarys unter /usr/local/bin/php* are called, because
in $PATH /usr/local/bin was before /usr/bin

linking the binarys from /usr/bin to /usr/local/bin solved the Problem.
PHP-GTK is now running fine.

Thanks for the help.

---

### Post by skeetre on 2010-06-01
> **nickcloy said:**
> after chatting to some very helpful people on irc this problem has been solved, the problem was in recent changes made to the source code, but it works again now

Cool, thanks! I'll try again when I get home.

---

### Post by ghanslet on 2010-06-08
[B]nickcloy,

how did u get rid of the error ?
[/B]

---

### Post by syngiun on 2010-06-11
Followed instructions up to here:

svn co [http://svn.php.net/repository/gtk/php-gtk/trunk](http://svn.php.net/repository/gtk/php-gtk/trunk) php-gtk
cd php-gtk
./buildconf

I got the following error:

configure.in:150: warning: LTOPTIONS_VERSION is m4_require'd but not m4_defun'd
aclocal.m4:2941: LT_INIT is expanded from...
aclocal.m4:2976: AC_PROG_LIBTOOL is expanded from...
configure.in:150: the top level
configure.in:150: warning: LTSUGAR_VERSION is m4_require'd but not m4_defun'd
configure.in:150: warning: LTVERSION_VERSION is m4_require'd but not m4_defun'd
configure.in:150: warning: LTOBSOLETE_VERSION is m4_require'd but not m4_defun'd
configure:11721: error: possibly undefined macro: m4_ifval
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:14749: error: possibly undefined macro: _LT_SET_OPTIONS
configure:14749: error: possibly undefined macro: LT_INIT
make[1]: *** [configure] Error 1
make: *** [all] Error 2

Then followed this post to add macros:
[http://ubuntuforums.org/showthread.php?t=1377395](http://ubuntuforums.org/showthread.php?t=1377395)

$cat /usr/share/aclocal/ltoptions.m4 /usr/share/aclocal/ltversion.m4 /usr/share/aclocal/ltsugar.m4 /usr/share/aclocal/lt~obsolete.m4 >>aclocal.m4

Then ./buildconf went well

I'm running Mint 9, however I have had the same issue on clean ubuntu 10.04. 

I suggest the OP ad this as a possibly necessary step. Thanks for the guide...

---

### Post by Frankie6502 on 2010-06-18
Hi firstly thank you for the guide. I have managed to install PHP-GTK on my intel based machine at home, however I am having major trouble installing it on a amd64 machine at work.

I can successfully run ./build

how ever when I run ./configure I get the following :- 


```
frankie@frankie-desktop:~/Downloads/php-gtk-2.0.1$ ./configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
./configure: line 3427: s/.*>//: No such file or directory
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20090626
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... re2c
checking for re2c version... 0.13.5 (ok)
checking for gawk... gawk
checking for PHP-GTK support... yes, shared
checking for PHP executable in /usr/bin... found version 5.3.2-1ubuntu4.2
checking for gawk... (cached) gawk
checking whether to include debugging symbols... no
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.6.0... yes (version 2.24.1)
./configure: line 4210: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4210: s/[^a-zA-Z0-9]/_/g: No such file or directory
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.6.0... yes (version 2.20.1)
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4602: s/[^a-zA-Z0-9]/_/g: No such file or directory
checking for atk >= 1.9.0... yes
checking ATK_CFLAGS... -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking ATK_LIBS... -pthread -latk-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
./configure: line 4832: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4832: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 4832: s/[^a-zA-Z0-9]/_/g: No such file or directory
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -pthread -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
./configure: line 5059: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 5059: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 5059: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 5395: -e: command not found
checking for gtkextra support... no
checking for html support... no
checking for libglade support... yes
checking for libglade-2.0 >= 2.4.0... yes
checking LIBGLADE_CFLAGS... -pthread -D_REENTRANT -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12  
checking LIBGLADE_LIBS... -pthread -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 6782: s/[^a-zA-Z0-9]/_/g: No such file or directory
./configure: line 7208: -e: command not found
checking for libsexy support... no
checking for GtkMozEmbed support... no
checking for scintilla support... no
checking for sourceview support... no
checking for spell support... no
./configure: line 10849: s#@ext_builddir@#.#g: command not found
./configure: line 10849: s#@ext_srcdir@#/home/frankie/Downloads/php-gtk-2.0.1#g: No such file or directory
./configure: line 11198: -e: command not found
creating main/php_gtk_ext.c
./configure: line 11217: AC_PROG_LIBTOOL: command not found
configure: creating ./config.status
config.status: creating config.h
config.status: config.h is unchanged
```

Can anyone please help!?

---

### Post by Frankie6502 on 2010-06-18
Ok I've tried a slightly different approach:-

Installed the latest version of libtool found here:- [http://ftp.gnu.org/gnu/libtool/libtool-2.2.8.tar.gz]("http://ftp.gnu.org/gnu/libtool/libtool-2.2.8.tar.gz.")

Next removed my old php-gtk installation directory and then created a new one by extracting php-gtk-2.0.1.tar again.

Ran this:-
```
cat /usr/share/aclocal/ltoptions.m4 /usr/share/aclocal/ltversion.m4 /usr/share/aclocal/ltsugar.m4 /usr/share/aclocal/lt~obsolete.m4 >> aclocal.m4
```

Then ran ./build which worked.
./configure also worked!

However when I tried make i get the following: -

```
/bin/bash /home/frankie/Downloads/php-gtk-2.0.1/libtool --mode=compile cc  -Iext/gtk+/ -I/home/frankie/Downloads/php-gtk-2.0.1/ext/gtk+/ -DPHP_ATOM_INC -I/home/frankie/Downloads/php-gtk-2.0.1/include -I/home/frankie/Downloads/php-gtk-2.0.1/main -I/home/frankie/Downloads/php-gtk-2.0.1 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/libglade-2.0 -I/usr/include/libxml2  -DHAVE_CONFIG_H  -g -O2   -c ext/gtk+/gen_atk.c -o ext/gtk+/gen_atk.lo 
libtool: compile:  cc -Iext/gtk+/ -I/home/frankie/Downloads/php-gtk-2.0.1/ext/gtk+/ -DPHP_ATOM_INC -I/home/frankie/Downloads/php-gtk-2.0.1/include -I/home/frankie/Downloads/php-gtk-2.0.1/main -I/home/frankie/Downloads/php-gtk-2.0.1 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/libglade-2.0 -I/usr/include/libxml2 -DHAVE_CONFIG_H -g -O2 -c ext/gtk+/gen_atk.c  -fPIC -DPIC -o ext/gtk+/.libs/gen_atk.o
ext/gtk+/gen_atk.c:272: error: duplicate ‘static’
ext/gtk+/gen_atk.c:277: error: duplicate ‘static’
ext/gtk+/gen_atk.c:282: error: duplicate ‘static’
ext/gtk+/gen_atk.c:287: error: duplicate ‘static’
ext/gtk+/gen_atk.c:292: error: duplicate ‘static’
ext/gtk+/gen_atk.c:298: error: duplicate ‘static’
ext/gtk+/gen_atk.c:303: error: duplicate ‘static’
ext/gtk+/gen_atk.c:308: error: duplicate ‘static’
ext/gtk+/gen_atk.c:313: error: duplicate ‘static’
ext/gtk+/gen_atk.c:318: error: duplicate ‘static’
ext/gtk+/gen_atk.c:440: error: duplicate ‘static’
ext/gtk+/gen_atk.c:445: error: duplicate ‘static’
ext/gtk+/gen_atk.c:722: error: duplicate ‘static’
ext/gtk+/gen_atk.c:727: error: duplicate ‘static’
ext/gtk+/gen_atk.c:732: error: duplicate ‘static’
ext/gtk+/gen_atk.c:737: error: duplicate ‘static’
ext/gtk+/gen_atk.c:742: error: duplicate ‘static’
ext/gtk+/gen_atk.c:747: error: duplicate ‘static’
ext/gtk+/gen_atk.c:791: error: duplicate ‘static’
ext/gtk+/gen_atk.c:829: error: duplicate ‘static’
ext/gtk+/gen_atk.c:923: error: duplicate ‘static’
ext/gtk+/gen_atk.c:929: error: duplicate ‘static’
ext/gtk+/gen_atk.c:934: error: duplicate ‘static’
ext/gtk+/gen_atk.c:999: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1147: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1152: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1157: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1162: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1167: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1172: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1341: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1346: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1351: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1356: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1361: error: duplicate ‘static’
ext/gtk+/gen_atk.c:1366: error: duplicate ‘static’
make: *** [ext/gtk+/gen_atk.lo] Error 1
```

Any ideas??

---

### Post by Frankie6502 on 2010-06-18
[SOLVED!]

Finally fixed this and got it to install on my amd64 machine.

Looks like the trunk version does not have this issue.

The following did the trick!

```
svn co http://svn.php.net/repository/gtk/php-gtk/trunk php-gtk
cd php-gtk

cat /usr/share/aclocal/ltoptions.m4 /usr/share/aclocal/ltversion.m4 /usr/share/aclocal/ltsugar.m4 /usr/share/aclocal/lt~obsolete.m4 >> aclocal.m4

./buildconf
./configure
make
sudo make install
```

:p

---

### Post by justken on 2010-07-11
Worked for me too - thanks everybody

Ken

---

### Post by az_kamran on 2011-02-09
Hi everyone! I followed the guide and everything went good until **./configure** command in  **php-gtk** folder. 
My OS is Ubuntu 10.10 64bit- the Maverick Meerkat , Amd64.
I get this message: 

```
user@ubuntu:~/Downloads/pecl-cairo$ cd ../php-gtk
user@ubuntu:~/Downloads/php-gtk$ ./buildconf
user@ubuntu:~/Downloads/php-gtk$ ./configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20090626
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... re2c
checking for re2c version... 0.13.5 (ok)
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for PHP-GTK support... yes, shared
checking for PHP executable... found version 5.3.3-1ubuntu9.3
checking for gawk... (cached) nawk
checking whether to include debugging symbols... no
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.6.0... yes (version 2.26.0)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.6.0... yes (version 2.22.0)
checking for atk >= 1.9.0... yes
checking ATK_CFLAGS... -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking ATK_LIBS... -pthread -latk-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -pthread -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for cairo >= 1.4.0... yes
checking CAIRO_CFLAGS... -pthread -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking CAIRO_LIBS... -lcairo  
checking for cairo php extension... yes
checking for gtkextra support... no
checking for html support... no
checking for libglade support... yes
checking for libglade-2.0 >= 2.4.0... yes
checking LIBGLADE_CFLAGS... -pthread -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking LIBGLADE_LIBS... -pthread -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpng12 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for libsexy support... no
checking for GtkMozEmbed support... no
checking for scintilla support... no
checking for sourceview support... no
checking for spell support... no
creating main/php_gtk_ext.c
./configure: line 12056: LTOPTIONS_VERSION: command not found
./configure: line 12057: LTSUGAR_VERSION: command not found
./configure: line 12058: LTVERSION_VERSION: command not found
./configure: line 12059: LTOBSOLETE_VERSION: command not found
checking for a sed that does not truncate output... (cached) /bin/sed
./configure: line 12134: syntax error near unexpected token `lt_decl_varnames,'
./configure: line 12134: `lt_if_append_uniq(lt_decl_varnames, SED, , ,'
user@ubuntu:~/Downloads/php-gtk$ ^C
user@ubuntu:~/Downloads/php-gtk$ make
make: *** No targets specified and no makefile found.  Stop.
user@ubuntu:~/Downloads/php-gtk$ make install
make: *** No rule to make target `install'.  Stop.
user@ubuntu:~/Downloads/php-gtk$ ./configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20090626
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... re2c
checking for re2c version... 0.13.5 (ok)
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for PHP-GTK support... yes, shared
checking for PHP executable... found version 5.3.3-1ubuntu9.3
checking for gawk... (cached) nawk
checking whether to include debugging symbols... no
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.6.0... yes (version 2.26.0)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.6.0... yes (version 2.22.0)
checking for atk >= 1.9.0... yes
checking ATK_CFLAGS... -pthread -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking ATK_LIBS... -pthread -latk-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -pthread -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for cairo >= 1.4.0... yes
checking CAIRO_CFLAGS... -pthread -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking CAIRO_LIBS... -lcairo  
checking for cairo php extension... yes
checking for gtkextra support... no
checking for html support... no
checking for libglade support... yes
checking for libglade-2.0 >= 2.4.0... yes
checking LIBGLADE_CFLAGS... -pthread -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking LIBGLADE_LIBS... -pthread -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpng12 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for libsexy support... no
checking for GtkMozEmbed support... no
checking for scintilla support... no
checking for sourceview support... no
checking for spell support... no
creating main/php_gtk_ext.c
./configure: line 12056: LTOPTIONS_VERSION: command not found
./configure: line 12057: LTSUGAR_VERSION: command not found
./configure: line 12058: LTVERSION_VERSION: command not found
./configure: line 12059: LTOBSOLETE_VERSION: command not found
checking for a sed that does not truncate output... (cached) /bin/sed
./configure: line 12134: syntax error near unexpected token `lt_decl_varnames,'
./configure: line 12134: `lt_if_append_uniq(lt_decl_varnames, SED, , ,'

```How can i fix it? :confused:  
Thank in advance.

---

### Post by Quadunit404 on 2011-02-09
[IMG]http://i563.photobucket.com/albums/ss76/Quadunit404/threadnecromancer.jpg[/IMG]

---

### Post by teresaejunior on 2011-04-02
@az_kamram, did you get anything? same problem here. The fix the other guys pointed don't work anymore...

---

### Post by Mutikasa on 2011-12-15
ok, everything went great after four hours compiling.
now, what, how do I start coding and running?
I know only for server. never did cli

---

### Post by teresaejunior on 2011-12-16
Save the following in a file called 'whatever.php':

```
<?php
if (!class_exists('gtk')) {
    die("Please load the php-gtk2 module in your php.ini\r\n");
}
 
$wnd = new GtkWindow();
$wnd->set_title('Hello world');
$wnd->connect_simple('destroy', array('gtk', 'main_quit'));
 
$lblHello = new GtkLabel("Just wanted to say\r\n'Hello world!'");
$wnd->add($lblHello);
 
$wnd->show_all();
Gtk::main();
?>
```

And then run:

```
php /path/to/whatever.php
```

Or you can do as in a shell script, making the file executable and adding to the top of the file:

```
#!/usr/bin/php
```And then running the file as an executable.


Follow the php tutorial :) [http://gtk.php.net/manual/en/tutorials.helloworld.php](http://gtk.php.net/manual/en/tutorials.helloworld.php)

---

### Post by Mutikasa on 2011-12-17
tnx, but now I upgraded to 11.10 and is not working.
This is the message:

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/php_gtk2.so' - libffi.so.5: cannot open shared object file: No such file or directory in Unknown on line 0
Please load the php-gtk2 module in your php.ini
```

this is madness, i have so much problems in last few days

---

### Post by teresaejunior on 2011-12-17
Newer versions of Ubuntu come with libffi.so.6, not 5, so I guess you need to compile php-gtk again...

---

### Post by Mutikasa on 2011-12-17
do I need to make any preparations or just run ./configure make install again?

---

### Post by teresaejunior on 2011-12-17
Running a "make clean" before "./configure" should be enough, though some clean targets may be badly written... So if "make clean" is not enough and you find any troubles, you could download a clean source from svn again to avoid more hassle.

---

