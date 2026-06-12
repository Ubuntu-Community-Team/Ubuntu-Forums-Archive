---
title: "gcc compiler not working"
date: 2006-05-30
forum: Programming Talk
---

### Post by dmorlow on 2006-05-30
Hi, 

I'm trying to compile some premade programs from tar.gz files and cannot get them to compile... Below is the output...

david@ubuntu:~$ tar -xvzf kleandisk-2.1beta1.tar.gz
kleandisk-2.1beta1/
kleandisk-2.1beta1/Makefile.in
kleandisk-2.1beta1/README
kleandisk-2.1beta1/stamp-h.in
kleandisk-2.1beta1/AUTHORS
kleandisk-2.1beta1/COPYING
kleandisk-2.1beta1/ChangeLog
kleandisk-2.1beta1/INSTALL
kleandisk-2.1beta1/Makefile.am
kleandisk-2.1beta1/TODO
kleandisk-2.1beta1/acinclude.m4
kleandisk-2.1beta1/aclocal.m4
kleandisk-2.1beta1/config.h.in
kleandisk-2.1beta1/configure
kleandisk-2.1beta1/configure.in
kleandisk-2.1beta1/admin/
kleandisk-2.1beta1/admin/acinclude.m4.in
kleandisk-2.1beta1/admin/am_edit
kleandisk-2.1beta1/admin/am_edit.py
kleandisk-2.1beta1/admin/ChangeLog
kleandisk-2.1beta1/admin/config.guess
kleandisk-2.1beta1/admin/config.pl
kleandisk-2.1beta1/admin/config.sub
kleandisk-2.1beta1/admin/configure.in.min
kleandisk-2.1beta1/admin/conf.change.pl
kleandisk-2.1beta1/admin/CVS/
kleandisk-2.1beta1/admin/CVS/Entries
kleandisk-2.1beta1/admin/CVS/Repository
kleandisk-2.1beta1/admin/CVS/Root
kleandisk-2.1beta1/admin/CVS/Tag
kleandisk-2.1beta1/admin/debianrules
kleandisk-2.1beta1/admin/depcomp
kleandisk-2.1beta1/admin/install-sh
kleandisk-2.1beta1/admin/libtool.m4.in
kleandisk-2.1beta1/admin/ltcf-c.sh
kleandisk-2.1beta1/admin/ltcf-cxx.sh
kleandisk-2.1beta1/admin/ltcf-gcj.sh
kleandisk-2.1beta1/admin/ltconfig
kleandisk-2.1beta1/admin/ltmain.sh
kleandisk-2.1beta1/admin/Makefile.common
kleandisk-2.1beta1/admin/missing
kleandisk-2.1beta1/admin/mkinstalldirs
kleandisk-2.1beta1/admin/ylwrap
kleandisk-2.1beta1/Makefile.dist
kleandisk-2.1beta1/configure.in.in
kleandisk-2.1beta1/kleandisk.kdevprj
kleandisk-2.1beta1/kleandisk.lsm
kleandisk-2.1beta1/kleandisk/
kleandisk-2.1beta1/kleandisk/Makefile.in
kleandisk-2.1beta1/kleandisk/Makefile.am
kleandisk-2.1beta1/kleandisk/duptree.cpp
kleandisk-2.1beta1/kleandisk/dup.cpp
kleandisk-2.1beta1/kleandisk/buttonlabelwidget.cpp
kleandisk-2.1beta1/kleandisk/abfileinfo.cpp
kleandisk-2.1beta1/kleandisk/udgtree.cpp
kleandisk-2.1beta1/kleandisk/rpmtree.cpp
kleandisk-2.1beta1/kleandisk/instree.cpp
kleandisk-2.1beta1/kleandisk/grouptree.cpp
kleandisk-2.1beta1/kleandisk/restorewizard.cpp
kleandisk-2.1beta1/kleandisk/configuredialog.cpp
kleandisk-2.1beta1/kleandisk/uninstalldialog.cpp
kleandisk-2.1beta1/kleandisk/stringdialog.cpp
kleandisk-2.1beta1/kleandisk/abicondialog.cpp
kleandisk-2.1beta1/kleandisk/udgeditordialog.cpp
kleandisk-2.1beta1/kleandisk/integerdialog.cpp
kleandisk-2.1beta1/kleandisk/logviewwidget.cpp
kleandisk-2.1beta1/kleandisk/buttonlabelwidget3.cpp
kleandisk-2.1beta1/kleandisk/groupviewwidget.cpp
kleandisk-2.1beta1/kleandisk/cleanupwizard.cpp
kleandisk-2.1beta1/kleandisk/buttonlabelwidget2.cpp
kleandisk-2.1beta1/kleandisk/info.cpp
kleandisk-2.1beta1/kleandisk/helperfunctions.cpp
kleandisk-2.1beta1/kleandisk/schedule.cpp
kleandisk-2.1beta1/kleandisk/udg.cpp
kleandisk-2.1beta1/kleandisk/rpm.cpp
kleandisk-2.1beta1/kleandisk/ins.cpp
kleandisk-2.1beta1/kleandisk/filegroupext.cpp
kleandisk-2.1beta1/kleandisk/filegroupbase.cpp
kleandisk-2.1beta1/kleandisk/batch.cpp
kleandisk-2.1beta1/kleandisk/abprocess.cpp
kleandisk-2.1beta1/kleandisk/filelistview.cpp
kleandisk-2.1beta1/kleandisk/ablabel.cpp
kleandisk-2.1beta1/kleandisk/kleandisk.cpp
kleandisk-2.1beta1/kleandisk/main.cpp
kleandisk-2.1beta1/kleandisk/restorebase.cpp
kleandisk-2.1beta1/kleandisk/configurebase.cpp
kleandisk-2.1beta1/kleandisk/uninstallbase.cpp
kleandisk-2.1beta1/kleandisk/stringbase.cpp
kleandisk-2.1beta1/kleandisk/abiconbase.cpp
kleandisk-2.1beta1/kleandisk/udgeditorbase.cpp
kleandisk-2.1beta1/kleandisk/integerbase.cpp
kleandisk-2.1beta1/kleandisk/cleanupbase.cpp
kleandisk-2.1beta1/kleandisk/groupviewbase.cpp
kleandisk-2.1beta1/kleandisk/kleandisk.h
kleandisk-2.1beta1/kleandisk/kleandisk.desktop
kleandisk-2.1beta1/kleandisk/groupviewbase.ui
kleandisk-2.1beta1/kleandisk/ablabel.h
kleandisk-2.1beta1/kleandisk/filelistview.h
kleandisk-2.1beta1/kleandisk/abprocess.h
kleandisk-2.1beta1/kleandisk/batch.h
kleandisk-2.1beta1/kleandisk/filegroupbase.h
kleandisk-2.1beta1/kleandisk/filegroupext.h
kleandisk-2.1beta1/kleandisk/ins.h
kleandisk-2.1beta1/kleandisk/rpm.h
kleandisk-2.1beta1/kleandisk/udg.h
kleandisk-2.1beta1/kleandisk/schedule.h
kleandisk-2.1beta1/kleandisk/helperfunctions.h
kleandisk-2.1beta1/kleandisk/info.h
kleandisk-2.1beta1/kleandisk/buttonlabelwidget2.h
kleandisk-2.1beta1/kleandisk/cleanupbase.ui
kleandisk-2.1beta1/kleandisk/cleanupwizard.h
kleandisk-2.1beta1/kleandisk/groupviewwidget.h
kleandisk-2.1beta1/kleandisk/buttonlabelwidget3.h
kleandisk-2.1beta1/kleandisk/logviewwidget.h
kleandisk-2.1beta1/kleandisk/integerdialog.h
kleandisk-2.1beta1/kleandisk/integerbase.ui
kleandisk-2.1beta1/kleandisk/udgeditorbase.ui
kleandisk-2.1beta1/kleandisk/udgeditordialog.h
kleandisk-2.1beta1/kleandisk/abiconbase.ui
kleandisk-2.1beta1/kleandisk/abicondialog.h
kleandisk-2.1beta1/kleandisk/stringbase.ui
kleandisk-2.1beta1/kleandisk/stringdialog.h
kleandisk-2.1beta1/kleandisk/kleandiskui.rc
kleandisk-2.1beta1/kleandisk/green.xpm
kleandisk-2.1beta1/kleandisk/green_marked.xpm
kleandisk-2.1beta1/kleandisk/red.xpm
kleandisk-2.1beta1/kleandisk/red_marked.xpm
kleandisk-2.1beta1/kleandisk/schedule_gray.xpm
kleandisk-2.1beta1/kleandisk/schedule_green.xpm
kleandisk-2.1beta1/kleandisk/schedule_green_broken.xpm
kleandisk-2.1beta1/kleandisk/schedule_red.xpm
kleandisk-2.1beta1/kleandisk/schedule_red_broken.xpm
kleandisk-2.1beta1/kleandisk/schedule_yellow.xpm
kleandisk-2.1beta1/kleandisk/schedule_yellow_broken.xpm
kleandisk-2.1beta1/kleandisk/kleandisk-large.xpm
kleandisk-2.1beta1/kleandisk/kleandisk-medium.xpm
kleandisk-2.1beta1/kleandisk/kleandisk-mini.xpm
kleandisk-2.1beta1/kleandisk/uninstallbase.ui
kleandisk-2.1beta1/kleandisk/uninstalldialog.h
kleandisk-2.1beta1/kleandisk/install.kleandisk
kleandisk-2.1beta1/kleandisk/configurebase.ui
kleandisk-2.1beta1/kleandisk/configuredialog.h
kleandisk-2.1beta1/kleandisk/restorebase.ui
kleandisk-2.1beta1/kleandisk/restorewizard.h
kleandisk-2.1beta1/kleandisk/grouptree.h
kleandisk-2.1beta1/kleandisk/instree.h
kleandisk-2.1beta1/kleandisk/rpmtree.h
kleandisk-2.1beta1/kleandisk/udgtree.h
kleandisk-2.1beta1/kleandisk/abfileinfo.h
kleandisk-2.1beta1/kleandisk/buttonlabelwidget.h
kleandisk-2.1beta1/kleandisk/dup.h
kleandisk-2.1beta1/kleandisk/duptree.h
kleandisk-2.1beta1/kleandisk/logviewbase.ui
kleandisk-2.1beta1/kleandisk/cleanupbase.h
kleandisk-2.1beta1/kleandisk/logviewbase.cpp
kleandisk-2.1beta1/kleandisk/configurebase.h
kleandisk-2.1beta1/kleandisk/buttonlabelbase2.cpp
kleandisk-2.1beta1/kleandisk/stringbase.h
kleandisk-2.1beta1/kleandisk/abiconbase.h
kleandisk-2.1beta1/kleandisk/groupviewbase.h
kleandisk-2.1beta1/kleandisk/restorebase.h
kleandisk-2.1beta1/kleandisk/buttonlabelbase3.h
kleandisk-2.1beta1/kleandisk/buttonlabelbase.ui
kleandisk-2.1beta1/kleandisk/buttonlabelbase2.ui
kleandisk-2.1beta1/kleandisk/logviewbase.h
kleandisk-2.1beta1/kleandisk/buttonlabelbase2.h
kleandisk-2.1beta1/kleandisk/uninstallbase.h
kleandisk-2.1beta1/kleandisk/udgeditorbase.h
kleandisk-2.1beta1/kleandisk/buttonlabelbase3.cpp
kleandisk-2.1beta1/kleandisk/kleandisk_meta_unload.cpp
kleandisk-2.1beta1/kleandisk/integerbase.h
kleandisk-2.1beta1/kleandisk/buttonlabelbase3.ui
kleandisk-2.1beta1/kleandisk/sv.po
kleandisk-2.1beta1/po/
kleandisk-2.1beta1/po/Makefile.in
kleandisk-2.1beta1/po/Makefile.am
kleandisk-2.1beta1/po/kleandisk.pot
kleandisk-2.1beta1/doc/
kleandisk-2.1beta1/doc/Makefile.in
kleandisk-2.1beta1/doc/Makefile.am
kleandisk-2.1beta1/doc/en/
kleandisk-2.1beta1/doc/en/index.docbook
kleandisk-2.1beta1/doc/en/Makefile.in
kleandisk-2.1beta1/doc/en/Makefile.am
kleandisk-2.1beta1/subdirs
david@ubuntu:~$ cd kleandisk-2.1beta1
david@ubuntu:~/kleandisk-2.1beta1$ ls
acinclude.m4  config.h.in      doc                Makefile.am    stamp-h.in
aclocal.m4    configure        INSTALL            Makefile.dist  subdirs
admin         configure.in     kleandisk          Makefile.in    TODO
AUTHORS       configure.in.in  kleandisk.kdevprj  po
ChangeLog     COPYING          kleandisk.lsm      README
david@ubuntu:~/kleandisk-2.1beta1$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for a C-Compiler...
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
david@ubuntu:~/kleandisk-2.1beta1$ gcc --version
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

david@ubuntu:~/kleandisk-2.1beta1$


Now when I go into the Synaptics program, I show I have GCC versions 3.3, 3.4 and 4.0 installed.  I've had a lot of bad luck in the past by trying to remove or change compilers.  If I try to do that, my luck if I reboot, Linux will crash... so I'm a little hesitant to make any changes.  But I'd like to install this one program, so I need to get my compilers figured out.

Thanks,

David

---

### Post by badrinarayan on 2006-05-30
Hi David,

You will need to install the build-essential package. Type this from the terminal (and enter your password when prompted): ```
sudo apt-get install build-essential
```. Alternatively, you may install it from Synaptic. ([From FAQ]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2513437"))

---

### Post by Mephist0 on 2006-06-02
ahh thx. this helped me too :) I did just search for GCC packages and glibc, ncurses, zlib and such but did not know about this packages.. 

Now it works better..

now i get this message instead 
configure: error: termcap support not found

But now I'll make a new search in the forum.. hehe.. thx!

---

