---
title: "gnu oleo build error"
date: 2017-03-06
forum: Packaging and Compiling Programs
---

### Post by brucehohl on 2017-03-06
Hi All,
I ran into a build problem I am hoping someone can comment on.  Here is what I did:

Downloaded oleo from:
[http://ftp.gnu.org/pub/gnu/oleo/oleo-1.99.16.tar.gz](http://ftp.gnu.org/pub/gnu/oleo/oleo-1.99.16.tar.gz)

And Debian patches from:
[https://fossies.org/linux/misc/gsrc-2014.10.11.tar.gz/index_dc.html](https://fossies.org/linux/misc/gsrc-2014.10.11.tar.gz/index_dc.html)
-rw-r--r--     26616 2013-03-19 11:06 gnu/oleo/files/oleo-1.99.16-debian-patches.diff

Stepped through the patch and build:
    tar -zxvf oleo-1.99.16.tar.gz
    cd oleo-1.99.16
    patch -p2 -i ../oleo-1.99.16-debian-patches.diff
    ./configure --without-x --without-motif --without-xbae
    make

Configure and Make output are below.  
Oleo is an early spreadsheet program I am exploring just because I like data tools!
Thanks for any help, hints, etc.

**configure output:**
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking for POSIXized ISC... no
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for executable suffix... no
checking size of short... 2
checking size of int... 4
checking size of long... 8
checking if malloc debugging is wanted... no
checking for bison... bison -y
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for texi2html... yes
checking for perl... /usr/bin/perl
checking for gcc option to accept ANSI C... none needed
checking for function prototypes... yes
checking for waddch in -lncurses... yes
checking for ncurses.h... yes
checking for sys_errlist and sys_nerr... yes
checking for tputs in -lmytinfo... no
checking for setlocale in -lxpg4... no
checking for main in -lm... yes
checking for X... disabled
checking for pl_openpl_r in -lplot... no
checking for sp_begin_plot in -lsciplot... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for ANSI C header files... yes
checking for fcntl.h... yes
checking for limits.h... yes
checking for malloc.h... yes
checking for strings.h... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for locale.h... yes
checking for time.h... yes
checking for math.h... yes
checking for libintl.h... yes
checking for XltCreateFontChooser... no
checking for gsl_error in -lgsl... no
checking for mysql_connect in -lmysqlclient... no
checking for working const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for tm_zone in struct tm... yes
checking for working alloca.h... yes
checking for alloca... yes
checking return type of signal handlers... void
checking for strftime... yes
checking for vprintf... yes
checking for ftime... yes
checking for gethostname... yes
checking for gettimeofday... yes
checking for mktime... yes
checking for select... yes
checking for strdup... yes
checking for strstr... yes
checking for putenv... yes
checking for strcasecmp... yes
checking for strerror... yes
checking for getcwd... yes
checking for rename... yes
checking for sys/time.h... (cached) yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... yes
checking for obstacks... yes
checking for cupsGetPrinters in -lcups... no
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for main in -lxbase... no
checking for main in -lxdb... no
checking for off_t... yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for argz.h... yes
checking for limits.h... (cached) yes
checking for locale.h... (cached) yes
checking for nl_types.h... yes
checking for malloc.h... (cached) yes
checking for string.h... yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getcwd... (cached) yes
checking for munmap... yes
checking for putenv... (cached) yes
checking for setenv... yes
checking for setlocale... yes
checking for strchr... yes
checking for strcasecmp... (cached) yes
checking for strdup... (cached) yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for stpcpy... yes
checking for LC_MESSAGES... yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for libintl.h... (cached) yes
checking for gettext in libc... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  en nl fr
updating cache ./config.cache
creating ./config.status
creating Makefile
creating oleobug
creating doc/Makefile
creating doc/texi2html
creating lib/Makefile
creating src/Makefile
creating intl/Makefile
creating m4/Makefile
creating po/Makefile.in
creating Xresources/Makefile
creating examples/Makefile
creating oleo.spec
creating afm/Makefile
creating config.h

**make output:**
make  all-recursive
make[1]: Entering directory '/home/user1/oleo/gnu-src/oleo-1.99.16'
Making all in doc
make[2]: Entering directory '/home/user1/oleo/gnu-src/oleo-1.99.16/doc'
/usr/bin/perl ../doc/texi2html ./oleo.texi
Unescaped left brace in regex is deprecated, passed through in regex; marked by <-- HERE in m/\@(x|px|info|)ref{ <-- HERE ([^{}]+)(}?)/ at ../doc/texi2html line 3177.
Can't use 'defined(@array)' (Maybe you should just omit the defined()?) at ../doc/texi2html line 3793.
Makefile:386: recipe for target 'oleo.html' failed
make[2]: *** [oleo.html] Error 2
make[2]: Leaving directory '/home/user1/oleo/gnu-src/oleo-1.99.16/doc'
Makefile:239: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/user1/oleo/gnu-src/oleo-1.99.16'
Makefile:383: recipe for target 'all-recursive-am' failed
make: *** [all-recursive-am] Error 2

---

### Post by brucehohl on 2017-03-11
I got the Oleo build to complete by applying the following patch before ./configure && make.  This patch only removes offending code without any attempt to address the cause.  It's in the doc directory so probably no harm. There were some make warnings but the build completed and Oleo starts.

```
--- work/oleo-1.99.16/doc/texi2html.in
+++ work/oleo-1.99.16/doc/texi2html.in
3177c3177
<     while (/\@(x|px|info|)ref{([^{}]+)(}?)/) {
---
>     while (/\@(x|px|info|)ref\{([^{}]+)(}?)/) {
3793c3793
<     if ($name =~ /^appendix/ || defined(@appendix_sec_num)) {
---
>     if ($name =~ /^appendix/ || defined()) {
3795c3795
< 	if (defined(@appendix_sec_num)) {
---
> 	if (defined()) {
3803c3803
< 	if (defined(@normal_sec_num)) 
---
> 	if (defined()) 
```

---

