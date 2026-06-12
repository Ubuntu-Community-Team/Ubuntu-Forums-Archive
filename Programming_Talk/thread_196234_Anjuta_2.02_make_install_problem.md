---
title: "Anjuta 2.02 make install problem"
date: 2006-06-13
forum: Programming Talk
---

### Post by weijie90 on 2006-06-13
Hi,
i built anjuta from source, but "sudo make install" gives me this problem:

```
Making install in devhelp
make[2]: Entering directory `/home/di/Desktop/anjuta-2.0.2/plugins/devhelp'
make[3]: Entering directory `/home/di/Desktop/anjuta-2.0.2/plugins/devhelp'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/pixmaps/anjuta" || mkdir -p -- "/usr/local/share/pixmaps/anjuta"
 /usr/bin/install -c -m 644 'anjuta-devhelp-plugin.png' '/usr/local/share/pixmaps/anjuta/anjuta-devhelp-plugin.png'
test -z "/usr/local/lib/anjuta" || mkdir -p -- "/usr/local/lib/anjuta"
 /usr/bin/install -c -m 644 'anjuta-devhelp.plugin' '/usr/local/lib/anjuta/anjuta-devhelp.plugin'
test -z "/usr/local/share/anjuta/ui" || mkdir -p -- "/usr/local/share/anjuta/ui" /usr/bin/install -c -m 644 'anjuta-devhelp.ui' '/usr/local/share/anjuta/ui/anjuta-devhelp.ui'
test -z "/usr/local/lib/anjuta" || mkdir -p -- "/usr/local/lib/anjuta"
 /bin/sh ../../libtool --mode=install /usr/bin/install -c  'libanjuta-devhelp.la' '/usr/local/lib/anjuta/libanjuta-devhelp.la'
libtool: install: warning: relinking `libanjuta-devhelp.la'
(cd /home/di/Desktop/anjuta-2.0.2/plugins/devhelp; /bin/sh ../../libtool  --tag=CC --mode=relink gcc -O0 -g -Wall -Wmissing-prototypes -Wmissing-declarations -Wparentheses -Wpointer-arith -g -O2 -o libanjuta-devhelp.la -rpath /usr/local/lib/anjuta plugin.lo htmlview.lo -pthread -ldevhelp-1 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnome-keyring -lxml2 -lz -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lgtk-x11-2.0 -lgnomevfs-2 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lbonobo-2 -lgconf-2 -lgobject-2.0 -lbonobo-activation -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 ../../libanjuta/libanjuta.la )
gcc -shared  .libs/plugin.o .libs/htmlview.o  -Wl,--rpath -Wl,/usr/local/lib -L/usr/lib -ldevhelp-1 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnome-keyring -lxml2 -lz -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lgtk-x11-2.0 -lgnomevfs-2 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lbonobo-2 -lgconf-2 -lgobject-2.0 -lbonobo-activation -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/local/lib -lanjuta  -pthread -Wl,-soname -Wl,libanjuta-devhelp.so.0 -o .libs/libanjuta-devhelp.so.0.0.0
/usr/bin/install -c .libs/libanjuta-devhelp.so.0.0.0T /usr/local/lib/anjuta/libanjuta-devhelp.so.0.0.0
(cd /usr/local/lib/anjuta && { ln -s -f libanjuta-devhelp.so.0.0.0 libanjuta-devhelp.so.0 || { rm -f libanjuta-devhelp.so.0 && ln -s libanjuta-devhelp.so.0.0.0 libanjuta-devhelp.so.0; }; })
(cd /usr/local/lib/anjuta && { ln -s -f libanjuta-devhelp.so.0.0.0 libanjuta-devhelp.so || { rm -f libanjuta-devhelp.so && ln -s libanjuta-devhelp.so.0.0.0 libanjuta-devhelp.so; }; })
/usr/bin/install -c .libs/libanjuta-devhelp.lai /usr/local/lib/anjuta/libanjuta-devhelp.la
/usr/bin/install: cannot stat `.libs/libanjuta-devhelp.lai': No such file or directory
make[3]: *** [install-pluginLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/di/Desktop/anjuta-2.0.2/plugins/devhelp'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/di/Desktop/anjuta-2.0.2/plugins/devhelp'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/di/Desktop/anjuta-2.0.2/plugins'
make: *** [install-recursive] Error 1
di@di-desktop:~/Desktop/anjuta-2.0.2$


```

`.libs/libanjuta-devhelp.lai': seems to be a spelling error?

please help, thanks!

---

