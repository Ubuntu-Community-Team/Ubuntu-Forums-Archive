---
title: "cmsg_nxthdr.c: No such file or directory"
date: 2012-11-29
forum: Programming Talk
---

### Post by giagnv on 2012-11-29
Hello,

I'm doing some socket programming, I need to access some ancillary data and I use recvmsg().

I iterate through the ancillary data via the CMSG_FIRSTHDR and CMSG_NXTHDR macros as follows:

```
for (pCmsg = CMSG_FIRSTHDR (&msg); pCmsg != NULL; pCmsg = CMSG_NXTHDR (&msg, pCmsg)) {
   ...
}

```

When CMSG_NXTHDR is called my program segfaults because apparently cmsg_nxthdr.c is not found (I get ../sysdeps/unix/sysv/linux/cmsg_nxthdr.c: No such file or directory).

I am on Ubuntu 12.04, I compile with g++ 4.6.3.

Does anybody have a clue on how to fix this?
Thanks,
G

---

### Post by Bachstelze on 2012-11-29
Post the full error message (and your code, obviously).

---

### Post by giagnv on 2012-11-29
OK, here is the code:

```

#include <errno.h>
#include <stdio.h>
#include <memory.h>
#include <arpa/inet.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/time.h>
#include <sys/ioctl.h>
#include <sys/select.h>
#include <sys/socket.h>
#include <sys/param.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <signal.h>
#include <unistd.h>

#if defined IP_PKTINFO
    # define DSTADDR_SOCKOPT IP_PKTINFO
    # define DSTADDR_DATASIZE (CMSG_SPACE(sizeof(struct in_pktinfo)))

    # define dstaddr(x) (&(((struct in_pktinfo *)(CMSG_DATA(x)))->ipi_addr))
    # define incomingIface(x) (((struct in_pktinfo *)(CMSG_DATA(x)))->ipi_ifindex)
#else
    # error "can't determine socket option"
#endif

int sockfd = 0;

ssize_t ifaceInfoReceiveFrom (int s, void *buf, size_t len, int flags, struct sockaddr *from, socklen_t *fromlen)
{
    struct iovec iov;
    iov.iov_base = buf;
    iov.iov_len = len;

    struct cmsghdr *pCmsg;
    struct msghdr msg;
    msg.msg_name = (caddr_t)from;
    msg.msg_namelen = (uint)*fromlen;
    msg.msg_iov = &iov;
    msg.msg_iovlen = 1;
    msg.msg_control = &pCmsg;
    msg.msg_controllen = sizeof (cmsghdr);
    msg.msg_flags = 0;

    size_t rc = recvmsg (s, &msg, flags);
    if (rc < 0) {
        return -1;
    }

    *fromlen = msg.msg_namelen;

    /* and arrange for IP_RECVDSTADDR to be available */
    if (msg.msg_controllen > 0) {
        for (pCmsg = CMSG_FIRSTHDR (&msg); pCmsg != NULL; pCmsg = CMSG_NXTHDR (&msg, pCmsg)) {
            printf ("Found level %u\n", pCmsg->cmsg_level);
            if (pCmsg->cmsg_level == IPPROTO_IP && pCmsg->cmsg_type == DSTADDR_SOCKOPT) {
                struct in_addr *to = (struct in_addr *) dstaddr (pCmsg);
                unsigned long ulIface = incomingIface (pCmsg);
                printf ("The incoming interface is %u\n", ulIface);
                break;
            }
        }
    }

    return rc;
}

int receive (void *pBuf, int iBufSize)
{
    if ((pBuf == NULL) || (iBufSize <= 0)) {
        return -1;
    }
    int rc;
    sockaddr_in sa;
    socklen_t saSourceLen = sizeof (sa);
        
    if ((rc = ifaceInfoReceiveFrom (sockfd, (char*)pBuf, iBufSize, 0, (struct sockaddr*) &sa, &saSourceLen)) < 0) {
        if (errno == EINTR) {
            // Some signal interrupted this call - just return 0 for timeout
            return 0;
        }
        else {
            return -3;
        }
    }

    return rc;
}

int main()
{
    //======================================
    // Socket Creation and Initialization
    //======================================
    sockfd = (int) socket (PF_INET, SOCK_DGRAM, IPPROTO_UDP);
    if (sockfd < 0) {
        return -1;
    }

    int opt_val = 1;
    if (setsockopt (sockfd, IPPROTO_IP, DSTADDR_SOCKOPT, (char*)&opt_val, sizeof (opt_val)) == -1) {
        return -2;
    }

    struct sockaddr_in local;
    memset (&local, 0, sizeof (local));
    local.sin_family = AF_INET;
    local.sin_port = htons (9999);
    local.sin_addr.s_addr = 0;  // Listen on wildcard address
    memset ((void*) local.sin_zero, 0, sizeof (local.sin_zero));

    //enables local address reuse
    if (setsockopt (sockfd, SOL_SOCKET, SO_REUSEADDR, (char*)&opt_val, sizeof (opt_val)) < 0) {
        return -2;
    }

    #if defined (OSX)

        //enables duplicate address and port bindings
        if (setsockopt (sockfd, SOL_SOCKET, SO_REUSEPORT, (char*)&opt_val, sizeof (opt_val)) < 0) {
            return -3;
        }

    #endif

    //enables permission to transmit broadcast messages
    if (setsockopt (sockfd, SOL_SOCKET, SO_BROADCAST, (char*) &opt_val, sizeof (opt_val)) < 0) {
        return -5;
    }

    //bind the socket to a specified address (INADDR_ANY if not specified) and port
    if (bind (sockfd, (struct sockaddr *) &local, sizeof (local)) < 0) {
         return -6;
    }

    //======================================
    // Receive
    //======================================
    for (char buf[1024]; true;) {
        if (receive (buf, 1024) == 0)
            printf ("Received packet\n");
        else
            printf ("Error Receiving packet");
    }
}

```

And here is the gdb back trace:

```

35	../sysdeps/unix/sysv/linux/cmsg_nxthdr.c: No such file or directory.
(gdb) bt
#0  __cmsg_nxthdr (mhdr=0xbfffecfc, cmsg=0x7fffda40) at ../sysdeps/unix/sysv/linux/cmsg_nxthdr.c:35
#1  0x080486b4 in ifaceInfoReceiveFrom (s=7, buf=0xbfffedcc, len=1024, flags=0, from=0xbfffed7c, fromlen=0xbfffed74) at ../udpsocket.cpp:55
#2  0x0804872a in receive (pBuf=0xbfffedcc, iBufSize=1024) at ../udpsocket.cpp:78
#3  0x0804891c in main () at ../udpsocket.cpp:141

```

Thanks!

---

