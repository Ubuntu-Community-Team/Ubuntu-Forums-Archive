---
title: "compiling Firefox for qt"
date: 2007-11-30
forum: Packaging and Compiling Programs
---

### Post by kiev on 2007-11-30
Please help 

I'm building with: 
./configure --build=x86_64-linux-gnu --prefix=/usr '--includedir=/usr/include' '--mandir=/usr/share/man' '--infodir=/usr/share/info' --sysconfdir=/etc --localstatedir=/var '--libexecdir=/usr/lib/firefox' --disable-maintainer-mode --disable-dependency-tracking --srcdir=. --disable-debug --with-default-mozilla-five-home= --with-user-appdir=.mozilla --with-system-png=/usr --with-system-jpeg=/usr --with-system-zlib=/usr --with-system-nspr --with-system-nss --disable-composer --disable-debug --disable-elf-dynstr-gc --disable-gtktest --disable-installer --disable-ldap --disable-mailnews --disable-profilesharing --disable-strip --disable-strip-libs --disable-tests --disable-updater --disable-xprint --enable-application=browser --enable-canvas --enable-libthai '--enable-optimize=-pipe\ -w\ -O2\ -fno-strict-aliasing\ -ftree-vectorize\ -march=athlon64\ -g' --enable-postscript --enable-svg --enable-svg-renderer=cairo --enable-system-cairo --enable-mathml --enable-xft --disable-xinerama --enable-extensions=default --enable-single-profile --enable-system-myspell --with-distribution-id=com.ubuntu --enable-official-branding --enable-system-cairo --with-qtdir=/usr/include/qt3 --enable-default-toolkit=qt      

Or:
**./configure --with-qtdir=/usr/include/qt3 --enable-default-toolkit=qt --enable-application=browser**

[B]Error:
checking Qt - version >= 3.2.0... no
configure: error: Qt Mozilla requires at least version 3.2.0 of Qt
[/B]

**$ sudo dpkg -la|grep qt**
ii  apport-qt                                  0.98                                      Qt4 frontend for the apport crash report sys
ii  gtk-qt-engine                              1:0.8~svn-rev36-2ubuntu2                  theme engine using Qt for GTK+ 2.x
ii  gtk2-engines-gtk-qt                        1:0.8~svn-rev36-2ubuntu2                  transitional dummy package
ii  gtk2-engines-qtcurve                       0.52.3-1                                  This is a set of widget styles for Gtk2 base
ii  gtk2-engines-qtpixmap                      0.28-1.2                                  QtPixmap GTK2.x theming engine
ii  kde-style-qtcurve                          0.52.3-1                                  This is a set of widget styles for KDE3 base
ii  kde4-style-qtcurve                         0.51-0ubuntu1                             Unified widget style for KDE and GTK+
ii  language-selector-qt                       0.2.9                                     Language selector for kubuntu linux
ii  libavahi-qt3-1                             0.6.20-2ubuntu3                           Avahi Qt3 integration library
ii  libavahi-qt3-dev                           0.6.20-2ubuntu3                           Development headers for the Avahi Qt3 integr
ii  libdbus-qt-1-1c2                           0.62.git.20060814-2build1                 simple interprocess messaging system (Qt-bas
ii  libpoppler-qt1                             0.5.91-0ubuntu1                           PDF rendering library (Qt 3 based shared lib
ii  libpoppler-qt2                             0.6.2-1~gutsy1                            PDF rendering library (Qt 3 based shared lib
ii  libqt-perl                                 3.008-2build1                             Perl bindings for the Qt library
ii  libqt0-ruby1.8                             4:3.5.7-1ubuntu4                          Qt bindings for Ruby
ii  libqt3-compat-headers                      3:3.3.8really3.3.7-0ubuntu11.1            Qt 1.x and 2.x compatibility includes
ii  libqt3-headers                             3:3.3.8really3.3.7-0ubuntu11.1            Qt3 header files
ii  libqt3-i18n                                3:3.3.8really3.3.7-0ubuntu11.1            i18n files for Qt3 library
ii  libqt3-mt                                  3:3.3.8really3.3.7-0ubuntu11.1            Qt GUI Library (Threaded runtime version), V
ii  libqt3-mt-dev                              3:3.3.8really3.3.7-0ubuntu11.1            Qt development files (Threaded)
ii  libqt3-mt-sqlite                           3:3.3.8really3.3.7-0ubuntu11.1            SQLite database driver for Qt3 (Threaded)
ii  libqt4-core                                4.3.2-0ubuntu3.1                          Qt 4 core non-GUI functionality runtime libr
ii  libqt4-gui                                 4.3.2-0ubuntu3.1                          Qt 4 core GUI functionality runtime library
ii  libqt4-qt3support                          4.3.2-0ubuntu3.1                          Qt 3 compatibility library for Qt 4
ii  libqt4-sql                                 4.3.2-0ubuntu3.1                          Qt 4 SQL database module
ii  libsmokeqt1                                4:3.5.7-1ubuntu4                          SMOKE Binding Library to Qt
ii  pinentry-qt                                0.7.3-1ubuntu2                            Qt-based PIN or pass-phrase entry dialog for
ii  python-qt3                                 3.17.3-2ubuntu3                           Qt3 bindings for Python
ii  python-qt4                                 4.3-2ubuntu7.1                            Python bindings for Qt4
ii  qt3-apps-dev                               3:3.3.8really3.3.7-0ubuntu11.1            Qt3 Developer applications development files
ii  qt3-dev-tools                              3:3.3.8really3.3.7-0ubuntu11.1            Qt3 development tools
ii  qt3-dev-tools-compat                       3:3.3.8really3.3.7-0ubuntu11.1            Conversion utilities for Qt3 development
ii  qt3-dev-tools-embedded                     3:3.3.8really3.3.7-0ubuntu11.1            Tools to develop embedded Qt applications

---

### Post by dholbach on 2007-12-03
Check out  config.log  and see what it complains about.

---

### Post by mr_ed on 2007-12-05
Just so you're aware, there hasn't been much activity on this project since about 2003.

---

### Post by z0mbie on 2007-12-21
I wish this project would build up some momentum. With KDE 4 coming out, I hope to see some light shed into Firefox Qt.

---

### Post by rzrgenesys187 on 2007-12-21
What is Firefox for qt may I ask?

---

### Post by z0mbie on 2007-12-22
> **rzrgenesys187 said:**
> What is Firefox for qt may I ask?

Qt = KDE 

GTK = Gnome

Firefox is GTK designed. So Firefox for Qt is just better integration with KDE.

---

### Post by panda84 on 2008-05-15
> **mr_ed said:**
> Just so you're aware, there hasn't been much activity on this project since about 2003.

Great news: someone is working on it now!
[http://blog.vlad1.com/2008/05/06/well-isnt-that-qt/](http://blog.vlad1.com/2008/05/06/well-isnt-that-qt/)

---

