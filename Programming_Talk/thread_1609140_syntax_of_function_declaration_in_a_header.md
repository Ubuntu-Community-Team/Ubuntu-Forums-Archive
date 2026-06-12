---
title: "syntax of function declaration in a header"
date: 2010-10-30
forum: Programming Talk
---

### Post by jamesbon on 2010-10-30
```

#include<sys/types.h>
#include<sys/socket.h>
#include<netinet/in.h>
#include<arpa/inet.h>
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<unistd.h>
#define REQUEST 400
#define REPLY 400
#define UDP_SERV_PORT 7777
#define TCP_SERV_PORT 8888
#define TTCP_SERV_PORT 9999
#define SA struct sockaddr *
void err_quit(const char *,...);
void err_sys(const char *,...);
int read_stream(int,char *,int);

int
main(int argc, char *argv[])        /* simple UDP client */
{
    struct sockaddr_in    serv;
    char                request[REQUEST], reply[REPLY];
    int                    sockfd, n;

    if (argc != 2)
        err_quit("usage: udpcli <IP address of server>");

    if ( (sockfd = socket(PF_INET, SOCK_DGRAM, 0)) < 0)
        err_sys("socket error");

    memset(&serv, 0, sizeof(serv));
    serv.sin_family         = AF_INET;
    serv.sin_addr.s_addr = inet_addr(argv[1]);
    serv.sin_port         = htons(UDP_SERV_PORT);

    /* form request[] ... */

    if (sendto(sockfd, request, REQUEST, 0,
               (SA) &serv, sizeof(serv)) != REQUEST)
        err_sys("sendto error");

    if ( (n = recvfrom(sockfd, reply, REPLY, 0,
                       (SA) NULL, (int *) NULL)) < 0)
        err_sys("recvfrom error");



    exit(0);
}
```
I am trying to compile above program below is the error I get
```
udpcli.c:(.text+0x3c): undefined reference to `err_quit'
udpcli.c:(.text+0x6e): undefined reference to `err_sys'
udpcli.c:(.text+0xf6): undefined reference to `err_sys'
udpcli.c:(.text+0x141): undefined reference to `err_sys'
collect2: ld returned 1 exit status

```
what is wrong with above declaration of functions?

---

### Post by Tony Flury on 2010-10-30
They "looK" like linker errors - not compiler errors.

Assuming that the err_quit and err_sys are defined in another module - are you including that other module as part of your link/compile command.

Can you post the command oin  you use to compile this programme.

---

### Post by jamesbon on 2010-10-30
I was compiling these programs as 
> cc udpcli.c -o udpcli.o 
I have now changed these two functions to printf.
The header file which I had has declaration of these functions as 
> void    err_quit(const char *, ...);
void    err_sys(const char *, ...);

I replaced all the occurence of err_quit and err_sys with printf and now the code I am trying is working.
This is the actual link [http://www.kohala.com/start/tcpipiv3.html](http://www.kohala.com/start/tcpipiv3.html)
from where I am trying the above program is from udpcli.c

---

### Post by Tony Flury on 2010-10-30
but which module (i.e. which ".c" or ".o" file) defines (not declares) those functions.

Unless you have a module which defines what those functions do then you will not be able to link your program into an executable application.

Edit : Looking at the tar file, It appears that they are defined in a file called error.c - did you compile that one ?

I think you might have to use the following command line : 

```

cc udpcli.c error.c -o udpcli

```
to compile and then link both files into a single application

That should work - but I am not a C expert.

Edit 2 : I just tried it - it does work.

---

### Post by Vox754 on 2010-10-30
> **jamesbon said:**
> I was compiling these programs as 

I have now changed these two functions to printf.
The header file which I had has declaration of these functions as 

I replaced all the occurence of err_quit and err_sys with printf and now the code I am trying is working.
This is the actual link [http://www.kohala.com/start/tcpipiv3.html](http://www.kohala.com/start/tcpipiv3.html)
from where I am trying the above program is from udpcli.c

You have only "declared" the functions, but you have not "defined" them.

A declaration is only a "wish". I wish to buy that car.
A definition is actually paying the money and buying that car.

This is your wish. You wish the function to be called "err_quit", to return nothing, and to accept a pointer of chars.
```

void err_quit(const char *,...);

```

You need to actually implement the function.
```

void err_quit(const char *name, ...) {
    printf("Print something") ;
    do_something_with_argument(name) ;
}

```

The declaration is typically placed in headers (*.h). While the definitions are typically in separate modules (*.c). The headers need to be included whenever that code is used, while each module needs to be compiled to actually make use of the code.

If you cannot comprehend this, you need to keep reading and learning. Read the FAQs.

---

### Post by nvteighen on 2010-10-30
Maybe you'll understand this better if you understand the purpose of function forward declarations.

C is a static-typed compiled language. That means the compiler needs to know the exact types of everything at compile-time... So, if you **define** a function in a module before you use it in the same module, the compiler won't need any forward declaration because, well, it already knows everything about the return value's and arguments' types.

So, this compiles perfectly:
```

#include <stdio.h>

void hey(int num)
{
    printf("Hey! %d\n", num);
}

int main(void)
{
    hey(5);
    return 0;
}

```

Now, let's say you want to write them inversely, e.g. because you like to have the main function at start so it's more visible. So, we define main before we define hey, but main uses hey, so we have to find a way to have the compiler know what the return value's and arguments' types are before the function is actually defined. To do this, we use a forward declaration:

```

/* "Inverted" case */
#include <stdio.h>

void hey(int);

int main(void)
{
    hey(5);
    return 0;
}

void hey(int num)
{
    printf("Hey! %d\n", num);
}

```

Observe that all the forward declaration needs is the types, not the variables' names (you can state them if you want). The syntax is exactly the same you use when defining a function, just that you skip the whole definition and use a semicolon to close it. Now the compiler will know the types beforehand and you can "use" hey before even telling what hey actually does.

Now, you also have to understand that all the compiler does is to turn C into ASM and all the assembler does is turn ASM into binary object code... All they want is enough information to do the translation right, but they don't check whether you actually defined stuff or not. That step, called "name resolution" is done by the linker in the compilation process's last stage. This is important because it explains why you also use a forward declaration (like in the "inverted" case) when using functions defined in different modules. When compiling, all you need to know are the types in order to translate C to ASM. The difference with the "inverted" case is that the linker will have to know where you're defining stuff, whereas in the "inverted" case the same file had the function's definition... just placed after "using" that function.

So, the errors you're getting are linker errors: "undefined reference" doesn't mean "Hey, I don't know what types this function is" (compiler), but "Hey, I don't find where to look this up" (linker's name resolution).

---

### Post by jamesbon on 2010-10-30
You people raised a good point.I understand that function definition should be complete no doubts about it.Since the programs are example codes in the book so I am not sure what the author is trying to do.
Tony thanks you correctly pointed error.c file I had not looked at that and the function is defined in it as

> void err_ret(const char *fmt, ...)
{
        va_list         ap;

        va_start(ap, fmt);
        err_doit(1, fmt, ap);
        va_end(ap);
        return;
}

I am not clear with following type of definition
> void err_ret(const char *fmt, ...)what do three dots after the comma above mean is it also a type of C declaration of function where you have not completely declared what the function does.
This type of function declaration is in error.c file.

In the tar ball following files are there
```

cliserv.h  Makefile  readstream.c  tcpcli.c      tcpserv.c      timer.c       ttcpcli.c      ttcphttpcli.c  ttcpserv.c      udpcli.c  udpclitime.c  udpservtime.c
error.c    README    sleepus.c     tcpclitime.c  tcpservtime.c  ttcpclibig.c  ttcpclitime.c  ttcpservbig.c  ttcpservtime.c  udpcli.o  udpserv.c
```> **nvteighen said:**
> Read the FAQs.

Give me a link to this as what should I read.

---

### Post by Tony Flury on 2010-10-31
> **jamesbon said:**
> 
I am not clear with following type of definition
what do three dots after the comma above mean is it also a type of C declaration of function where you have not completely declared what the function does.
This type of function declaration is in error.c file.


The three dots (called an ellipsis) is used in C to define a variable argument list, i,e. where the compiler does not know the number of arguments at compile time - think about what printf does.
The data passed to the function can be accessed by these constructs : 
```
 
va_list ap;

va_start(ap, fmt);
....
......
va_end(ap);

```

> 
In the tar ball following files are there
```

cliserv.h  Makefile  readstream.c  tcpcli.c      tcpserv.c      timer.c       ttcpcli.c      ttcphttpcli.c  ttcpserv.c      udpcli.c  udpclitime.c  udpservtime.c
error.c    README    sleepus.c     tcpclitime.c  tcpservtime.c  ttcpclibig.c  ttcpclitime.c  ttcpservbig.c  ttcpservtime.c  udpcli.o  udpserv.c
```

Give me a link to this as what should I read.

Start with the file called README.

---

