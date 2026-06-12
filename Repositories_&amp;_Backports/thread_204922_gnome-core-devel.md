---
title: "gnome-core-devel"
date: 2006-06-27
forum: Repositories &amp; Backports
---

### Post by Rinnan on 2006-06-27
Anjuta recommends "gnome-devel", which makes sense to me.  When I try to add it however, I get this:

```
erik@oak:~$ sudo apt-get install gnome-devel
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gnome-devel: Depends: gnome-core-devel (= 1:2.12.2.3) but it is not going to be installed
E: Broken packages
erik@oak:~$
``` 
I am using "my recommended sources.list" with no changes from the sticky post above this forum.  As far as I can tell it's a bog-standard core/universe/multiverse with sources but without any other repositories.

Can someone help?

---

### Post by knn on 2006-06-27
[QUOTE=Rinnan]Anjuta recommends "gnome-devel", which makes sense to me.  When I try to add it however, I get this:

```
erik@oak:~$ sudo apt-get install gnome-devel
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gnome-devel: Depends: gnome-core-devel (= 1:2.12.2.3) but it is not going to be installed
E: Broken packages
erik@oak:~$
``` 
I am using "my recommended sources.list" with no changes from the sticky post above this forum.  As far as I can tell it's a bog-standard core/universe/multiverse with sources but without any other repositories.

Can someone help?[/QUOTE]

Open synaptic, search for gnome-core-devel, and mark it. It comes with a lot of dependencies, so one of those probably can't be resolved. When you see this kind of error message it is always a good idea to try to install the package apt complains about separatly (i.e. not as a dependancy), because then you'll see what the real problem is. In case you have Breezy maybe you have to upgrade to Dapper

---

### Post by Rinnan on 2006-06-28
Thank you.  This is what I get:

```
gnome-core-devel:
 Depends: libatspi-dev but it is not going to be installed
 Depends: libeel2-dev but it is not going to be installed
 Depends: libgnomeprintui2.2-dev but it is not going to be installed
 Depends: libgnomeprint2.2-dev but it is not going to be installed
 Depends: libnautilus-extension-dev but it is not going to be installed
 Depends: libgail-dev but it is not going to be installed
 Depends: libgtk2.0-dev but it is not going to be installed
 Depends: libpanel-applet2-dev but it is not going to be installed
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libglade2-dev but it is not going to be installed
 Depends: libgnomeui-dev but it is not going to be installed
 Depends: librsvg2-dev but it is not going to be installed
 Depends: libgtksourceview-dev but it is not going to be installed
```

Still researching...

---

### Post by ashrack on 2006-07-08
are their any solutions to this??

This is my error:

```
sudo apt-get install gnome-core-devel
The following packages have unmet dependencies.
  gnome-core-devel: Depends: libeel2-dev (>= 2.12.2) but it is not going to be installed
                    Depends: libgnome-menu-dev (>= 2.12.0) but it is not going to be installed
                    Depends: libnautilus-extension-dev (>= 2.12.2) but it is not going to be installed
                    Depends: libgnome2-dev (>= 2.12.0.1) but it is not going to be installed
                    Depends: libgnomevfs2-dev (>= 2.12.2) but it is not going to be installed
                    Depends: libpanel-applet2-dev (>= 2.12.2) but it is not going to be installed
                    Depends: libgnomeui-dev (>= 2.12.0) but it is not going to be installed
E: Broken packages


```

---

### Post by knn on 2006-07-08
As I've said two post ago:

> When you see this kind of error message it is always a good idea to try to install the package apt complains about separatly (i.e. not as a dependancy), because then you'll see what the real problem is. In case you have Breezy maybe you have to upgrade to Dapper

Try installing all those dependancies separately, until you find the package that's causing the problem.

---

### Post by ashrack on 2006-07-08
tried installing them separately but I get dependency problem on all of them.
I opened a bug report here:
[https://launchpad.net/distros/ubuntu/+source/meta-gnome2/+bug/52344](https://launchpad.net/distros/ubuntu/+source/meta-gnome2/+bug/52344)
anyelse also affected by this bug please report the bug

---

### Post by knn on 2006-07-08
What's the output of:
sudo apt-get install libeel2-dev
sudo apt-get install libgnome-menu-dev
sudo apt-get install libnautilus-extension-dev
sudo apt-get install libgnome2-dev
sudo apt-get install libgnomevfs2-dev
sudo apt-get install libpanel-applet2-dev
sudo apt-get install libgnomeui-dev

---

### Post by ashrack on 2006-07-08
I got it to work using the following:
```
aptitude install gnome-core-devel
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libdbus-1-dev
The following NEW packages will be automatically installed:
  autoconf automake1.4 autotools-dev docbook docbook-dsssl docbook-to-man docbook-xsl gnome-common gtk-doc-tools intltool jade libart-2.0-dev
  libatspi-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libbz2-dev libcompress-zlib-perl libcroco3-dev
  libeel2-dev libfont-afm-perl libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev libgnome-desktop-dev libgnome-keyring-dev libgnome-menu-dev
  libgnome2-dev libgnomecanvas2-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgpg-error-dev
  libgsf-1-dev libgtksourceview-dev libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libidl-dev libltdl3 libltdl3-dev
  libmailtools-perl libnautilus-extension-dev libopencdk8-dev liborbit2-dev libpanel-applet2-dev librsvg2-dev libsp1c2 libstartup-notification0-dev
  libtasn1-2-dev libtimedate-perl libtool liburi-perl libwww-perl libxml-parser-perl libxml2-dev libxslt1-dev m4 orbit2 sp
The following NEW packages will be installed:
  autoconf automake1.4 autotools-dev docbook docbook-dsssl docbook-to-man docbook-xsl gnome-common gnome-core-devel gtk-doc-tools intltool jade
  libart-2.0-dev libatspi-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libbz2-dev libcompress-zlib-perl
  libcroco3-dev libeel2-dev libfont-afm-perl libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev libgnome-desktop-dev libgnome-keyring-dev
  libgnome-menu-dev libgnome2-dev libgnomecanvas2-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev
  libgpg-error-dev libgsf-1-dev libgtksourceview-dev libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libidl-dev libltdl3
  libltdl3-dev libmailtools-perl libnautilus-extension-dev libopencdk8-dev liborbit2-dev libpanel-applet2-dev librsvg2-dev libsp1c2
  libstartup-notification0-dev libtasn1-2-dev libtimedate-perl libtool liburi-perl libwww-perl libxml-parser-perl libxml2-dev libxslt1-dev m4 orbit2 sp
0 packages upgraded, 68 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.3MB of archives. After unpacking 59.7MB will be used.
The following packages have unmet dependencies:
  libdbus-1-dev: Depends: libdbus-1-2 (= 0.60-6ubuntu8) but 0.60-6ubuntu9 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libdbus-1-2 [0.60-6ubuntu9 (now) -> 0.60-6ubuntu8 (dapper)]

Score is -40

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  autoconf automake1.4 autotools-dev docbook docbook-dsssl docbook-to-man docbook-xsl gnome-common gtk-doc-tools intltool jade libart-2.0-dev
  libatspi-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libbz2-dev libcompress-zlib-perl libcroco3-dev
  libdbus-1-dev libeel2-dev libfont-afm-perl libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev libgnome-desktop-dev libgnome-keyring-dev
  libgnome-menu-dev libgnome2-dev libgnomecanvas2-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev
  libgpg-error-dev libgsf-1-dev libgtksourceview-dev libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libidl-dev libltdl3
  libltdl3-dev libmailtools-perl libnautilus-extension-dev libopencdk8-dev liborbit2-dev libpanel-applet2-dev librsvg2-dev libsp1c2
  libstartup-notification0-dev libtasn1-2-dev libtimedate-perl libtool liburi-perl libwww-perl libxml-parser-perl libxml2-dev libxslt1-dev m4 orbit2 sp
The following packages will be DOWNGRADED:
  libdbus-1-2
The following NEW packages will be installed:
  autoconf automake1.4 autotools-dev docbook docbook-dsssl docbook-to-man docbook-xsl gnome-common gnome-core-devel gtk-doc-tools intltool jade
  libart-2.0-dev libatspi-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libbz2-dev libcompress-zlib-perl
  libcroco3-dev libdbus-1-dev libeel2-dev libfont-afm-perl libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev libgnome-desktop-dev
  libgnome-keyring-dev libgnome-menu-dev libgnome2-dev libgnomecanvas2-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev libgnomeui-dev libgnomevfs2-dev
  libgnutls-dev libgpg-error-dev libgsf-1-dev libgtksourceview-dev libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libidl-dev libltdl3 libltdl3-dev libmailtools-perl libnautilus-extension-dev libopencdk8-dev liborbit2-dev libpanel-applet2-dev librsvg2-dev libsp1c2
  libstartup-notification0-dev libtasn1-2-dev libtimedate-perl libtool liburi-perl libwww-perl libxml-parser-perl libxml2-dev libxslt1-dev m4 orbit2 sp
0 packages upgraded, 68 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 14.5MB of archives. After unpacking 59.7MB will be used.
Do you want to continue? [Y/n/?] y

```
am just worried why did it have to [COLOR="Red"]downgrade[/COLOR] a package???

---

### Post by dj kraemer on 2006-07-19
Thank you for taking the time to share your solution.
I encountered the exact same problem and your solution helped me!

Thanks!

---

