---
title: "libtool error"
date: 2009-03-21
forum: Packaging and Compiling Programs
---

### Post by pegal_linux on 2009-03-21
I'm try make a source in intrepid. But i'm get error message

% make
```
make  all-recursive
make[1]: Entering directory `/home/wirasto/v2mp3'
Making all in src
make[2]: Entering directory `/home/wirasto/v2mp3/src'
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o v2mp3  main.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   -pthread -lgnomevfs-2 -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -lgobject-2.0 -lglib-2.0   
../libtool: line 824: X--tag=CC: command not found
../libtool: line 857: libtool: ignoring unknown tag : command not found
../libtool: line 824: X--mode=link: command not found
../libtool: line 991: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 992: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 2236: X-g: command not found
../libtool: line 2236: X-O2: command not found
../libtool: line 2405: Xv2mp3: command not found
X: user not authorized to run the X server, aborting.
../libtool: line 2417: Xv2mp3: command not found
../libtool: line 2425: mkdir /.libs: No such file or directory
mkdir: cannot create directory `/.libs': Permission denied
make[2]: *** [v2mp3] Error 1
make[2]: Leaving directory `/home/wirasto/v2mp3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/wirasto/v2mp3'
make: *** [all] Error 2

```

How fix it ?
Thank's

---

