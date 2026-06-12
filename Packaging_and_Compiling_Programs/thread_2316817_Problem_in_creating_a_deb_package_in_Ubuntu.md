---
title: "Problem in creating a deb package in Ubuntu"
date: 2016-03-11
forum: Packaging and Compiling Programs
---

### Post by Anes_P_A on 2016-03-11
Dear Friends,

In my code project (([https://drive.google.com/file/d/0BxE7wbgixC4GX3l4XzRWZTE2UnM/view?usp=sharing](https://drive.google.com/file/d/0BxE7wbgixC4GX3l4XzRWZTE2UnM/view?usp=sharing))  and try to generate deb from it. But I still got some message error . I  could not understand what it ? The content of the build file with name  which show warnig as can see here (dbr_1.0-1_i386.build) : [http://pastie.org/10755815](http://pastie.org/10755815)
The main thread of that message is :

```
dpkg-source: info: local changes detected, the modified files are:
 dbr-1.0.1/po/missing
dpkg-source: error: aborting due to unexpected upstream changes, see /tmp/dbr_1.0-1.diff.M_YVm1
dpkg-source: info: you can integrate the local changes with dpkg-source --commit
dpkg-buildpackage: error: dpkg-source -b dbr-1.0.1 gave error exit status 2
```

The corresponding /tmp/dbr_1.0-1.diff.M_YVm1  file content is:
```

Description: <short summary of the patch>
 TODO: Put a short summary on the line above and replace this paragraph
 with a longer explanation of this change. Complete the meta-information
 with other relevant fields (see below for details). To make it easier, the
 information below has been extracted from the changelog. Adjust it or drop
 it.
 .
 dbr (1.0-1) UNRELEASED; urgency=medium
 .
   * Initial release. (Closes: #XXXXXX)
Author: Insight <info@insight.org.in>

---
The information above should follow the Patch Tagging Guidelines, please
checkout [http://dep.debian.net/deps/dep3/](http://dep.debian.net/deps/dep3/) to learn about the format. Here
are templates for supplementary fields that you might want to add:

Origin: <vendor|upstream|other>, <url of original patch>
Bug: <url in upstream bugtracker>
Bug-Debian: https://bugs.debian.org/<bugnumber>
Bug-Ubuntu: https://launchpad.net/bugs/<bugnumber>
Forwarded: <no|not-needed|url proving that it has been forwarded>
Reviewed-By: <name and email of someone who approved the patch>
Last-Update: <YYYY-MM-DD>

--- /dev/null
+++ dbr-1.0/po/missing
@@ -0,0 +1 @@
+src/controlador.py
```


When I change the debian/source/format contant from 3.0 (quilt) to 3.0 (native) according to the forum post [http://askubuntu.com/questions/226495/how-to-solve-dpkg-source-source-problem-when-building-a-package/353700#353700](http://askubuntu.com/questions/226495/how-to-solve-dpkg-source-source-problem-when-building-a-package/353700#353700)

I got a new message in dbr_1.0-1_i386.build as:

```
[INDENT] dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: source package dbr
dpkg-buildpackage: source version 1.0-1
dpkg-buildpackage: source distribution UNRELEASED
dpkg-buildpackage: source changed by Insight <info@insight.org.in>
 dpkg-source --before-build dbr-1.0.1
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh clean
   dh_testdir
   dh_auto_clean
   dh_clean
 dpkg-source -b dbr-1.0.1
dpkg-source: warning: native package version may not have a revision
dpkg-source: info: using source format '3.0 (native)'
dpkg-source: info: building dbr in dbr_1.0-1.tar.xz
dpkg-source: info: building dbr in dbr_1.0-1.dsc
 debian/rules build
dh build
   dh_testdir
   dh_auto_configure
    ./configure --build=i686-linux-gnu --prefix=/usr  --includedir=\${prefix}/include --mandir=\${prefix}/share/man  --infodir=\${prefix}/share/info --sysconfdir=/etc --localstatedir=/var  --disable-silent-rules --libdir=\${prefix}/lib/i386-linux-gnu  --libexecdir=\${prefix}/lib/i386-linux-gnu --disable-maintainer-mode  --disable-dependency-tracking
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking dependency style of gcc... none
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
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for intltool >= 0.35.0... 0.51.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking for a BSD-compatible install... /usr/bin/install -c
checking for library containing strerror... none required
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/site-packages
checking for headers required to compile python extensions... found
checking for python module gettext... yes
checking for python module getopt... yes
checking for python module pygst... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/dbr
config.status: creating src/dbr_i18n.py
config.status: creating dbr.spec
config.status: creating po/Makefile.in
config.status: creating src/controlador.py
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
   dh_auto_build
    make -j1
make[1]: Entering directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1'
make  all-recursive
make[2]: Entering directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1'
Making all in po
make[3]: Entering directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1/po'
file=`echo es | sed 's,.*/,,'`.gmo \
  && rm -f $file && /usr/bin/msgfmt -o $file es.po
file=`echo gl | sed 's,.*/,,'`.gmo \
  && rm -f $file && /usr/bin/msgfmt -o $file gl.po
make[3]: Leaving directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1/po'
Making all in src
make[3]: Entering directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1/src'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1/src'
make[3]: Entering directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1'
LC_ALL=C /usr/bin/intltool-merge -d -u -c ./po/.intltool-merge-cache ./po dbr.desktop.in dbr.desktop
Generating and caching the translation database
Merging translations into dbr.desktop.
make[3]: Leaving directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1'
make[2]: Leaving directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1'
make[1]: Leaving directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1'
   dh_auto_test
    make -j1 check
make[1]: Entering directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1'
Making check in po
make[2]: Entering directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1/po'
INTLTOOL_EXTRACT=/usr/bin/intltool-extract srcdir=. /usr/bin/intltool-update --gettext-package dbr --pot
rm -f missing notexist
srcdir=. /usr/bin/intltool-update -m
The following files contain translations and are currently not in use. Please
consider adding these to the POTFILES.in file, located in the po/ directory.

src/controlador.py

If some of these files are left out on purpose then please add them to
POTFILES.skip instead of POTFILES.in. A file 'missing' containing this list
of left out files has been written in the current directory.
if [ -r missing -o -r notexist ]; then \
  exit 1; \
fi
Makefile:152: recipe for target 'check' failed
make[2]: *** [check] Error 1
make[2]: Leaving directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1/po'
Makefile:327: recipe for target 'check-recursive' failed
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory '/home/anes/Desktop/DebianTest/dbr/dbr-1.0.1'
dh_auto_test: make -j1 check returned exit code 2
debian/rules:3: recipe for target 'build' failed
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2[/INDENT]

```
Please advise the possible solution...
Waiting for your's fast reply

Thanks
Anes

---

### Post by Irihapeti on 2016-03-11
*Thread moved to **Packaging and Compiling Programs**.*

---

### Post by mc4man on 2016-03-12
Well it has told you what to do (either with quilt & with native) so just do what it says.
Overall if you are using .orig & - in the name you should be using quilt.
In any event there are loads of lintian errors & warnings plus gst-0.10 is being dropped in Debian/Ubuntu, 16.04 likely won't have it so app may have limited use.

(-errors & warnings
> Now running lintian...
E: dbr changes: bad-distribution-in-changes-file stable
W: dbr source: native-package-with-dash-version
E: dbr source: python-depends-but-no-python-helper dbr
W: dbr source: superfluous-clutter-in-homepage <insert the upstream URL, if relevant>
W: dbr source: bad-homepage <insert the upstream URL, if relevant>
W: dbr source: syntax-error-in-dep5-copyright line 156: Continuation line outside a paragraph (maybe line 155 should be " .").
W: dbr: new-package-should-close-itp-bug
E: dbr: copyright-file-contains-full-gpl-license
W: dbr: copyright-has-url-from-dh_make-boilerplate
E: dbr: unknown-priority optioan
W: dbr: superfluous-clutter-in-homepage <insert the upstream URL, if relevant>
W: dbr: bad-homepage <insert the upstream URL, if relevant>
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/ usr/lib/python2.7/dist-packages/dbr/
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/__init__.py usr/lib/python2.7/dist-packages/dbr/__init__.py
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/__init__.pyc
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/__init__.pyc usr/lib/python2.7/dist-packages/dbr/__init__.pyc
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/__init__.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/__init__.pyo usr/lib/python2.7/dist-packages/dbr/__init__.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/controlador.py usr/lib/python2.7/dist-packages/dbr/controlador.py
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/controlador.pyc
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/controlador.pyc usr/lib/python2.7/dist-packages/dbr/controlador.pyc
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/controlador.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/controlador.pyo usr/lib/python2.7/dist-packages/dbr/controlador.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/dbr.py usr/lib/python2.7/dist-packages/dbr/dbr.py
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/dbr.pyc
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/dbr.pyc usr/lib/python2.7/dist-packages/dbr/dbr.pyc
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/dbr.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/dbr.pyo usr/lib/python2.7/dist-packages/dbr/dbr.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/dbr_i18n.py usr/lib/python2.7/dist-packages/dbr/dbr_i18n.py
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/dbr_i18n.pyc
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/dbr_i18n.pyc usr/lib/python2.7/dist-packages/dbr/dbr_i18n.pyc
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/dbr_i18n.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/dbr_i18n.pyo usr/lib/python2.7/dist-packages/dbr/dbr_i18n.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/libro.py usr/lib/python2.7/dist-packages/dbr/libro.py
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/libro.pyc
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/libro.pyc usr/lib/python2.7/dist-packages/dbr/libro.pyc
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/libro.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/libro.pyo usr/lib/python2.7/dist-packages/dbr/libro.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/registro.py usr/lib/python2.7/dist-packages/dbr/registro.py
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/registro.pyc
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/registro.pyc usr/lib/python2.7/dist-packages/dbr/registro.pyc
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/registro.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/registro.pyo usr/lib/python2.7/dist-packages/dbr/registro.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/reproductor.py usr/lib/python2.7/dist-packages/dbr/reproductor.py
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/reproductor.pyc
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/reproductor.pyc usr/lib/python2.7/dist-packages/dbr/reproductor.pyc
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/reproductor.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/reproductor.pyo usr/lib/python2.7/dist-packages/dbr/reproductor.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/vista.py usr/lib/python2.7/dist-packages/dbr/vista.py
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/vista.pyc
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/vista.pyc usr/lib/python2.7/dist-packages/dbr/vista.pyc
E: dbr: package-installs-python-bytecode usr/lib/python2.7/site-packages/dbr/vista.pyo
W: dbr: python-module-in-wrong-location usr/lib/python2.7/site-packages/dbr/vista.pyo usr/lib/python2.7/dist-packages/dbr/vista.pyo
W: dbr: binary-without-manpage usr/bin/dbr
W: dbr: desktop-entry-lacks-main-category usr/share/applications/dbr.desktop

---

### Post by Anes_P_A on 2016-03-12
Dear mc4man and friends,

 So you created deb file of my application ? If so please share that deb with me. So the gstreamer app will not work normally.

 My targeted system is not debian . It's ubuntu only. 

Please reply 

  Thanks 

Anes

---

