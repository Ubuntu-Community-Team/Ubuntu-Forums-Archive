---
title: "Install GTK"
date: 2007-03-31
forum: Programming Talk
---

### Post by dJnEvS on 2007-03-31
Im trying to install GTK stuff,
but gtk cant compile because of atk,
and atk cant compile because of glib.

./configure of atk returns this:
```
checking for GLIB - version >= 2.5.7...
*** 'pkg-config --modversion glib-2.0' returned 2.12.4, but GLIB (2.13.0)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
```

So, i need to uninstall gtk 2.12.4,
but how do i do that.

---

### Post by WW on 2007-03-31
Is there a reason that you want to compile it yourself from source?  If not, it will be much easier to install the Ubuntu packages.  Check out the third post (by lnostdal) in this thread: [http://ubuntuforums.org/showthread.php?t=396439](http://ubuntuforums.org/showthread.php?t=396439)

---

### Post by dJnEvS on 2007-03-31
hmm. i think i got a problem with that.

```

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libatk1.0-dev libavahi-client-dev libavahi-glib-dev libbonobo2-dev
  libbonoboui2-dev libgnome-desktop-dev libgnome-keyring-dev libgnomeui-dev
  libgnomevfs2-dev libgpg-error-dev libgtk2.0-dev libopencdk8-dev
  liborbit2-dev libpopt-dev librsvg2-dev libxml2-dev
The following NEW packages will be automatically installed:
  autoconf automake1.4 autotools-dev docbook docbook-dsssl docbook-to-man
  docbook-xsl gnome-common gtk-doc-tools intltool jade libart-2.0-dev
  libatspi-dev libbz2-dev libcroco3-dev libdbus-1-dev libeel2-dev
  libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev libgnome-menu-dev
  libgnome2-dev libgnomecanvas2-dev libgnomeprint2.2-dev
  libgnomeprintui2.2-dev libgnutls-dev libgsf-1-dev libgtksourceview-dev
  libidl-dev libltdl3 libltdl3-dev libnautilus-extension-dev
  libpanel-applet2-dev libsp1c2 libstartup-notification0-dev libtasn1-2-dev
  libtool libxml-parser-perl libxslt1-dev orbit2 sp
The following packages have been kept back:
  ekiga evolution evolution-data-server evolution-plugins file firefox
  firefox-gnome-support language-pack-gnome-en language-pack-gnome-nl
  language-pack-kde-nl libaudio-dev libaudio2 libcamel1.2-8 libebook1.2-5
  libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7
  libedataserverui1.2-6 libegroupwise1.2-9 libexchange-storage1.2-1
  libgpgme11 libmagic1 libmysqlclient15off libnspr4 libnss3 libspeex1
  libwnck-common libwnck18 libwpd8c2a libxine-main1 mysql-common
  openoffice.org openoffice.org-common openoffice.org-core
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-java-common openoffice.org-l10n-en-us python-uno
  ttf-opensymbol wine xmms
The following NEW packages will be installed:
  autoconf automake1.4 autotools-dev docbook docbook-dsssl docbook-to-man
  docbook-xsl gnome-common gnome-core-devel gtk-doc-tools intltool jade
  libart-2.0-dev libatspi-dev libbz2-dev libcroco3-dev libdbus-1-dev
  libeel2-dev libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev
  libgnome-menu-dev libgnome2-dev libgnomecanvas2-dev libgnomeprint2.2-dev
  libgnomeprintui2.2-dev libgnutls-dev libgsf-1-dev libgtksourceview-dev
  libidl-dev libltdl3 libltdl3-dev libnautilus-extension-dev
  libpanel-applet2-dev libsp1c2 libstartup-notification0-dev libtasn1-2-dev
  libtool libxml-parser-perl libxslt1-dev orbit2 sp
0 packages upgraded, 59 newly installed, 0 to remove and 44 not upgraded.
Need to get 15.5MB of archives. After unpacking 64.5MB will be used.
The following packages have unmet dependencies:
  libpopt-dev: Depends: libpopt0 (= 1.7-5) but 1.10-2 is installed.
  liborbit2-dev: Depends: liborbit2 (= 1:2.14.0-0ubuntu1) but 1:2.14.3-0ubuntu2 is installed.
  libgnomeui-dev: Depends: libgnomeui-0 (= 2.14.1-0ubuntu3) but 2.16.1-0ubuntu2 is installed.
  libatk1.0-dev: Depends: libatk1.0-0 (= 1.11.4-0ubuntu1) but 1.12.3-0ubuntu1 is installed.
  libgpg-error-dev: Depends: libgpg-error0 (= 1.1-4) but 1.2-1 is installed.
  libgnome-desktop-dev: Depends: libgnome-desktop-2 (= 2.14.3-0ubuntu1) but 2.16.1-0ubuntu1 is installed.
  libopencdk8-dev: Depends: libopencdk8 (= 0.5.7-2) but 0.5.8-1 is installed.
  libgnome-keyring-dev: Depends: libgnome-keyring0 (= 0.4.9-1ubuntu1) but 0.6.0-0ubuntu2 is installed.
  libavahi-client-dev: Depends: libavahi-client3 (= 0.6.10-0ubuntu3.4) but 0.6.13-2ubuntu2.4 is installed.
  libbonoboui2-dev: Depends: libbonoboui2-0 (= 2.14.0-0ubuntu1) but 2.16.0-0ubuntu1 is installed.
  libbonobo2-dev: Depends: libbonobo2-0 (= 2.14.0-0ubuntu2) but 2.16.0-0ubuntu1 is installed.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.20-0ubuntu1.1) but 2.10.6-0ubuntu3.1 is installed.
  libxml2-dev: Depends: libxml2 (= 2.6.24.dfsg-1ubuntu1) but 2.6.26.dfsg-2ubuntu4 is installed.
  libgnomevfs2-dev: Depends: libgnomevfs2-0 (= 2.14.2-0ubuntu1) but 2.16.1-0ubuntu7 is installed.
  librsvg2-dev: Depends: librsvg2-2 (= 2.14.4-0ubuntu1) but 2.16.0-0ubuntu2 is installed.
  libavahi-glib-dev: Depends: libavahi-glib1 (= 0.6.10-0ubuntu3.4) but 0.6.13-2ubuntu2.4 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnome-core-devel [Not Installed]
libatk1.0-dev [Not Installed]
libatspi-dev [Not Installed]
libavahi-client-dev [Not Installed]
libavahi-glib-dev [Not Installed]
libbonobo2-dev [Not Installed]
libbonoboui2-dev [Not Installed]
libeel2-dev [Not Installed]
libgail-dev [Not Installed]
libgconf2-dev [Not Installed]
libgcrypt11-dev [Not Installed]
libglade2-dev [Not Installed]
libgnome-desktop-dev [Not Installed]
libgnome-keyring-dev [Not Installed]
libgnome-menu-dev [Not Installed]
libgnome2-dev [Not Installed]
libgnomecanvas2-dev [Not Installed]
libgnomeprint2.2-dev [Not Installed]
libgnomeprintui2.2-dev [Not Installed]
libgnomeui-dev [Not Installed]
libgnomevfs2-dev [Not Installed]
libgnutls-dev [Not Installed]
libgpg-error-dev [Not Installed]
libgsf-1-dev [Not Installed]
libgtk2.0-dev [Not Installed]
libgtksourceview-dev [Not Installed]
libnautilus-extension-dev [Not Installed]
libopencdk8-dev [Not Installed]
liborbit2-dev [Not Installed]
libpanel-applet2-dev [Not Installed]
libpopt-dev [Not Installed]
librsvg2-dev [Not Installed]
libxml2-dev [Not Installed]
libxslt1-dev [Not Installed]

Score is 296

Accept this solution? [Y/n/q/?]
```

when i press y, it doesnt do anything
when i press n, it wants to downgrade lots of stuff....

---

### Post by dJnEvS on 2007-03-31
Please respond,
How do i uninstall something that is compiled from source??

---

### Post by egrus on 2007-04-03
go back to the directory in which you compiled and execute 
```
sudo make uninstall
```

cheers
surge

---

