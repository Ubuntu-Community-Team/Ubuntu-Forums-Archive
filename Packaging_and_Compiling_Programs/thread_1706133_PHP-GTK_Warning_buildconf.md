---
title: "PHP-GTK Warning buildconf"
date: 2011-03-13
forum: Packaging and Compiling Programs
---

### Post by Dr.Paneas on 2011-03-13
I am trying to install PHP-GTK-2.0.1 Source - 15 May 2008

```

paneas@paneasbox:~/Downloads$ ls
php-gtk-2.0.1  php-gtk-2.0.1.tar.gz
paneas@paneasbox:~/Downloads$ cd php-gtk-2.0.1/
paneas@paneasbox:~/Downloads/php-gtk-2.0.1$ ./buildconf
rebuilding config.h.in
configure.in:150: warning: LTOPTIONS_VERSION is m4_require'd but not m4_defun'd
aclocal.m4:2944: LT_INIT is expanded from...
aclocal.m4:2979: AC_PROG_LIBTOOL is expanded from...
configure.in:150: the top level
[COLOR=DarkGreen]configure.in:150: warning: LTSUGAR_VERSION is m4_require'd but not m4_defun'd
configure.in:150: warning: LTVERSION_VERSION is m4_require'd but not m4_defun'd
configure.in:150: warning: LTOBSOLETE_VERSION is m4_require'd but not m4_defun'd[/COLOR]

```
How I can fix this warning error ?

EDIT:
Instead of downloading : [php-gtk-2.0.1 Source]("http://gtk.php.net/do_download.php?download_file=php-gtk-2.0.1.tar.gz") - 15-May-2008

I used the other one from CVS server:
```

svn co http://svn.php.net/repository/gtk/php-gtk/trunk php-gtk

```

No errors or warnings :)

---

### Post by gastoncs on 2011-09-09
I have the same Issue, cud you fix it?

---

### Post by SevenMachines on 2011-09-09
Have you tried regenerating aclocal? Other autotools things may need refreshed too
```

# Generate aclocal.m4
$ aclocal

# maybe this, runs lots of autotools, 
# forces all files obsolete and installs missing
$ autoreconf -fi
```

---

