---
title: "List of dependencies of packages requested"
date: 2008-10-29
forum: Programming Talk
---

### Post by jis on 2008-10-29
How can you get a simple complete recursive list of packages that another list of packages depends on? It would include all packages that satisfy aforementioned dependencies, or at least installed ones. It would be nice to have an option to include recommended packages and even suggested packages but the list should contain only package names. I want this kind of lists to perform set operations with them.

---

### Post by slavik on 2008-10-29
it's doable ... I'm not sure if there is a script in existance, though ...

---

### Post by bapoumba on 2008-10-29
For one package, you can use the output of dpkg, apt-cache or aptitude. Dunno how to do that for several packages though.

```
bapoumba@SonyBlue:~$ dpkg -s gedit | grep ^Depends:
Depends: gconf2 (>= 2.10.1-2), gedit-common (>= 2.22), gedit-common (<< 2.23), iso-codes, libatk1.0-0 (>= 1.20.0), libattr1 (>= 2.4.4-1), libc6 (>= 2.4), libcairo2 (>= 1.6.0), libenchant1c2a, libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.16.0), libgnome2-0 (>= 2.17.3), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.12.0), libgtksourceview2.0-0 (>= 2.2.0), liblaunchpad-integration1 (>= 0.1.17), libpango1.0-0 (>= 1.20.1), libx11-6, libxml2 (>= 2.6.27), python, python-glade2 (>= 2.9.7), python-gobject (>= 2.11.5), python-gtk2 (>= 2.9.7), python-gtksourceview2 (>= 2.2.0), python-support (>= 0.7.1), python2.5 (>= 2.5), scrollkeeper

```

```
bapoumba@SonyBlue:~$ apt-cache depends gedit
gedit
  Depends: gconf2
  Depends: gedit-common
  Depends: gedit-common
  Depends: iso-codes
  Depends: libatk1.0-0
  Depends: libattr1
  Depends: libc6
  Depends: libcairo2
  Depends: libenchant1c2a
  Depends: libgconf2-4
  Depends: libglade2-0
  Depends: libglib2.0-0
  Depends: libgnome2-0
  Depends: libgnomeui-0
  Depends: libgnomevfs2-0
  Depends: libgtk2.0-0
  Depends: libgtksourceview2.0-0
  Depends: liblaunchpad-integration1
  Depends: libpango1.0-0
  Depends: libx11-6
  Depends: libxml2
  Depends: python
  Depends: python-glade2
  Depends: python-gobject
  Depends: python-gtk2
  Depends: python-gtksourceview2
  Depends: python-support
  Depends: python2.5
  Depends: scrollkeeper
    rarian-compat
  Recommends: libgnomevfs2-bin
  Recommends: python-gnome2
  Recommends: zenity
  Conflicts: gedit-common
  Replaces: gedit-common

```
```
bapoumba@SonyBlue:~$ aptitude show gedit
Package: gedit
State: installed
Automatically installed: yes
Version: 2.22.3-0ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 2753k
Depends: gconf2 (>= 2.10.1-2), gedit-common (>= 2.22), gedit-common (< 2.23),
         iso-codes, libatk1.0-0 (>= 1.20.0), libattr1 (>= 2.4.4-1), libc6 (>=
         2.4), libcairo2 (>= 1.6.0), libenchant1c2a, libgconf2-4 (>= 2.13.5),
         libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.16.0), libgnome2-0 (>=
         2.17.3), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90),
         libgtk2.0-0 (>= 2.12.0), libgtksourceview2.0-0 (>= 2.2.0),
         liblaunchpad-integration1 (>= 0.1.17), libpango1.0-0 (>= 1.20.1),
         libx11-6, libxml2 (>= 2.6.27), python, python-glade2 (>= 2.9.7),
         python-gobject (>= 2.11.5), python-gtk2 (>= 2.9.7),
         python-gtksourceview2 (>= 2.2.0), python-support (>= 0.7.1), python2.5
         (>= 2.5), scrollkeeper
Recommends: libgnomevfs2-bin, python-gnome2, zenity
Conflicts: gedit-common (<= 2.10.5-1)
Replaces: gedit-common (< 2.16.2-3)
Description: official text editor of the GNOME desktop environment
 gedit is a text editor which supports most standard editor features, extending
 this basic functionality with other features not usually found in simple text
 editors. gedit is a graphical application which supports editing multiple text
 files in one window (known sometimes as tabs or MDI). 
 
 gedit fully supports international text through its use of the Unicode UTF-8
 encoding in edited files. Its core feature set includes syntax highlighting of
 source code, auto indentation and printing and print preview support. 
 
 gedit is also extensible through its plugin system, which currently includes
 support for spell checking, comparing files, viewing CVS ChangeLogs, and
 adjusting indentation levels. 
 
 Homepage: http://www.gnome.org/projects/gedit/

```

---

### Post by jis on 2008-10-29
I want recursive dependencies so I can think of "apt-cache --recurse depends [pkg...]" and "apt-rdepends --follow=Depends,PreDepends,Suggests,Recommends --show=Depends,PreDepends,Suggests,Recommends [pkg...]". The former gives 29039 line hard-to-parse output for gedit. The latter one gives easier-to-parse 32 line output, but is obviously not recursive, which is a bug I think, and sometimes outputs "non-existing" dependencies instead of packages that provide those dependencies: e.g. for aptitude it should list apt, but it lists libapt-pkg-libc6.7-6-4.6 in ubuntu 8.04.

---

