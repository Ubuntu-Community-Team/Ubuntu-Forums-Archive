---
title: "Using library problem"
date: 2010-03-12
forum: Programming Talk
---

### Post by fmigpaulo on 2010-03-12
Hi,
i'm a computer science student with some programming background (c, c++ and java).

Here's were problems may start: I've installed LORCON2 (a library for injecting 802.11 packets)
```

./configure --prefix=/usr && make && sudo make install

```

edited /etc/ld.so.conf
```

include /etc/ld.so.conf.d/*.conf
include /usr/local/lib

```
and updated it: sudo ldconfig

After that, i've created an example.c file, with code presented as example in [http://802.11ninja.net/docs/lorcon.3.html](http://802.11ninja.net/docs/lorcon.3.html)
When i try to compile:
```

sample.c:4:21: error: tx80211.h: No such file or directory
sample.c:5:28: error: tx80211_packet.h: No such file or directory
sample.c: In function ‘usage’:
sample.c:19: warning: assignment makes pointer from integer without a cast
sample.c:25: error: dereferencing pointer to incomplete type
sample.c:26: error: dereferencing pointer to incomplete type
sample.c: In function ‘main’:
sample.c:41: error: storage size of ‘in_tx’ isn’t known
sample.c:42: error: storage size of ‘in_packet’ isn’t known
sample.c:54: error: ‘INJ_NODRIVER’ undeclared (first use in this function)
sample.c:54: error: (Each undeclared identifier is reported only once
sample.c:54: error: for each function it appears in.)
sample.c:69: error: ‘TX80211_CAP_CTRL’ undeclared (first use in this function)
sample.c:76: error: ‘TX80211_FUNCMODE_INJMON’ undeclared (first use in this function)
sample.c:78: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
sample.c:85: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
sample.c:92: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
sample.c:104: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’

```

I've looked for the location of tx80211.h in my computer (to do someting like $ gcc sample.c -o sample -I /finded_dir -lorcon) without sucess locating it.
After download tx80211.h, tx80211.c and tx80211_packet.h from 802.11ninja.net/lorcon/browser/trunk/ the "INJ_NODRIVER undeclared" keep me still.

I'm a noob! Can someone please help?

---

### Post by gmargo on 2010-03-12
When you did a "make install", the installation process copied those tx*.h file somewhere.  Probably into /usr/include/lorcon/.  But your example program expects those .h files in the current directory or somewhere along the include directory search path.  Change the include directive in the example program to:
```
#include <lorcon/[tx80211.h]("file:///usr/include/tx80211.h")>
#include <lorcon/[tx80211_packet.h]("file:///usr/include/tx80211.h")>
```Adjust "lorcon" to reflect the actual location under /usr/include/.  Alternatively, you can add to the directory search path by adding "-I /usr/include/lorcon" to your CFLAGS.

In general for user-added libraries, you should use --prefix=/usr/local or /opt/xxx, but not /usr.

---

### Post by fmigpaulo on 2010-03-12
Success.
I've found that this headers are no longer included in the library.
About the rest of the errors, the linker option is now -lorcon2 and not -lorcon.

[quote="gmargo"]you should use --prefix=/usr/local[/quote]
Understood.

How about this steep? Can you explain why it as to be made (or what changes makes to the system):
$ gedit /etc/ld.so.conf
```

include /etc/ld.so.conf.d/*.conf
include /usr/local/lib

```


Previosely i've found this error:
ex_lib.so: cannot open shared object file: No such file or directory

I've "fixed it" by:
cp /usr/local/lib/ex_lib.so /usr/lib

It as someting to have with that? 


---------------------------------------------------------------------------------------------------------
Previous output information:

Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

---

### Post by dwhitney67 on 2010-03-12
> **fmigpaulo said:**
> 
How about this steep? Can you explain why it as to be made (or what changes makes to the system):
$ gedit /etc/ld.so.conf
```

include /etc/ld.so.conf.d/*.conf
include /usr/local/lib

```

Wrong, but you were on the right track.  Remove the 'include' portion of the statement, so you are left with merely '/usr/local/lib'.  Alternatively, and I'm surprised you do not have this, is to look in the /etc/ld.so.conf.d directory for a file called libc.conf; it should contain /usr/local/lib.  If you do not have the file, IMO you should create it.

> **fmigpaulo said:**
> 
Previosely i've found this error:
ex_lib.so: cannot open shared object file: No such file or directory

I've "fixed it" by:
cp /usr/local/lib/ex_lib.so /usr/lib

Wrong; don't do this.

After you finish editing the /etc/ld.so.conf (or using the alternative approach), make sure you update the system's library cache using the following command:
```

sudo ldconfig

```

---

### Post by fmigpaulo on 2010-03-14
Thank you both for helping me. With your help I could overcome the problems that prevented me from using the library. Many thanks.

---

### Post by rchtbhutani on 2010-08-12
hey i started working in the same manner as u did the problem i am facing is.Initially i was facing the same problem as urs but when i included those 2 files in same directory i came up wid this issue

code:

CogAP001:~/packetinjection# gcc tryone.c
In file included from tx80211.h:30,
                 from tryone.c:4:
tx80211_packet.h:26:9: warning: no newline at end of file
/tmp/ccF27sY6.o: In function `usage':
tryone.c:(.text+0x1a): undefined reference to `tx80211_getcardlist'
tryone.c:(.text+0xa4): undefined reference to `tx80211_freecardlist'
/tmp/ccF27sY6.o: In function `main':
tryone.c:(.text+0x11d): undefined reference to `tx80211_resolvecard'
tryone.c:(.text+0x174): undefined reference to `tx80211_init'
tryone.c:(.text+0x1ba): undefined reference to `tx80211_getcapabilities'
tryone.c:(.text+0x20e): undefined reference to `tx80211_setfunctionalmode'
tryone.c:(.text+0x254): undefined reference to `tx80211_geterrstr'
tryone.c:(.text+0x290): undefined reference to `tx80211_setchannel'
tryone.c:(.text+0x2d6): undefined reference to `tx80211_geterrstr'
tryone.c:(.text+0x30a): undefined reference to `tx80211_open'
tryone.c:(.text+0x350): undefined reference to `tx80211_geterrstr'
tryone.c:(.text+0x39f): undefined reference to `tx80211_txpacket'
tryone.c:(.text+0x3e5): undefined reference to `tx80211_geterrstr'
tryone.c:(.text+0x416): undefined reference to `tx80211_close'
collect2: ld returned 1 exit status


Please let me know what the isssue can be?

---

### Post by dwhitney67 on 2010-08-12
This is your issue...
```

gcc tryone.c

```
You are attempting to compile a source file, and it appears everything is ok.

However, as a minor issue, the library has a problem within tx80211_packet.h.  Pay attention to the warning that you posted earlier.

The more important issue is that you are not specifying which library to link against when linking tryone.c object file.  You should have something like:
```

gcc tryone.c -ltx80211

```
If your library is not called "libtx80211.so" (or .a), then substitute the name shown above, without the "lib" or the file extension.

This is basic stuff... hopefully your next reply will say "Thanks; problem solved!".

---

