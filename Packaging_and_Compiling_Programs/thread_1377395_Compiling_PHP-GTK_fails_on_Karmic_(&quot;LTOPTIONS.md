---
title: "Compiling PHP-GTK fails on Karmic (&quot;LTOPTIONS_VERSION: command not found&quot; etc.)"
date: 2010-01-10
forum: Packaging and Compiling Programs
---

### Post by xtrakt on 2010-01-10
I'm trying to compile PHP-GTK from source using these simple instructions:

```

svn co http://svn.php.net/repository/gtk/php-gtk/trunk php-gtk
cd php-gtk
./buildconf
./configure
make
make install

```At first it failed at ./buildconf. It did this:

```

cd /usr/share/aclocal
chmod 777 libtool.m4
cat lt~obsolete.m4 ltoptions.m4 ltsugar.m4 ltversion.m4 >> libtool.m4
chmod 644 libtool.m4

```Worked. Then ./configure failed because PHP-Cairo was not installed. So I installed it. Now ./configure fails with these errors:

```

./configure: line 12344: LTOPTIONS_VERSION: command not found
./configure: line 12345: LTSUGAR_VERSION: command not found
./configure: line 12346: LTVERSION_VERSION: command not found
./configure: line 12347: LTOBSOLETE_VERSION: command not found
checking for a sed that does not truncate output... (cached) /bin/sed
./configure: line 12422: syntax error near unexpected token `lt_decl_varnames,'
./configure: line 12422: `lt_if_append_uniq(lt_decl_varnames, SED, , ,'

```I haven't found any any solution to this. All help much appreciated.

Here's the complete output of ./configure:
[http://pastebin.com/f6823ae63](http://pastebin.com/f6823ae63)

---

### Post by SevenMachines on 2010-01-10
add the macros to aclocal in the source root dir of php-gtk

$cat /usr/share/aclocal/ltoptions.m4 /usr/share/aclocal/ltversion.m4 /usr/share/aclocal/ltsugar.m4 /usr/share/aclocal/lt~obsolete.m4 >>aclocal.m4

then,
$./buildconf
$./configure

worked without problems here at least

---

### Post by xtrakt on 2010-01-10
> **SevenMachines said:**
> add the macros to aclocal in the source root dir of php-gtk

$cat /usr/share/aclocal/ltoptions.m4 /usr/share/aclocal/ltversion.m4 /usr/share/aclocal/ltsugar.m4 /usr/share/aclocal/lt~obsolete.m4 >>aclocal.m4

then,
$./buildconf
$./configure

worked without problems here at least

I managed to compile 2.0.0 with these instructions:

[http://blog.pabluk.com.ar/2009/01/compilando-php-gtk2-en-ubuntu-810.html](http://blog.pabluk.com.ar/2009/01/compilando-php-gtk2-en-ubuntu-810.html)

But thanks for the fast reply, I'll try to compile 2.0.1 some day with your instructions.

---

### Post by wiscalico on 2010-02-18
I've got it compiling an put it in [my PPA]("https://launchpad.net/~jacob-emcken/+archive/ppa/")... for those too lazy to build themselves :)

It is build with the following: --with-extra --with-html --with-libsexy --with-spell --enable-php-gtk --enable-scintilla --with-mozembed

---

