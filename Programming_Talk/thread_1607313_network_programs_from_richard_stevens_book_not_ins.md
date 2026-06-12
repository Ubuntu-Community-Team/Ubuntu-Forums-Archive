---
title: "network programs from richard stevens book not installing"
date: 2010-10-27
forum: Programming Talk
---

### Post by jamesbon on 2010-10-27
I am learning network programming via a book of Richard Stevens.
The sample source codes are given here
[http://www.unpbook.com/unpv13e.tar.gz](http://www.unpbook.com/unpv13e.tar.gz)
I downloaded and unzipped the file in /usr/src folder.
As per the instructions given in README of downloaded archive I did 
```

./configure
cd lib
make 
cd ../libfree
make

```I got this error
```

gcc -I../lib -g -O2 -D_REENTRANT -Wall   -c -o inet_ntop.o inet_ntop.c
inet_ntop.c: In function &#8216;inet_ntop&#8217;:
inet_ntop.c:61: error: argument &#8216;size&#8217; doesn&#8217;t match prototype
/usr/include/arpa/inet.h:65: error: prototype declaration
make: *** [inet_ntop.o] Error 1
```
Searching this in Google did not gave any useful information
[http://www.google.com/search?client=ubuntu&channel=fs&q=%2Fusr%2Finclude%2Farpa%2Finet.h%3A65%3A+error%3A+prototype+declaration&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=%2Fusr%2Finclude%2Farpa%2Finet.h%3A65%3A+error%3A+prototype+declaration&ie=utf-8&oe=utf-8)
I am not clear as how to proceed from here and where to proceed.

---

### Post by Arndt on 2010-10-27
> **jamesbon said:**
> I am learning network programming via a book of Richard Stevens.
The sample source codes are given here
[http://www.unpbook.com/unpv13e.tar.gz](http://www.unpbook.com/unpv13e.tar.gz)
I downloaded and unzipped the file in /usr/src folder.
As per the instructions given in README of downloaded archive I did 
```

./configure
cd lib
make 
cd ../libfree
make

```I got this error
```

gcc -I../lib -g -O2 -D_REENTRANT -Wall   -c -o inet_ntop.o inet_ntop.c
inet_ntop.c: In function ‘inet_ntop’:
inet_ntop.c:61: error: argument ‘size’ doesn’t match prototype
/usr/include/arpa/inet.h:65: error: prototype declaration
make: *** [inet_ntop.o] Error 1
```
Searching this in Google did not gave any useful information
[http://www.google.com/search?client=ubuntu&channel=fs&q=%2Fusr%2Finclude%2Farpa%2Finet.h%3A65%3A+error%3A+prototype+declaration&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=%2Fusr%2Finclude%2Farpa%2Finet.h%3A65%3A+error%3A+prototype+declaration&ie=utf-8&oe=utf-8)
I am not clear as how to proceed from here and where to proceed.

I'm not fully clear either, but the manual page for inet_ntop has this note:

CONFORMING TO
       POSIX.1-2001.  Note that RFC 2553 defines a prototype  where  the  last
       argument  size is of type size_t.  Many systems follow RFC 2553.  Glibc
       2.0 and 2.1 have size_t, but 2.2 and later have socklen_t.


Apparently socklen_t and size_t are not the same thing on your system (or mine, probably, but I didn't try to compile). You can get the code working by changing size_t to socklen_t, perhaps.

---

### Post by dwhitney67 on 2010-10-27
Something you should know about Richard Stevens... he is deceased.

His book, first published in 1990, was and still is a gem.  Unfortunately, however, it was developed for UNIX environments, not Linux.  Secondly, Linux in itself has matured over the years, and it's supported compilers have too.  Thus it is doubtful that the source code will build.

To obtain the latest version of the source code from R. Stevens, go to his website:  [http://www.kohala.com/start/unpv22e/unpv22e.html](http://www.kohala.com/start/unpv22e/unpv22e.html)
(yes, in almost every location on Earth, it is still legal to maintain a website even if you are deceased).

P.S.  22e is the latest version of the source code, which as I found out, does not build on Ubuntu 10.04 LTS.  If you want working code, you will need to fix the errors yourself.

---

### Post by jamesbon on 2010-10-28
Thanks a lot for the link you gave.
In case if that code will work on some old edition of Ubuntu let me know I will install that on my machine.

---

### Post by gmargo on 2010-10-28
> **dwhitney67 said:**
> P.S.  22e is the latest version of the source code,.

I believe you're confusing Volume 1 (sockets) and Volume 2 (ipc) of Unix Network Programming.  The original poster is using the latest version of the Volume 1 code.  22e is for Volume 2.

Here's a list of three books (with 2 editions of Vol 1) lifted from Wikipedia: [http://en.wikipedia.org/wiki/W._Richard_Stevens](http://en.wikipedia.org/wiki/W._Richard_Stevens)

1998 - *UNIX Network Programming, Volume 1, Second Edition: Networking APIs: [Sockets]("http://en.wikipedia.org/wiki/Berkeley_Sockets") and [XTI]("http://en.wikipedia.org/wiki/X/Open_Transport_Interface")* - [ISBN 0-13-490012-X]("http://en.wikipedia.org/wiki/Special:BookSources/013490012X")
 1999 - *UNIX Network Programming, Volume 2, Second Edition: [Interprocess Communications]("http://en.wikipedia.org/wiki/Interprocess_Communication")* - [ISBN 0-13-081081-9]("http://en.wikipedia.org/wiki/Special:BookSources/0130810819")
 2003 - *UNIX Network Programming Volume 1, Third Edition: The Sockets Networking API* - [ISBN 0-13-141155-1]("http://en.wikipedia.org/wiki/Special:BookSources/0131411551") (with Bill Fenner, and Andrew M. Rudoff)


Here's a list of web sites for each version and edition, where the appropriate source code can be downloaded:

Volume 1, 2nd edition web site: [http://www.kohala.com/start/unpv12e.html](http://www.kohala.com/start/unpv12e.html)
Volume 2, 2nd edition web site: [http://www.kohala.com/start/unpv22e/unpv22e.html](http://www.kohala.com/start/unpv22e/unpv22e.html)
Volume 1, 3rd edition web site: [http://unpbook.com/](http://unpbook.com/)
[URL="http://www.kohala.com/start/unpv22e/unpv22e.html"]
[/URL]

---

### Post by jamesbon on 2010-10-28
I want to know one more thing in case the programs from book do not compile and work I still would like to work on this part.What project should I pick up and do ( I am beginner) I have by now written basic client server programs in C.

---

