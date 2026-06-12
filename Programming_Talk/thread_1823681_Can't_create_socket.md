---
title: "Can't create socket"
date: 2011-08-12
forum: Programming Talk
---

### Post by xq2003 on 2011-08-12
Hi folks,

I'm quite new to using sockets, so I thought I'd simply try to create one. I tried to create a socket using a simple C script like this:
```

#include <sys/types.h>
#include <sys/socket.h>

int main()
{
  int s = socket(AF_INET, SOCK_STREAM, 0);
  printf("%d\n", s);

  return 0;
}

```However, when run, the program returns -1 as the return value of socket(). When I tried the command directly in bash, I got:
```

root@vbox-ubuntu:~# socket(AF_INET, SOCK_STREAM, 0)
bash: syntax error near unexpected token `AF_INET,'

```I've searched everywhere for a solution, I even looked into the /usr/include/sys/socket.h, but to no avail. I hope, someone can help :confused:

---

### Post by karlson on 2011-08-12
> **xq2003 said:**
> Hi folks,

I'm quite new to using sockets, so I thought I'd simply try to create one. I tried to create a socket using a simple C script like this:
```

#include <sys/types.h>
#include <sys/socket.h>

int main()
{
  int s = socket(AF_INET, SOCK_STREAM, 0);
  printf("%d\n", s);

  return 0;
}

```


First of all it's not a script.  Second you need to look at the value of the "errno" variable to see why this is failing.

> However, when run, the program returns -1 as the return value of socket(). When I tried the command directly in bash, I got:
```

root@vbox-ubuntu:~# socket(AF_INET, SOCK_STREAM, 0)
bash: syntax error near unexpected token `AF_INET,'

```I've searched everywhere for a solution, I even looked into the /usr/include/sys/socket.h, but to no avail. I hope, someone can help :confused:

The bash command that you have tried requires "socket" package to be installed and it may not be called in this fashion.

---

### Post by dwhitney67 on 2011-08-12
> **xq2003 said:**
> I hope, someone can help 

There's nothing wrong with the **C program** that you presented, other than you forgot to include stdio.h for the printf().

Did you compile the program?

Why are you logged in as "root"?

P.S.  Refer to this wonderful tutorial for your socket questions:  [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

### Post by xq2003 on 2011-08-12
> **dwhitney67 said:**
> Did you compile the program?

Yes, I did compile the C source code and ran the program afterwards.

[QUOTE=karlson]The bash command that you have tried requires "socket" package to be installed and it may not be called in this fashion.[/QUOTE]

I thought I could run this command right from the bash? After all, there is a manpage for the socket command.

---

### Post by dwhitney67 on 2011-08-12
> **xq2003 said:**
> 
I thought I could run this command right from the bash? After all, there is a manpage for the socket command.

The manpage you are referring to is related to the function available in the C library (btw, socket is described in sections 2, 3p, and 7 of the man-pages).

---

### Post by johnl on 2011-08-12
Try this.

```
include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h> /* IPPROTO_TCP */
#include <stdio.h>  /* printf() */
#include <unistd.h> /* close()  */

int main(int argc, char* argv[])
{
    /* I assume you wanted a TCP socket.  Don't pass 0, use the constant. */
    int fd = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
    if (fd < 0) {
        /* if something is going wrong this will give you more information. */
        perror("socket");
    } else {
        printf("success!\n");
    }

    close(fd);

    return 0;
}

```

If it still fails with those changes, the output of perror() should give you some hint as to the problem.

---

### Post by karlson on 2011-08-12
> **xq2003 said:**
> I thought I could run this command right from the bash? After all, there is a manpage for the socket command.

The fact that there is a man page for the socket **C function** doesn't mean that it's a command.  If you want a socket command you need to install it
```

$ sudo apt-get install socket

```

---

### Post by dwhitney67 on 2011-08-12
...

---

### Post by karlson on 2011-08-12
> **dwhitney67 said:**
> 
Seriously, Karlson, do you really think the OP is looking for a command-line solution??????????

I don't think that discussion of my implied lunacy is a matter for public eyes.

As far as the OP is concerned I have no idea what the intent really was especially in the view that OP seem to lack an understanding of the difference between compiled program and a shell script.  So if this is an attempt to learn C/C++ programming then I think that pointers to the literature from this thread [http://ubuntuforums.org/showthread.php?t=1790791](http://ubuntuforums.org/showthread.php?t=1790791) would be more advantageous then the suggestion of what to do for creating the socket.

Now if the intent was to have a socket created to test something already in existence then a command line solution might be a better way to go.

IMHO what the OP intended to find out is for the OP to describe and clarify don't you think?

---

### Post by dwhitney67 on 2011-08-13
> **karlson said:**
> 
IMHO what the OP intended to find out is for the OP to describe and clarify don't you think?

My apologies; you are correct.

---

