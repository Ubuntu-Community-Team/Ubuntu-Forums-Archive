---
title: "KDevelop - Program in C++"
date: 2007-10-31
forum: Programming Talk
---

### Post by Code_Red on 2007-10-31
when I try Build the project i have this message

This Makefile is only for the CVS repository
This will be deleted before making the distribution
<br />
./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

---

### Post by ilsd on 2007-10-31
more info

---

### Post by dataw0lf on 2007-10-31
Do you have autotools installed?

---

### Post by Paul820 on 2007-10-31
It tells you what is wrong right here
> *** KDE requires autoconf 2.53 or newer

---

### Post by dataw0lf on 2007-10-31
> **Paul820 said:**
> It tells you what is wrong right here

Well, no, it tells him what's wrong right here:

> *** AUTOCONF NOT FOUND!.

So he needs to install autoconf (which used to reside in the autotools package, but it looks like it is in it's own package now -- predictably named "autoconf").

---

### Post by Paul820 on 2007-10-31
There is no need for nitpicking. I showed him/her that line because autoconf 2.53 or newer is required, therefore that is the error.

---

### Post by Code_Red on 2007-10-31
I tried configure using de Synaptic Package manager but when i make de project is de same error.


I tried install install the autoconf-2.61 using:

./configure --prefix=/usr && make && make install

[SIZE="1"]sudo ./configure --prefix=/usr && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether /bin/sh -n is known to work... no
checking for expr... /usr/bin/expr
checking for gm4... no
checking for gnum4... no
checking for m4... /usr/bin/m4
checking whether m4 supports frozen files... yes
checking how m4 supports trace files... --debugfile
checking for perl... /usr/bin/perl
checking for emacs... no
checking for xemacs... no
checking for emacs... no
checking where .elc files should go... ${datadir}/emacs/site-lisp
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
configure: creating ./config.status
config.status: creating tests/Makefile
config.status: creating tests/atlocal
config.status: creating man/Makefile
config.status: creating lib/emacs/Makefile
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating lib/Makefile
config.status: creating lib/Autom4te/Makefile
config.status: creating lib/autoscan/Makefile
config.status: creating lib/m4sugar/Makefile
config.status: creating lib/autoconf/Makefile
config.status: creating lib/autotest/Makefile
config.status: creating bin/Makefile
config.status: executing tests/atconfig commands
Making all in bin
make[1]: Entering directory `/home/code-red/Desktop/autoconf-2.61/bin'
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
rm -f autom4te autom4te.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@M4_DEBUGFILE[@]|--debugfile|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from autom4te.in; do not edit by hand.|g' `test -f ./autom4te.in || echo ./`autom4te.in >autom4te.tmp
chmod +x autom4te.tmp
chmod a-w autom4te.tmp
mv autom4te.tmp autom4te
autom4te_perllibdir='..'/lib AUTOM4TE_CFG='../lib/autom4te.cfg'         ../bin/autom4te -B '..'/lib -B '..'/lib         --language M4sh --cache '' --melt ./autoconf.as -o autoconf.in
rm -f autoconf autoconf.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@M4_DEBUGFILE[@]|--debugfile|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from autoconf.in; do not edit by hand.|g' `test -f ./autoconf.in || echo ./`autoconf.in >autoconf.tmp
chmod +x autoconf.tmp
chmod a-w autoconf.tmp
mv autoconf.tmp autoconf
rm -f autoheader autoheader.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@M4_DEBUGFILE[@]|--debugfile|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from autoheader.in; do not edit by hand.|g' `test -f ./autoheader.in || echo ./`autoheader.in >autoheader.tmp
chmod +x autoheader.tmp
chmod a-w autoheader.tmp
mv autoheader.tmp autoheader
rm -f autoreconf autoreconf.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@M4_DEBUGFILE[@]|--debugfile|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from autoreconf.in; do not edit by hand.|g' `test -f ./autoreconf.in || echo ./`autoreconf.in >autoreconf.tmp
chmod +x autoreconf.tmp
chmod a-w autoreconf.tmp
mv autoreconf.tmp autoreconf
rm -f ifnames ifnames.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@M4_DEBUGFILE[@]|--debugfile|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from ifnames.in; do not edit by hand.|g' `test -f ./ifnames.in || echo ./`ifnames.in >ifnames.tmp
chmod +x ifnames.tmp
chmod a-w ifnames.tmp
mv ifnames.tmp ifnames
rm -f autoscan autoscan.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@M4_DEBUGFILE[@]|--debugfile|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from autoscan.in; do not edit by hand.|g' `test -f ./autoscan.in || echo ./`autoscan.in >autoscan.tmp
chmod +x autoscan.tmp
chmod a-w autoscan.tmp
mv autoscan.tmp autoscan
rm -f autoupdate autoupdate.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@M4_DEBUGFILE[@]|--debugfile|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from autoupdate.in; do not edit by hand.|g' `test -f ./autoupdate.in || echo ./`autoupdate.in >autoupdate.tmp
chmod +x autoupdate.tmp
chmod a-w autoupdate.tmp
mv autoupdate.tmp autoupdate
make[1]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/bin'
Making all in .
make[1]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
Making all in lib
make[1]: Entering directory `/home/code-red/Desktop/autoconf-2.61/lib'
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
Making all in Autom4te
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61/lib/Autom4te'
make[3]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[3]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/lib/Autom4te'
Making all in m4sugar
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61/lib/m4sugar'
make[3]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[3]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
autom4te_perllibdir='../..'/lib AUTOM4TE_CFG='../../lib/autom4te.cfg'         ../../bin/autom4te -B '../..'/lib -B '../..'/lib                                 \
                --language=m4sugar                      \
                --freeze                        \
                --output=m4sugar.m4f
autom4te_perllibdir='../..'/lib AUTOM4TE_CFG='../../lib/autom4te.cfg'         ../../bin/autom4te -B '../..'/lib -B '../..'/lib                                 \
                --language=m4sh                 \
                --freeze                        \
                --output=m4sh.m4f
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/lib/m4sugar'
Making all in autoconf
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61/lib/autoconf'
make[3]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[3]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
autom4te_perllibdir='../..'/lib AUTOM4TE_CFG='../../lib/autom4te.cfg'         ../../bin/autom4te -B '../..'/lib -B '../..'/lib                                 \
                --language=autoconf                     \
                --freeze                        \
                --output=autoconf.m4f
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/lib/autoconf'
Making all in autotest
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61/lib/autotest'
make[3]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[3]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
autom4te_perllibdir='../..'/lib AUTOM4TE_CFG='../../lib/autom4te.cfg'         ../../bin/autom4te -B '../..'/lib -B '../..'/lib                                 \
                --language=autotest                     \
                --freeze                        \
                --output=autotest.m4f
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/lib/autotest'
Making all in autoscan
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61/lib/autoscan'
make[3]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[3]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
echo '# Automatically Generated: do not edit this file' >autoscan.list
sed '/^[#]/!q' ./autoscan.pre                  >>autoscan.list
( \
          sed -n '/^[^#]/p' ./autoscan.pre; \
          autom4te_perllibdir='../..'/lib AUTOM4TE_CFG='../../lib/autom4te.cfg'         ../../bin/autom4te -B '../..'/lib -B '../..'/lib         --cache '' -M -l autoconf -t'AN_OUTPUT:$1: $2          $3' \
        ) | LC_ALL=C sort                                      >>autoscan.list
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/lib/autoscan'
Making all in emacs
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61/lib/emacs'
make[3]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[3]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/lib/emacs'
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61/lib'
make[3]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[3]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
rm -f autom4te.cfg autom4te.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' ./autom4te.in >autom4te.tmp
chmod a-w autom4te.tmp
mv autom4te.tmp autom4te.cfg
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/lib'
make[1]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/lib'
Making all in man
make[1]: Entering directory `/home/code-red/Desktop/autoconf-2.61/man'
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/man'
Making all in doc
make[1]: Entering directory `/home/code-red/Desktop/autoconf-2.61/doc'
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/doc'
Making all in tests
make[1]: Entering directory `/home/code-red/Desktop/autoconf-2.61/tests'
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/tests'
Making install in bin
make[1]: Entering directory `/home/code-red/Desktop/autoconf-2.61/bin'
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
autom4te_perllibdir='..'/lib AUTOM4TE_CFG='../lib/autom4te.cfg'         ../bin/autom4te -B '..'/lib -B '..'/lib         --language M4sh --cache '' --melt ./autoconf.as -o autoconf.in
rm -f autoconf autoconf.tmp
sed -e 's|@SHELL[@]|/bin/bash|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@bindir[@]|/usr/bin|g' -e 's|@datadir[@]|/usr/share/autoconf|g' -e 's|@prefix[@]|/usr|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/m4|g' -e 's|@M4_DEBUGFILE[@]|--debugfile|g' -e 's|@AWK[@]|mawk|g' -e 's|@VERSION[@]|2.61|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from autoconf.in; do not edit by hand.|g' `test -f ./autoconf.in || echo ./`autoconf.in >autoconf.tmp
chmod +x autoconf.tmp
chmod a-w autoconf.tmp
mv autoconf.tmp autoconf
make[2]: Entering directory `/home/code-red/Desktop/autoconf-2.61/bin'
make[3]: Entering directory `/home/code-red/Desktop/autoconf-2.61'
make[3]: Leaving directory `/home/code-red/Desktop/autoconf-2.61'
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
 /usr/bin/install -c 'autom4te' '/usr/bin/autom4te'
/usr/bin/install: cannot create regular file `/usr/bin/autom4te': Permission denied
 /usr/bin/install -c 'autoconf' '/usr/bin/autoconf'
/usr/bin/install: cannot create regular file `/usr/bin/autoconf': Permission denied
 /usr/bin/install -c 'autoheader' '/usr/bin/autoheader'
/usr/bin/install: cannot create regular file `/usr/bin/autoheader': Permission denied
 /usr/bin/install -c 'autoreconf' '/usr/bin/autoreconf'
/usr/bin/install: cannot create regular file `/usr/bin/autoreconf': Permission denied
 /usr/bin/install -c 'ifnames' '/usr/bin/ifnames'
/usr/bin/install: cannot create regular file `/usr/bin/ifnames': Permission denied
 /usr/bin/install -c 'autoscan' '/usr/bin/autoscan'
/usr/bin/install: cannot create regular file `/usr/bin/autoscan': Permission denied
 /usr/bin/install -c 'autoupdate' '/usr/bin/autoupdate'
/usr/bin/install: cannot create regular file `/usr/bin/autoupdate': Permission denied
make[2]: *** [install-binSCRIPTS] Error 1
make[2]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/bin'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/code-red/Desktop/autoconf-2.61/bin'
make: *** [install-recursive] Error 1
code-red@hack:~/Desktop/autoconf-2.61$ 
code-red@hack:~/Desktop/autoconf-2.61$ 
code-red@hack:~/Desktop/autoconf-2.61$ 
[/SIZE]

---

### Post by Code_Red on 2007-10-31
In the Synaptic Package manager installed is autoconf version 2.63 but ther KDevelop report de same message:

This Makefile is only for the CVS repository
This will be deleted before making the distribution
<br />
./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

---

### Post by Code_Red on 2007-10-31
Other program to programing c++ in linux???

---

### Post by Paul820 on 2007-10-31
You are getting permission denied when installing because the sudo only works on the first command:
> sudo ./configure --prefix=/usr && make && make install

First do:
> sudo ./configure --prefix=/usr && make
Then:
> sudo make install

If you want to try another ide i would recommend either geany or codeblocks.

EDIT: In fact you don't even need the sudo before the configure, you only need sudo for the 'make install' as you are writing into the systems folders.

---

### Post by Paul820 on 2007-10-31
You can get codeblocks from here [http://forums.codeblocks.org/index.php/board,20.0.html]("http://forums.codeblocks.org/index.php/board,20.0.html")
Just look for the latest nightly build. You will also need
> libwxgtk2.8-0
from the repos and geany is available from the repos.

---

