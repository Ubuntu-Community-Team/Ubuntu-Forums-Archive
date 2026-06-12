---
title: "Trying to compile GTK"
date: 2009-10-07
forum: Programming Talk
---

### Post by Silvernail on 2009-10-07
I am trying to compile the GTK suite. I don't want to use the perl, python, ada stuff so I have not knowingly downloaded any.

Here is where I am. What else do I need to install to get things going?
 
> dave@Dafy:~/phpscripts/php-gtk-2.0.1$ ./buildconf
rebuilding configure
configure.in:77: warning: LTOPTIONS_VERSION is m4_require'd but not m4_defun'd
aclocal.m4:2912: LT_INIT is expanded from...
aclocal.m4:2947: AC_PROG_LIBTOOL is expanded from...
configure.in:77: the top level
configure.in:77: warning: LTSUGAR_VERSION is m4_require'd but not m4_defun'd
configure.in:77: warning: LTVERSION_VERSION is m4_require'd but not m4_defun'd
configure.in:77: warning: LTOBSOLETE_VERSION is m4_require'd but not m4_defun'd
configure:12695: error: possibly undefined macro: m4_ifval
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:16403: error: possibly undefined macro: _LT_SET_OPTIONS
configure:16403: error: possibly undefined macro: LT_INIT
make[1]: *** [configure] Error 1
make: *** [all] Error 2
dave@Dafy:~/phpscripts/php-gtk-2.0.1$

> dave@Dafy:~/phpscripts/php-gtk-2.0.1$ ./configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.12.0 or later if you want to regenerate PHP parsers.
checking for gawk... gawk
checking for PHP-GTK support... yes, shared
checking for PHP executable in /usr/bin... found version 5.2.6-3ubuntu4.2
checking for gawk... (cached) gawk
checking whether to include debugging symbols... no
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.6.0... yes (version 2.20.1)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.6.0... yes (version 2.16.1)
checking for atk >= 1.9.0... yes
checking ATK_CFLAGS... -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking ATK_LIBS... -latk-1.0 -lgobject-2.0 -lglib-2.0  
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
checking for gtkextra support... no
checking for html support... no
checking for libglade support... yes
checking for libglade-2.0 >= 2.4.0... Unable to locate libglade version 2.4.0 or higher: not building
checking for libsexy support... no
checking for GtkMozEmbed support... no
checking for scintilla support... no
checking for sourceview support... no
checking for spell support... no
creating main/php_gtk_ext.c
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
./configure: line 12613: LTOPTIONS_VERSION: command not found
./configure: line 12614: LTSUGAR_VERSION: command not found
./configure: line 12615: LTVERSION_VERSION: command not found
./configure: line 12616: LTOBSOLETE_VERSION: command not found
checking for a sed that does not truncate output... (cached) /bin/sed
./configure: line 12693: syntax error near unexpected token `lt_decl_varnames,'
./configure: line 12693: `lt_if_append_uniq(lt_decl_varnames, SED, , ,'
dave@Dafy:~/phpscripts/php-gtk-2.0.1$ 


---

### Post by januzi on 2009-10-07
[http://ubuntuforums.org/showthread.php?t=1082332](http://ubuntuforums.org/showthread.php?t=1082332)
cd /usr/share/aclocal
cp libtool.m4 libtool.m4.old
cat lt~obsolete.m4 ltoptions.m4 ltsugar.m4 ltversion.m4 >> libtool.m4

and try again

---

### Post by Silvernail on 2009-10-07
> -rw-r--r-- 1 root root 260278 2009-01-16 04:58 libtool.m4

> dave@Dafy:/usr/share/aclocal$ sudo cat lt~obsolete.m4 ltoptions.m4 itsugar.m4 itversion.m4 >> libtool.m4
bash: libtool.m4: Permission denied
dave@Dafy:/usr/share/aclocal$ 


??????????

---

### Post by Silvernail on 2009-10-08
OK. I've worked around that. I opened gedit and copy and pasted everything together.

got a successfull build, I think.

Got to find out what 'make test' means

Thanks for your help.
Dave

---

### Post by wiscalico on 2010-02-18
I've got it compiling an put it in [my PPA]("https://launchpad.net/~jacob-emcken/+archive/ppa/")... for those too lazy to build themselves :)

It is build with the following: --with-extra --with-html --with-libsexy --with-spell --enable-php-gtk --enable-scintilla --with-mozembed

---

