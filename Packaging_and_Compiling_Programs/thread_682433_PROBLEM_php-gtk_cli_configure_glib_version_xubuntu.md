---
title: "PROBLEM: php-gtk cli configure glib version xubuntu Gutsy"
date: 2008-01-30
forum: Packaging and Compiling Programs
---

### Post by essexboyracer on 2008-01-30
Hi All,

I am trying to get php-gtk working on xubuntu gutsy. Steps followed;

1. install php cli version from synaptic and php-dev for phpize
2. checked out thelatest CVS og php-gtk 2, as per instructions at [http://gtk.php.net/manual/en/tutorials.installation.linux.php](http://gtk.php.net/manual/en/tutorials.installation.linux.php)
3. Followed instructions for installing over an existing php install, with the following;

```
$ ./buildconf --with-phpize=/usr/bin/phpize
```
output:

Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
rebuilding aclocal.m4
rebuilding configure
rebuilding config.h.in

```
$ ./configure --with-php-config=/usr/bin/php-config
```
output:

checking for GLIB - version >= 2.6.0... no
*** A new enough version of pkg-config was not found.
*** See [http://www.freedesktop.org/software/pkgconfig/](http://www.freedesktop.org/software/pkgconfig/)
configure: error: PHP-GTK 2.x requires GLib 2.6.0 or higher

Thats where I am up to. Checked synaptic for glib 2.6.0 but am stuck. Any ideas?

---

### Post by PaulFr on 2008-01-30
```
aptitude show pkg-config
aptitude show libglib2.0-dev
```The first line is for your pkg-config version error, the second for the glib (you'll need to verify version and installation status). Hope this helps.

---

### Post by essexboyracer on 2008-01-30
aptitude show pkg-config
```
root@kubuntu:/home/oliver# aptitude show pkg-config
Package: pkg-config
State: installed
Automatically installed: no
Version: 0.22-1
Priority: optional
Section: devel
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 156k
Depends: libc6 (>= 2.5-5), libglib2.0-0 (>= 2.13.5)
Description: manage compile and link flags for libraries
 pkg-config is a system for managing library compile and link flags that works
 with automake and autoconf. 
 
 Increasingly libraries ship with ".pc" files that allow querying of the
 compiler and linker flags needed to use them through the pkg-config(1) program.

```

aptitude show libglib2.0-dev

```
root@kubuntu:/home/oliver# aptitude show libglib2.0-dev
Package: libglib2.0-dev
State: installed
Automatically installed: no
Version: 2.14.1-1ubuntu1
Priority: optional
Section: libdevel
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 2384k
Depends: libglib2.0-0 (= 2.14.1-1ubuntu1), pkg-config (>= 0.14.0)
Suggests: libglib2.0-doc
Conflicts: libglib1.3-dev
Replaces: libglib1.3-dev
Description: Development files for the GLib library
 GLib is a library containing many useful C routines for things such as trees,
 hashes, lists, and strings.  It is a useful general-purpose C library used by
 projects such as GTK+, GIMP, and GNOME. 
 
 This package is needed to compile programs against libglib2.0-0, as only it
 includes the header files and static libraries (optionally) needed for
 compiling.
```

So I need better versions of both? Any hints / pointers as to next step?

---

### Post by PaulFr on 2008-01-31
You have version 0.22 of pkg-config (that is the latest) and version 2.14.1 of glib2.0 so that should be enough. You can test this by running ```
/usr/bin/pkg-config --modversion glib-2.0
```

The standard pkg-config is /usr/bin/pkg-config, so if you want to force the configure command to use this, you can ```
export PKG_CONFIG=/usr/bin/pkg-config
```before running your **configure** command.

FYI, when I tried to reproduce your steps on my Hardy Heron alpha (with 0.22 version of pkg-config and 2.15.4 version of glib-2.0), I did not have an issue with glib, but I had a problem with the flex version mentioned in acinclude.m4 (the flex_version_list mentioned there does not match the flex version on my system - the entry indicates 2.5.4, the system has flex 2.5.33 (run **flex -V** to find out)). I had to edit it to > flex_version_list="2.5.33" and then configure completed successfully.

---

### Post by essexboyracer on 2008-01-31
well, didnt do anything since my last post (save a couple of re-boots) and it installed fine, ran the demo.php fine. weird

---

