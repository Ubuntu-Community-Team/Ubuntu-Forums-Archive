---
title: "pcre linking"
date: 2011-04-19
forum: Programming Talk
---

### Post by jasonlfunk on 2011-04-19
I'm having trouble getting pcre to link with my program. Any ideas as to why?


```

$ make clean && make
rm -f *.o
cc -Wall -g -I.. -I/usr/local/include/libxml2 -I/usr/local/include -L/usr/lib -lpcre    -c -o example.o example.c
cc -Wall -g -I.. -I/usr/local/include/libxml2 -I/usr/local/include -L/usr/lib -lpcre    -c -o ps_dlp_api.o ps_dlp_api.c
cc -o example example.o ps_dlp_api.o 
ps_dlp_api.o: In function `ca_alg_matches':
/home/jasonfunk/workspace/dlpsdk/C/ps_dlp_api.c:1109: undefined reference to `pcre_exec'
collect2: ld returned 1 exit status
make: *** [example] Error 1
```

```
$ pcre-config --libs
-L/usr/lib -lpcre

```

```
$ uname -a
Linux jasonfunk-laptop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux
```

```
$ dpkg --get-selections | grep pcre
libpcre++0                                      deinstall
libpcre3                                        install
libpcre3-dev                                    install
libpcrecpp0                                     install

```

---

### Post by Some Penguin on 2011-04-19
-lpcre doesn't mean very much when you're compiling individual object files; you need to set it for the *linking* phase when you build the executable (e.g. in LDFLAGS if you're using a fairly traditional Makefile).  Your linking command doesn't have it.

---

