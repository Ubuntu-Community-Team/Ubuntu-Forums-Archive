---
title: "problems using apt/dpkg help!"
date: 2005-12-15
forum: Repositories &amp; Backports
---

### Post by herot on 2005-12-15
i tried to install ubuntu-lite-desktop...
now whenever i try to do something with apt i get the code below....
also it says i need to do "dpkg --configure -a" but when i try to do that the computer just locks up (usually at configuring bittornado) and i have to turn it off and back on (cant even reboot) so i thought i would try purging the packages it locks up on or try purging ubuntu-lite-desktop but none of these have fixed my problem!!  how can i get this package to go away like before i tried to install it??? please help!



```

herot@slasheru:~$ su
Password:
root@slasheru:/home/herot # /etc/init.d/samba stop
 * Stopping Samba daemons...                                             [done!]
root@slasheru:/home/herot # apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:3 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Get:4 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:5 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Fetched 39.6kB in 11s (3542B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
root@slasheru:/home/herot # dpkg --purge
dpkg: --purge needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

root@slasheru:/home/herot # dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 xpdf-utils           Portable Document Format (PDF) suite -- utilities
 xpdf-reader          Portable Document Format (PDF) suite -- viewer for X11
 libgoffice-1         Document centric objects library - runtime files
 rox-filer            A simple graphical file manager for X11
 wdm                  WINGs Display Manager - an xdm replacement with a WindowM
 graveman             graphical tool to burn dvd and cd, gtk based
 icewm-themes         Theme files for the Ice Window Manager
 xpdf                 Portable Document Format (PDF) suite
 gnumeric-common      common files for Gnumeric, the GNOME spreadsheet applicat
 python-wxgtk2.4      wxWindows Cross-platform C++ GUI toolkit (wxPython bindin
 icewm                wonderful Win95-OS/2-Motif-like window manager
 sylpheed-i18n        Locale data for Sylpheed (i18n support)
 emelfm               file manager for X/gtk
 libwraster3          Shared libraries of Window Maker rasterizer
 icewm-common         wonderful Win95-OS/2-Motif-like window manager
 abiword              WYSIWYG word processor based on GTK2
 python-gtk-1.2       GTK support module for Python
 libgpgme11           GPGME - GnuPG Made Easy
 iceme                A graphical menu editor for IceWM
 icepref              Yet another configuration tool for IceWM
 cdrdao               Disk-At-Once (DAO) recording of audio and data CD-Rs/CD-R
 libxfcegui4-3        Basic GUI C functions for Xfce4
 xpdf-common          Portable Document Format (PDF) suite -- common files
 lynx                 Text-mode WWW Browser
 sylpheed             Light weight e-mail client with GTK+
 python-wxversion     wxWidgets Cross-platform C++ GUI toolkit (wxPython versio
 python2.4-sip4-qt3   Python/C++ bindings generator - Python2.3+Qt3 runtime
 gqview               A simple image viewer using GTK+
 abiword-common       WYSIWYG word processor based on GTK2
 libmysqlclient14     mysql database client library
 libgsf-gnome-1       Structured File Library - runtime version for GNOME
 mousepad             simple Xfce oriented text editor
 gnumeric             GNOME spreadsheet application
 icewm-gnome-support  GNOME support files for IceWM
 lesstif1             OSF/Motif 1.2 implementation released under LGPL
 libwxgtk2.4-1        wxWindows Cross-platform C++ GUI toolkit (GTK+ runtime)
 python-qt3           Qt3 bindings for Python (default version)
 ivman                daemon to auto-mount and manage media devices
 xfce4-icon-theme     Xfce Standard icon theme
 mc                   midnight commander - a powerful file manager
 hplip                HP Linux Printing and Imaging System (hplip) - GUI
 python2.4-qt3        Qt3 bindings for Python 2.4
 bittornado-gui       bittorrent client with enhanced GUI interface

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 language-selector    Language selector for ubuntu linux
 bittornado           bittorrent client with enhanced curses interface

root@slasheru:/home/herot # dpkg --purge bittornado
(Reading database ... 103737 files and directories currently installed.)
Removing bittornado ...
Use `dselect' or `aptitude' for user-friendly package management.
root@slasheru:/home/herot # dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 xpdf-utils           Portable Document Format (PDF) suite -- utilities
 xpdf-reader          Portable Document Format (PDF) suite -- viewer for X11
 libgoffice-1         Document centric objects library - runtime files
 rox-filer            A simple graphical file manager for X11
 wdm                  WINGs Display Manager - an xdm replacement with a WindowM
 graveman             graphical tool to burn dvd and cd, gtk based
 icewm-themes         Theme files for the Ice Window Manager
 xpdf                 Portable Document Format (PDF) suite
 gnumeric-common      common files for Gnumeric, the GNOME spreadsheet applicat
 python-wxgtk2.4      wxWindows Cross-platform C++ GUI toolkit (wxPython bindin
 icewm                wonderful Win95-OS/2-Motif-like window manager
 sylpheed-i18n        Locale data for Sylpheed (i18n support)
 emelfm               file manager for X/gtk
 libwraster3          Shared libraries of Window Maker rasterizer
 icewm-common         wonderful Win95-OS/2-Motif-like window manager
 abiword              WYSIWYG word processor based on GTK2
 python-gtk-1.2       GTK support module for Python
 libgpgme11           GPGME - GnuPG Made Easy
 iceme                A graphical menu editor for IceWM
 icepref              Yet another configuration tool for IceWM
 cdrdao               Disk-At-Once (DAO) recording of audio and data CD-Rs/CD-R
 libxfcegui4-3        Basic GUI C functions for Xfce4
 xpdf-common          Portable Document Format (PDF) suite -- common files
 lynx                 Text-mode WWW Browser
 sylpheed             Light weight e-mail client with GTK+
 python-wxversion     wxWidgets Cross-platform C++ GUI toolkit (wxPython versio
 python2.4-sip4-qt3   Python/C++ bindings generator - Python2.3+Qt3 runtime
 gqview               A simple image viewer using GTK+

```

---

