---
title: "Unix Network Programming : The Sockets Networking API"
date: 2012-01-08
forum: Programming Talk
---

### Post by arseshan on 2012-01-08
Hi,

 I've was trying to learn using the book Unix Network Programming : The Sockets Networking API, by W. Richard Stevens. Please help me with the following problem. 

 I downloaded the file unpv12ep-0.2.tar.gz from [http://www.kegel.com/unpv1/]("http://www.kegel.com/unpv1/")

 I did as per the suggestions but I came up with these errors.

 (I saved it in the templates directory)


```

arun@arun:~/Templates/unpv12e$ cd lib
arun@arun:~/Templates/unpv12e/lib$ make
gcc -g -O2 -D_REENTRANT -Wall   -c -o connect_nonb.o connect_nonb.c
In file included from connect_nonb.c:1:0:
unp.h:114:8: error: redefinition of &#8216;struct in_pktinfo&#8217;
/usr/include/i386-linux-gnu/bits/in.h:113:8: note: originally defined here
make: *** [connect_nonb.o] Error 1


arun@arun:~/Templates/unpv12e/libfree$ cd ../libgai
arun@arun:~/Templates/unpv12e/libgai$  make
gcc -g -O2 -D_REENTRANT -Wall   -c -o getaddrinfo.o getaddrinfo.c
In file included from gai_hdr.h:1:0,
                 from getaddrinfo.c:2:
unp.h:114:8: error: redefinition of &#8216;struct in_pktinfo&#8217;
/usr/include/i386-linux-gnu/bits/in.h:113:8: note: originally defined here
getaddrinfo.c: In function &#8216;getaddrinfo&#8217;:
getaddrinfo.c:58:6: error: &#8216;EAI_ADDRFAMILY&#8217; undeclared (first use in this function)
getaddrinfo.c:58:6: note: each undeclared identifier is reported only once for each function it appears in
getaddrinfo.c:116:21: error: &#8216;EAI_NODATA&#8217; undeclared (first use in this function)
make: *** [getaddrinfo.o] Error 1


arun@arun:~/Templates/unpv12e/libgai$  cd ../libroute
arun@arun:~/Templates/unpv12e/libroute$ make 
gcc -g -O2 -D_REENTRANT -Wall   -c -o get_rtaddrs.o get_rtaddrs.c
In file included from unproute.h:1:0,
                 from get_rtaddrs.c:1:
unp.h:114:8: error: redefinition of &#8216;struct in_pktinfo&#8217;
/usr/include/i386-linux-gnu/bits/in.h:113:8: note: originally defined here
In file included from get_rtaddrs.c:1:0:
unproute.h:3:45: fatal error: net/if_dl.h: No such file or directory
compilation terminated.
make: *** [get_rtaddrs.o] Error 1


arun@arun:~/Templates/unpv12e/libroute$ cd ../libxti
arun@arun:~/Templates/unpv12e/libxti$ make
gcc -g -O2 -D_REENTRANT -Wall   -c -o wrapxti.o wrapxti.c
In file included from unpxti.h:5:0,
                 from wrapxti.c:5:
unp.h:114:8: error: redefinition of &#8216;struct in_pktinfo&#8217;
/usr/include/i386-linux-gnu/bits/in.h:113:8: note: originally defined here
In file included from wrapxti.c:5:0:
unpxti.h:7:17: fatal error: xti.h: No such file or directory
compilation terminated.
make: *** [wrapxti.o] Error 1


arun@arun:~/Templates/unpv12e/libxti$ make
gcc -g -O2 -D_REENTRANT -Wall   -c -o wrapxti.o wrapxti.c
In file included from unpxti.h:5:0,
                 from wrapxti.c:5:
unp.h:114:8: error: redefinition of &#8216;struct in_pktinfo&#8217;
/usr/include/i386-linux-gnu/bits/in.h:113:8: note: originally defined here
In file included from wrapxti.c:5:0:
unpxti.h:7:17: fatal error: xti.h: No such file or directory
compilation terminated.
make: *** [wrapxti.o] Error 1


arun@arun:~/Templates/unpv12e/libxti$ cd ../intro 
arun@arun:~/Templates/unpv12e/intro$  make daytimetcpcli
gcc -g -O2 -D_REENTRANT -Wall   -c -o daytimetcpcli.o daytimetcpcli.c
In file included from daytimetcpcli.c:1:0:
unp.h:114:8: error: redefinition of &#8216;struct in_pktinfo&#8217;
/usr/include/i386-linux-gnu/bits/in.h:113:8: note: originally defined here
make: *** [daytimetcpcli.o] Error 1



```


 Without solving these errors, I guess I can't use the book much. I'd really appreciate it if someone could help me out here. I thank you all for you time and efforts in advance.

---

### Post by The Cog on 2012-01-08
Moved to Programming Talk, where it should get a more appropriate audience.

I do note that the referred download page says it was last updated 10 years ago, and that there were problems with Linux compatibility even then. I suspect there may be quite a lot of work in getting the code modified to work on current Linux systems.

---

