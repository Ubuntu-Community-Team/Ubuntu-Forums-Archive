---
title: "Error compiling xchat"
date: 2012-12-15
forum: Packaging and Compiling Programs
---

### Post by Hungry Man on 2012-12-15
/usr/include/glib-2.0/glib/gunicode.h:23:2: error: #error "Only <glib.h> can be included directly."

When I run "make". I get multiple errors like this.

---

### Post by oldos2er on 2012-12-15
Moved to Packaging and Compiling Programs.

---

### Post by mc4man on 2012-12-15
Don't know what source you're using but on xchat Debian/Ubuntu would patch like this - Ex. from xchat-2.8.8
```
--- a/src/common/servlist.c
+++ b/src/common/servlist.c
@@ -24,7 +24,7 @@
 #include <unistd.h>
 
 #include "xchat.h"
-#include <glib/ghash.h>
+#include <glib.h>
 
 #include "cfgfiles.h"
 #include "fe.h"
--- a/src/common/text.c
+++ b/src/common/text.c
@@ -28,7 +28,7 @@
 #include <sys/mman.h>
 
 #include "xchat.h"
-#include <glib/ghash.h>
+#include <glib.h>
 #include "cfgfiles.h"
 #include "chanopt.h"
 #include "plugin.h"
--- a/src/common/util.c
+++ b/src/common/util.c
@@ -39,7 +39,7 @@
 #include <errno.h>
 #include "xchat.h"
 #include "xchatc.h"
-#include <glib/gmarkup.h>
+#include <glib.h>
 #include <ctype.h>
 #include "util.h"
 #include "../../config.h"
--- a/src/common/xchat.h
+++ b/src/common/xchat.h
@@ -1,10 +1,6 @@
 #include "../../config.h"
 
-#include <glib/gslist.h>
-#include <glib/glist.h>
-#include <glib/gutils.h>
-#include <glib/giochannel.h>
-#include <glib/gstrfuncs.h>
+#include <glib.h>
 #include <time.h>			/* need time_t */
 
 #ifndef XCHAT_H
```

---

### Post by Hungry Man on 2012-12-15
I'm using the source from the tarball on their site. What would I patch?

---

### Post by andrew.46 on 2012-12-15
Up near the top of the patch:

```

--- a/src/common/**[COLOR="Red"]servlist.c[/COLOR]**
+++ b/src/common/**[COLOR="Red"]servlist.c[/COLOR]**

```

Open the tarball and have a look at this file. Similar pattern for other files mentioned in this patch, but of course you would simply use *patch* to apply these changes...

---

### Post by Hungry Man on 2012-12-15
Alright, I applied that patch, which seems to have helped. New error...

> libtool: link: gcc -shared  .libs/perl.o   -L/usr/local/lib -L/usr/lib/perl/5.14/CORE -lperl -lm -lpthread -lcrypt -ldl -lrt -lglib-2.0  -Wl,-E -Wl,--export-dynamic -pthread   -pthread -Wl,-soname -Wl,perl.so -o .libs/perl.so
/usr/bin/ld.bfd.real: cannot find -lperl
collect2: error: ld returned 1 exit status
make[4]: *** [perl.la] Error 1
make[4]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins/perl'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins/perl'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/colin/Downloads/xchat-2.8.8'
make: *** [all] Error 2


---

### Post by andrew.46 on 2012-12-15
With regard to dependencies perhaps the easiest way would be to run:

```
sudo apt-get build-dep xchat
```

Not the most elegant way to do it but might make your life easier :)

---

### Post by Hungry Man on 2012-12-15
Hm. I run make install, and it finishes... but it isn't installed.

> installing pt.gmo as /usr/local/share/locale/pt/LC_MESSAGES/xchat.mo
installing ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/xchat.mo
installing sq.gmo as /usr/local/share/locale/sq/LC_MESSAGES/xchat.mo
installing sr.gmo as /usr/local/share/locale/sr/LC_MESSAGES/xchat.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/xchat.mo
installing th.gmo as /usr/local/share/locale/th/LC_MESSAGES/xchat.mo
installing uk.gmo as /usr/local/share/locale/uk/LC_MESSAGES/xchat.mo
installing vi.gmo as /usr/local/share/locale/vi/LC_MESSAGES/xchat.mo
installing zh_CN.gmo as /usr/local/share/locale/zh_CN/LC_MESSAGES/xchat.mo
installing zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/xchat.mo
if test "xchat" = "gettext-tools"; then \
	  /bin/mkdir -p /usr/local/share/gettext/po; \
	  for file in Makefile.in.in remove-potcdate.sin    Makevars.template; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/po/$file; \
	  done; \
	  for file in Makevars; do \
	    rm -f /usr/local/share/gettext/po/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/po'
Making install in intl
make[1]: Entering directory `/home/colin/Downloads/xchat-2.8.8/intl'
if { test "xchat" = "gettext-runtime" || test "xchat" = "gettext-tools"; } \
	   && test 'no' = yes; then \
	  /bin/mkdir -p /usr/local/lib /usr/local/include; \
	  /usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \
	  /bin/sh ../libtool --mode=install \
	    /usr/bin/install -c -m 644 libintl.a /usr/local/lib/libintl.a; \
	  if test "@RELOCATABLE@" = yes; then \
	    dependencies=`sed -n -e 's,^dependency_libs=\(.*\),\1,p' < /usr/local/lib/libintl.la | sed -e "s,^',," -e "s,'\$,,"`; \
	    if test -n "$dependencies"; then \
	      rm -f /usr/local/lib/libintl.la; \
	    fi; \
	  fi; \
	else \
	  : ; \
	fi
if test "xchat" = "gettext-tools" \
	   && test 'no' = no \
	   && test yes != no; then \
	  /bin/mkdir -p /usr/local/lib; \
	  /bin/sh ../libtool --mode=install \
	    /usr/bin/install -c -m 644 libgnuintl.a /usr/local/lib/libgnuintl.a; \
	  rm -f /usr/local/lib/preloadable_libintl.so; \
	  /usr/bin/install -c -m 644 /usr/local/lib/libgnuintl.so /usr/local/lib/preloadable_libintl.so; \
	  /bin/sh ../libtool --mode=uninstall \
	    rm -f /usr/local/lib/libgnuintl.a; \
	else \
	  : ; \
	fi
if test 'no' = yes; then \
	  test yes != no || /bin/mkdir -p /usr/local/lib; \
	  temp=/usr/local/lib/t-charset.alias; \
	  dest=/usr/local/lib/charset.alias; \
	  if test -f /usr/local/lib/charset.alias; then \
	    orig=/usr/local/lib/charset.alias; \
	    sed -f ref-add.sed $orig > $temp; \
	    /usr/bin/install -c -m 644 $temp $dest; \
	    rm -f $temp; \
	  else \
	    if test yes = no; then \
	      orig=charset.alias; \
	      sed -f ref-add.sed $orig > $temp; \
	      /usr/bin/install -c -m 644 $temp $dest; \
	      rm -f $temp; \
	    fi; \
	  fi; \
	  /bin/mkdir -p /usr/local/share/locale; \
	  test -f /usr/local/share/locale/locale.alias \
	    && orig=/usr/local/share/locale/locale.alias \
	    || orig=./locale.alias; \
	  temp=/usr/local/share/locale/t-locale.alias; \
	  dest=/usr/local/share/locale/locale.alias; \
	  sed -f ref-add.sed $orig > $temp; \
	  /usr/bin/install -c -m 644 $temp $dest; \
	  rm -f $temp; \
	else \
	  : ; \
	fi
if test "xchat" = "gettext-tools"; then \
	  /bin/mkdir -p /usr/local/share/gettext/intl; \
	  /usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION; \
	  /usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ChangeLog; \
	  dists="COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin export.h libintl.rc gmo.h gettextP.h hash-string.h loadinfo.h plural-exp.h eval-plural.h localcharset.h lock.h relocatable.h tsearch.h tsearch.c xsize.h printf-args.h printf-args.c printf-parse.h wprintf-parse.h printf-parse.c vasnprintf.h vasnwprintf.h vasnprintf.c os2compat.h libgnuintl.h.in bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c hash-string.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c lock.c relocatable.c langprefs.c localename.c log.c printf.c version.c osdep.c os2compat.c intl-exports.c intl-compat.c"; \
	  for file in $dists; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  chmod a+x /usr/local/share/gettext/intl/config.charset; \
	  dists="plural.c"; \
	  for file in $dists; do \
	    if test -f $file; then dir=.; else dir=.; fi; \
	    /usr/bin/install -c -m 644 $dir/$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c COPYING.LIB-2 gettext.h libgettext.h plural-eval.c libgnuintl.h libgnuintl.h_vms Makefile.vms libgnuintl.h.msvc-static libgnuintl.h.msvc-shared Makefile.msvc"; \
	  for file in $dists; do \
	    rm -f /usr/local/share/gettext/intl/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/intl'
Making install in src
make[1]: Entering directory `/home/colin/Downloads/xchat-2.8.8/src'
Making install in pixmaps
make[2]: Entering directory `/home/colin/Downloads/xchat-2.8.8/src/pixmaps'
make[3]: Entering directory `/home/colin/Downloads/xchat-2.8.8/src/pixmaps'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/src/pixmaps'
make[2]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/src/pixmaps'
Making install in common
make[2]: Entering directory `/home/colin/Downloads/xchat-2.8.8/src/common'
Making install in .
make[3]: Entering directory `/home/colin/Downloads/xchat-2.8.8/src/common'
make[4]: Entering directory `/home/colin/Downloads/xchat-2.8.8/src/common'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/src/common'
make[3]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/src/common'
make[2]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/src/common'
make[2]: Entering directory `/home/colin/Downloads/xchat-2.8.8/src'
make[3]: Entering directory `/home/colin/Downloads/xchat-2.8.8/src'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/src'
make[2]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/src'
make[1]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/src'
Making install in plugins
make[1]: Entering directory `/home/colin/Downloads/xchat-2.8.8/plugins'
Making install in .
make[2]: Entering directory `/home/colin/Downloads/xchat-2.8.8/plugins'
make[3]: Entering directory `/home/colin/Downloads/xchat-2.8.8/plugins'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins'
make[2]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins'
Making install in perl
make[2]: Entering directory `/home/colin/Downloads/xchat-2.8.8/plugins/perl'
make  install-am
make[3]: Entering directory `/home/colin/Downloads/xchat-2.8.8/plugins/perl'
make[4]: Entering directory `/home/colin/Downloads/xchat-2.8.8/plugins/perl'
test -z "/usr/local/lib/xchat/plugins" || /bin/mkdir -p "/usr/local/lib/xchat/plugins"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c   perl.la '/usr/local/lib/xchat/plugins'
libtool: install: /usr/bin/install -c .libs/perl.so /usr/local/lib/xchat/plugins/perl.so
libtool: install: /usr/bin/install -c .libs/perl.lai /usr/local/lib/xchat/plugins/perl.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/sbin" ldconfig -n /usr/local/lib/xchat/plugins
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xchat/plugins

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins/perl'
make[3]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins/perl'
make[2]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins/perl'
make[1]: Leaving directory `/home/colin/Downloads/xchat-2.8.8/plugins'
make[1]: Entering directory `/home/colin/Downloads/xchat-2.8.8'
make[2]: Entering directory `/home/colin/Downloads/xchat-2.8.8'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/pixmaps" || /bin/mkdir -p "/usr/local/share/pixmaps"
 /usr/bin/install -c -m 644 xchat.png '/usr/local/share/pixmaps'
test -z "/usr/local/share/applications" || /bin/mkdir -p "/usr/local/share/applications"
 /usr/bin/install -c -m 644 xchat.desktop '/usr/local/share/applications'
make[2]: Leaving directory `/home/colin/Downloads/xchat-2.8.8'
make[1]: Leaving directory `/home/colin/Downloads/xchat-2.8.8'
root@colinvb:/home/colin/Downloads/xchat-2.8.8# xchat
The program 'xchat' is currently not installed. You can install it by typing:
apt-get install xchat
root@colinvb:/home/colin/Downloads/xchat-2.8.8# /usr/bin/xchat
bash: /usr/bin/xchat: No such file or directory


---

### Post by andrew.46 on 2012-12-15
You have not given your ./configure string which might prove useful but have a look at:

```
sudo find /usr -iname xchat
```

and you may find xchat in /usr/local/bin. BTW perhaps checkinstall might be useful here...

Can I ask why you are compiling xchat?

---

### Post by Hungry Man on 2012-12-15
No important reason. It hasn't been updated in a long time so I was just curious to see if it would run with some security flags. Mostly boredom.

sudo find /usr -iname xchat
/usr/include/xchat
/usr/local/lib/xchat

---

### Post by andrew.46 on 2012-12-16
At the risk of giving you nothing more to work on I have tested the following *single* command and it installs a working version of xchat (copy and paste the whole thing into a terminal):

```

sudo apt-get install build-essential checkinstall && \
sudo apt-get remove xchat && \
sudo apt-get build-dep xchat && \
mkdir -pv $HOME/xchat_build && cd $HOME/xchat_build \
wget http://xchat.org/files/source/2.8/xchat-2.8.8.tar.xz && \
tar xvf xchat-2.8.8.tar.xz && cd xchat-2.8.8 && \
sed -i_bak 's|<glib/.*\.h>|<glib.h>|' src/common/{servlist.c,text.c,util.c,xchat.h} && \
./configure && \
make -j 4 && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/xchat_build" \
   --pkgname xchat --backup=no --deldoc=yes --deldesc=yes --delspec=yes \
   --default --pkgversion 2.8.8-4

```

I guess you can then return and fiddle with the source, adjust options etc as you wish?

---

### Post by mc4man on 2012-12-16
> **Hungry Man said:**
> No important reason. It hasn't been updated in a long time so I was just curious to see if it would run with some security flags. Mostly boredom.

the source hasn't been updated in a long time, 2.8.8 is fairly common in recent Ubuntu releases

As far as your  build - look inside your source folder & see if a binary was built (or look in /usr/local/bin

---

