---
title: "gdf - gnome debugging framework"
date: 2007-09-18
forum: Programming Talk
---

### Post by jtgalway on 2007-09-18
I am trying to compile some software which was written a long time ago which uses libraries from GDF. I think there is a problem linking with these libraries because they were for a <2.4.x kernel and I am looking for something similar for >2.6 kernel.

I tried to grab the source code and compile it using my current Feisty Fawn installation, but it comes back with a complaint about not having something from gnome-libs which I am now trying to install from source. Then Berkeley db was needed for this install, so I added that. These aren't available from repos. And the berkeley db I installed is an obsolete version to be compliant. 

Now my configure for gnome-libs worked and the make crapped out with the following:

```
*** Scanning header files ***
cd . && ( \
        if test -f libart.types && grep -l '^..*$' libart.types > /dev/null ; then \
            CC="/bin/sh ../libtool --mode=compile gcc" LD="/bin/sh ../libtool --mode=link gcc" CFLAGS="" LDFLAGS="" gtkdoc-scangobj --module=libart ; \
        else \
            for i in libart.args libart.hierarchy libart.signals ; do \
               test -f $i || touch $i ; \
            done \
        fi )
cd . && \
          gtkdoc-scan --module=libart --source-dir=../ --ignore-headers="libart-features.h config.h acconfig.h libart.h" --deprecated-guards="GTK_ENABLE_BROKEN|GTK_DISABLE_DEPRECATED"  
touch scan-build.stamp
*** Rebuilding template files ***
cd . && gtkdoc-mktmpl --module=libart
=============================================================================
WARNING: 39 unused declarations.
  These can be found in libart-unused.txt.
  They should be added to libart-sections.txt in the appropriate place.
=============================================================================
touch tmpl-build.stamp
*** Building SGML ***
cd . && \
        gtkdoc-mkdb --module=libart --source-dir=../ 
78% symbol docs coverage (89 symbols documented, 0 symbols incomplete, 25 not documented)
See libart-undocumented.txt for a list of missing docs.
The doc coverage percentage doesn't include intro sections.
touch sgml-build.stamp
*** Building HTML ***
test -d ./html || mkdir ./html
cd ./html && gtkdoc-mkhtml libart ../libart.sgml
/usr/bin/jade:../sgml/art_svp.sgml:71:10:E: end tag for "PARA" omitted, but OMITTAG NO was specified
/usr/bin/jade:../sgml/art_svp.sgml:70:0: start tag was here
/usr/bin/jade:../libart.sgml:851:2:E: cannot find "fdl.sgml"; tried "../fdl.sgml", "/usr/local/share/sgml/fdl.sgml", "/usr/share/sgml/fdl.sgml"
make[4]: *** [html-build.stamp] Error 1
make[4]: Leaving directory `/home/john/ucdanalysis/src/gdf/vpro/temp/gnome-libs-1.4.2/libart_lgpl/doc'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/john/ucdanalysis/src/gdf/vpro/temp/gnome-libs-1.4.2/libart_lgpl'
make[2]: *** [all-recursive-am] Error 2
make[2]: Leaving directory `/home/john/ucdanalysis/src/gdf/vpro/temp/gnome-libs-1.4.2/libart_lgpl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/john/ucdanalysis/src/gdf/vpro/temp/gnome-libs-1.4.2'
make: *** [all-recursive-am] Error 2

```

Basically, is there any quick way of doing this and then getting the gdf code to compile or does anyone know of some package which might have the same files as the older gdf stuff rolled into it as an even quicker fix?

   John T

---

