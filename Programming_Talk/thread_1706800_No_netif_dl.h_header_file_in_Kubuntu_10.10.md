---
title: "No net/if_dl.h header file in Kubuntu 10.10"
date: 2011-03-14
forum: Programming Talk
---

### Post by jailed on 2011-03-14
Hi,

I'm trying to compile programs from the [Unix network programming book]("http://www.unpbook.com/") (3rd ed.). When I do a make in the libroute directory of the [source code]("http://www.unpbook.com/src.html"), I get the following error:

```
$ make                                                                                                                               
gcc -I../lib -g -O2 -D_REENTRANT -Wall   -c -o get_rtaddrs.o get_rtaddrs.c                                                                                                          
In file included from get_rtaddrs.c:1:                                                                                                                                              
unproute.h:3: fatal error: _*net/if_dl.h: No such file or directory*_                                                                                                                   
compilation terminated.                                                                                                                                                             
make: *** [get_rtaddrs.o] Error 1               
```

As can be seen I do not have the required header file. I tried to search for the header file using apt-file: 
```
$ apt-file search if_dl.h                                                                                                            
libnewlib-dev: /usr/lib/newlib/i686-linux-gnu/include/net/if_dl.h      
```

I get the *[COLOR="SeaGreen"]libnewlib-dev[/COLOR]* package, which is for embedded systems. Here is an excerpt from ```
apt-cache show libnewlib-dev
```
 > newlib C library (devel)                                                                                                                                               
 Newlib is a C library intended for use on embedded systems.

So which package contains the [COLOR="SeaGreen"]net/if_dl.h[/COLOR] header. 

Thank you.

---

### Post by dwhitney67 on 2011-03-14
As the title of the book implies, the code you have obtained is applicable for compiling and use under UNIX.  UNIX and Linux are not the same.

You may need to port the s/w to compile/run under Linux.

If you are merely attempting to learn about socket programming, then you may have better luck referencing the material documented here:  [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

### Post by jailed on 2011-03-14
> **dwhitney67 said:**
> As the title of the book implies, the code you have obtained is applicable for compiling and use under UNIX.  UNIX and Linux are not the same.


Thank you dwhitney67, after doing some search and also asking folks in stackoverflow, I found the same answer (that it was specific to BSD), and we need to port the headers for it to work in Linux.   

> **dwhitney67 said:**
> 
If you are merely attempting to learn about socket programming, then you may have better luck referencing the material documented here:  [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

Thanks for the link. Looks like this is another widely accepted document for socket programming in Linux.

Thank you.

---

