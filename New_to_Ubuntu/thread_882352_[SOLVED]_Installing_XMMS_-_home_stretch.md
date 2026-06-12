---
title: "[SOLVED] Installing XMMS - home stretch"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by ghostypaste on 2008-08-06
Hi. I am having to install XMMS from source. I have gotten past ./configure and make as described in "How to install ANYTHING in Ubuntu." When I do sudo checkinstall the install fails with an error. Here's the output:

```


Installing with make install...

========================= Installation results ===========================
Making install in intl
make[1]: Entering directory `/home/sam/xmms-1.2.11/intl'
if { test "xmms" = "gettext-runtime" || test "xmms" = "gettext-tools"; } \
	   && test 'no' = yes; then \
	  /bin/sh .././mkinstalldirs /usr/local/lib /usr/local/include; \
	  /usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \
	  /bin/sh ../libtool --mode=install \
	    /usr/bin/install -c -m 644 libintl.a /usr/local/lib/libintl.a; \
	  if test "@RELOCATABLE@" = yes; then \
	    dependencies=`sed -n -e 's,^dependency_libs=\(.*\),\1,p' < /usr/local/lib/libintl.la | sed -e "s,^',," -e "s,'\$,,"`; \
	    if test -n "ependencies"; then \
	      rm -f /usr/local/lib/libintl.la; \
	    fi; \
	  fi; \
	else \
	  : ; \
	fi
if test "xmms" = "gettext-tools" \
	   && test 'no' = no; then \
	  /bin/sh .././mkinstalldirs /usr/local/lib; \
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
	  test yes != no || /bin/sh .././mkinstalldirs /usr/local/lib; \
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
	  /bin/sh .././mkinstalldirs /usr/local/share/locale; \
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
if test "xmms" = "gettext-tools"; then \
	  /bin/sh .././mkinstalldirs /usr/local/share/gettext/intl; \
	  /usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION; \
	  /usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ChangeLog; \
	  dists="COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin gmo.h gettextP.h hash-string.h loadinfo.h plural-exp.h eval-plural.h localcharset.h relocatable.h os2compat.h libgnuintl.h.in bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c relocatable.c localename.c log.c osdep.c os2compat.c intl-compat.c"; \
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
	  dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c COPYING.LIB-2 gettext.h libgettext.h plural-eval.c libgnuintl.h"; \
	  for file in $dists; do \
	    rm -f /usr/local/share/gettext/intl/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Leaving directory `/home/sam/xmms-1.2.11/intl'
Making install in libxmms
make[1]: Entering directory `/home/sam/xmms-1.2.11/libxmms'
make[2]: Entering directory `/home/sam/xmms-1.2.11/libxmms'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libxmms.la' '/usr/local/lib/libxmms.la'
/usr/bin/install -c .libs/libxmms.so.1.3.1 /usr/local/lib/libxmms.so.1.3.1
(cd /usr/local/lib && { ln -s -f libxmms.so.1.3.1 libxmms.so.1 || { rm -f libxmms.so.1 && ln -s libxmms.so.1.3.1 libxmms.so.1; }; })
(cd /usr/local/lib && { ln -s -f libxmms.so.1.3.1 libxmms.so || { rm -f libxmms.so && ln -s libxmms.so.1.3.1 libxmms.so; }; })
/usr/bin/install -c .libs/libxmms.lai /usr/local/lib/libxmms.la
/usr/bin/install -c .libs/libxmms.a /usr/local/lib/libxmms.a
chmod 644 /usr/local/lib/libxmms.a
chmod: changing permissions of `/usr/local/lib/libxmms.a': No such file or directory
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/sam/xmms-1.2.11/libxmms'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/sam/xmms-1.2.11/libxmms'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

I'm not sure what my problem is at this point. Some files are missing? I also had the pretty common other problems with this install: glib and gtk+ libraries missing. But this I haven't found out much about. This is Hardy 64-bit, by the way. Ideas?

---

### Post by SunnyRabbiera on 2008-08-06
XMMS is not really supported asnymore to be honest, you are better off trying one of its successors like audacity.

---

### Post by steveneddy on 2008-08-06
I use audacious

Looks like XMMS, but works much better.

XMMS isn't supported anymore.

Audacious is in the repos.

I use audacious daily.

I particularly like streamtuner with audacious.

---

### Post by mevets on 2008-08-06
Just looks like you are missing libxmms. Searching in Synaptic doesnt make it clear which result should be installed. I'd venture to guess its libxmmsclient++1, libxmmsclient2, libxmmsclient-dev, libxmmsclient++-dev, or maybe its the ones that mention glib. I dont know w/o tryign myself.

Or you could
```

sudo apt-get build-dep xmms2

```
This doesnt install xmms2, it just installs the dependencies for xmms2. You might be opposed to this cause you want to build everything including all the dependencies, but I know myself that I usually satisfied with just compiling the program itself.

---

### Post by ghostypaste on 2008-08-06
fair enough

---

### Post by cozmicharlie on 2008-08-06
I know this is marked solved but just in case you get stuck or others reading this may be looking for help, this is an excellent tutorial for installing xmms in Hardy.
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

---

