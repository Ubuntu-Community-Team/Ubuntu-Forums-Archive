---
title: "makefile errors"
date: 2010-10-30
forum: Programming Talk
---

### Post by jamesbon on 2010-10-30
The network programming book of Richard Stevens had some errors in its functions.
Volume three code is available on internet as ttcpcliserv.tar 
[http://www.kohala.com/start/ttcpcliserv.tar](http://www.kohala.com/start/ttcpcliserv.tar)
I found many example codes on this tar ball were using 
err_sys and err_quit functions which were defined in the header 
as file cliserv.h as ```

void    err_quit(const char *, ...);
void    err_sys(const char *, ...);

```I could not understand above type of declaration of err_quit and err_sys (never seen such a function definition)
Replaced these words by printf in all c codes of above tar ball
```

sed -i 's/err_sys/printf/g' ./*.c
sed -i 's/err_quit/printf/g' ./*.c
```The programs which I have read with first chapter of Vol3 of book
 now seem to have worked and the header file cliserv.h which was included in each source code of example 
of book 
had declaration of 
including the header files as 
```

#include        <sys/types.h>
#include        <sys/socket.h>
#include        <netinet/in.h>
#include        <arpa/inet.h>
#include        <stdio.h>
#include        <stdlib.h>
#include        <string.h>
#include        <unistd.h>

```

so I added this to each c file of that tar ball.So till now all the codes which I have tried to work or make work have worked till here.

Now the actual question begins e tar ball is coming with a 
Makefile to be able to compile the source codes with examples in book with make.
When I compile that Makefile I get some errors what should I modify in the Makefile if any one can understand I am giving the Makefile and the corresponding errors

```

# Change the following as required:
CC    = gcc

CFLAGS    = -Wall
#CFLAGS    = -ansi -Wall -Dsun -D__STDC__=0 -DMSG_EOF=0
# My flags for gcc/solaris 2.3:  -ansi -Wall -Dsun -D__STDC__=0
#   (Solaris -DMSG_EOF just to let me compile it under Solaris; it won't run)
# Add in -DGCC_STRUCT_PROBLEM for gcc versions 1.x under SunOS 4.x
# Add in -D__STDC__=0 for gcc under Solaris 2 (for Sun's screwy headers)
# Add in -D_BSD=44 for AIX 3.2.2 (see <sys/socket.h>)
# Add in -D_SOCKADDR_LEN for DEC OSF/1 (see <sys/socket.h>)

# Following line for SVR4, Solaris 2.x; 2.5 no longer requires libucb.a.
#LIBS    = ./libmisc.a /usr/ucblib/libucb.a -lsocket -lnsl

# Following line for 4.4BSD, BSD/386, SunOS 4.x, AIX 3.2.2, OSF/1
LIBS    = ./libmisc.a

PROGS =    udpcli udpserv tcpcli tcpserv ttcpcli ttcpserv \
    ttcpclibig ttcpservbig ttcphttpcli \
    udpclitime udpservtime tcpclitime tcpservtime ttcpclitime ttcpservtime

all:    ${PROGS}

udpcli:        udpcli.o
        ${CC} ${CCFLAGS} -o $@ udpcli.o ${LIBS}

udpserv:    udpserv.o
        ${CC} ${CCFLAGS} -o $@ udpserv.o ${LIBS}

tcpcli:        tcpcli.o readstream.o
        ${CC} ${CCFLAGS} -o $@ tcpcli.o readstream.o ${LIBS}

tcpserv:    tcpserv.o readstream.o
        ${CC} ${CCFLAGS} -o $@ tcpserv.o readstream.o ${LIBS}

ttcpcli:    ttcpcli.o readstream.o
        ${CC} ${CCFLAGS} -o $@ ttcpcli.o readstream.o ${LIBS}

ttcpserv:    ttcpserv.o readstream.o
        ${CC} ${CCFLAGS} -o $@ ttcpserv.o readstream.o ${LIBS}

ttcpclibig:    ttcpclibig.o readstream.o
        ${CC} ${CCFLAGS} -o $@ ttcpclibig.o readstream.o ${LIBS}

ttcpservbig:    ttcpservbig.o readstream.o
        ${CC} ${CCFLAGS} -o $@ ttcpservbig.o readstream.o ${LIBS}

ttcphttpcli:    ttcphttpcli.o readstream.o
        ${CC} ${CCFLAGS} -o $@ ttcphttpcli.o readstream.o ${LIBS}

udpclitime:    udpclitime.o timer.o
        ${CC} ${CCFLAGS} -o $@ udpclitime.o timer.o ${LIBS}

udpservtime:    udpservtime.o timer.o
        ${CC} ${CCFLAGS} -o $@ udpservtime.o timer.o ${LIBS}

tcpclitime:    tcpclitime.o readstream.o timer.o
        ${CC} ${CCFLAGS} -o $@ tcpclitime.o readstream.o timer.o ${LIBS}

tcpservtime:    tcpservtime.o readstream.o timer.o
        ${CC} ${CCFLAGS} -o $@ tcpservtime.o readstream.o timer.o ${LIBS}

ttcpclitime:    ttcpclitime.o readstream.o timer.o
        ${CC} ${CCFLAGS} -o $@ ttcpclitime.o readstream.o timer.o ${LIBS}

ttcpservtime:    ttcpservtime.o readstream.o timer.o
        ${CC} ${CCFLAGS} -o $@ ttcpservtime.o readstream.o timer.o ${LIBS}

clean:
        rm -f ${PROGS} core core.* *.o temp.* *.out typescript*
```and error when I compile this is 
```
gcc  -o udpcli udpcli.o ./libmisc.a
gcc: ./libmisc.a: No such file or directory
make: *** [udpcli] Error 1

```What should I modify in Makefile to make it work?
My machine is Ubuntu 10.04 64 bit
```
 gcc --version
gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


```

---

### Post by gmargo on 2010-10-30
> ```

void    err_quit(const char *, ...);
void    err_sys(const char *, ...);

```I could not understand above type of declaration of err_quit and err_sys (never seen such a function definition)That is a prototype for a function with a variable number of arguments.  In this case the function has at least one argument.  Look at the **sprintf(3)** man page - you'll see it there too.

> 
Replaced these words by printf in all c codes of above tar ball
```

sed -i 's/err_sys/printf/g' ./*.c
sed -i 's/err_quit/printf/g' ./*.c
```The functions are defined in the **error.c** file.  The **Makefile** does not compile that file, but the **README** explains it.

---

### Post by dwhitney67 on 2010-10-30
From the gcc error, it would seem to me that you need to build libmisc.a.

Btw, I thought your intent was learn about socket programming.  Instead, it seems your focus is to learn how to fix a "broken" package of s/w that won't compile under Linux.  It's a worthy venture, but which has nothing to do with socket programming.

---

### Post by gmargo on 2010-10-30
Attached is a small patch that makes this code compile cleanly on 64-bit 10.10 Maverick.  I have not tested the programs at all.

Download patch and apply to the source code directory with:
```

patch -p1 < ttcpcliserv_maverick.patch.txt

```

---

### Post by jamesbon on 2010-10-30
@gmargo 
Wow your patch worked perfectly and make worked without any errors I am using 10.04 64 bit.Thanks a lot for this wonderful work.
Tell me what should I be reading if I were to be able to write patch as you wrote because there are two more zip files of the book which may also need patches in same way.

@dwhitney67
I understand your point.But the thing is I am trying to understand the example codes from the book.
Since I am a beginner so I thought that the example codes should work so that what ever I am reading I be able to appreciate that.If there is any problem in these examples I would like to fix this.

---

### Post by johnl on 2010-10-30
I think you might be better served with a better example.

Check out the famous [beej's guide to network programming](http://beej.us/guide/bgnet/), which along with examples has enough documentation and explanation for pretty much anyone.

---

### Post by jamesbon on 2010-10-31
> **johnl said:**
> I think you might be better served with a better example.

Check out the famous [beej's guide to network programming]("http://beej.us/guide/bgnet/"), 
Yes I have read that and practiced the programs from Beej's network programming guide.Now I am trying Richard Stevens books.

---

