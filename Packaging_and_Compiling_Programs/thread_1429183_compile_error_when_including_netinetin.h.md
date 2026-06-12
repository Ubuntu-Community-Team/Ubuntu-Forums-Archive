---
title: "compile error when including netinet/in.h"
date: 2010-03-13
forum: Packaging and Compiling Programs
---

### Post by bingasedu on 2010-03-13
I'm compiling a simple client and server that exchange a message and exit.  I've had no trouble building the code on either FreeBSD 7.2 or Mac OS X 10.5.8, but I'm getting an unexpected error when I try to build on Ubuntu.  I just updated to Ubuntu 9.10 but it didn't change anything.

Whenever I include netinet/in.h I get the following error:

/usr/include/netinet/in.h:86: error: expected identifier before numeric constant

Thanks for any help.

Here's the server code, which gives this error:

file server.c:
```

#include "common.h"

int main(void)
{
    int rv;                          /* return value               */
    int l_sock;                      /* listening socket           */
    int r_sock;                      /* reading socket             */
    struct sockaddr_in addr;         /* server address             */
    socklen_t addr_len;              /* server address length      */
    int buff_len=1024;               /* beffer length              */
    char buffer[buff_len];           /* buffer for incoming data   */
    int optval;                      /* socket option value        */
    int optlen = sizeof(optval);     /* socket option value length */
    int flags = 0;                   /* flags for sctp_recvmsg     */

    /* call routine to create socket and local address */
    rv = setup_socket(&l_sock, &addr);
    if (rv < 0) {
        printf("setup_socket failed\n");
        exit(1);
    }

    /* bind socket to address */
    rv = bind(l_sock, (struct sockaddr*) &addr, sizeof(addr));
    check_result_exit("bind", rv);


    /* allow reuse of addresses in TIME_WAIT state */
    optval = 1;
    rv = setsockopt(l_sock, SOL_SOCKET, SO_REUSEADDR, &optval, optlen);
    check_result_exit("setsockopt", rv);

    /* begin listening on socket */
    rv = listen(l_sock, 5);
    check_result_exit("listen", rv);

    /* accept incomming connections */
    r_sock = accept(l_sock, (struct sockaddr *) &addr, &addr_len);
    check_result_exit("accept", r_sock);

    /* read incomming message */
    memset(buffer, 0, buff_len);
    rv = sctp_recvmsg(r_sock, buffer, buff_len, NULL, NULL, NULL, &flags);
    check_result_exit("sctp_recvmsg", rv);

    /* output received message */
    buffer[rv] = '\0';
    printf("sctp_recvmsg received: %s\n", buffer);

    /* close reading and listening sockets */
    rv = close(r_sock);
    rv = close(l_sock);

    return 0;
}

```

file common.h:
```

#ifndef COMMON_H
#define COMMON_H

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <netinet/sctp.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <errno.h>

#define check_result(a, b) \
        printf(a" returned %d with errno = %d (%s)\n", (b), errno, strerror(errno))

#define check_result_exit(a, b) \
        if (b < 0) { \
            printf(a" returned %d with errno = %d (%s)\n", (b), errno, strerror(errno)); \
            exit(1); \
        }

#define SERV_PORT 8021

int setup_socket(int *sock, struct sockaddr_in *addr);

#endif  /* COMMON_H */

```

file common.c:
```

#include "common.h"

int setup_socket(int *sock, struct sockaddr_in *addr)
{
    int rv;

    /* create socket */
    *sock = socket(AF_INET, SOCK_STREAM, IPPROTO_SCTP);
    if (sock < 0) {
        check_result("socket", *sock);
        return -1;
    }

    /* set up server's address */
    memset(addr, 0, sizeof(*addr));
    addr->sin_family = AF_INET;
    addr->sin_port = htons(SERV_PORT);
    rv = inet_aton("127.0.0.1", &(addr->sin_addr));
    if (rv != 1) {
        check_result("inet_aton", rv);
        return -1;
    }

    return 0;
}

```

---

### Post by SevenMachines on 2010-03-13
netinet/in.h tries to define  IPPROTO_SCTP, which is already defined by netinet/sctp.h in your code. if you switch the order of these 2 includes that should work (since netinet/sctp.h checks to see if its already defined)

---

### Post by bingasedu on 2010-03-13
Wow - very simple solution.  It looks like FreeBSD and Mac OS X handle the in.h defines in a way that isn't bothered by the definition of IPPROTO_SCTP in sctp.h.  Thanks very much!

---

