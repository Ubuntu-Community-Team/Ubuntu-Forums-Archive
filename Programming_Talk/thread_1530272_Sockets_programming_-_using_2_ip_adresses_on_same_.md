---
title: "Sockets programming - using 2 ip adresses on same computer"
date: 2010-07-13
forum: Programming Talk
---

### Post by CelticFiddle on 2010-07-13
Hello all,

I am testing a socket program and need to test it using two different IP adresses.
I am used to use client and server both as loopback, but I can assign to one of them the adress of my ethernet interface? (Doesn't really make sense to me now.. but Im asking anyway :D )

---

### Post by dwhitney67 on 2010-07-13
Typically (always?) it is the server that binds a port to an interface.

You can test binding to two different IP addresses quite easily; the first IP to use is 127.0.0.1, the other can be the one assigned to your system by your router or ISP (eg. 192.168.1.100).


P.S.  If the server binds a port to 127.0.0.1, then this port will be unreachable by a remote computer.

---

### Post by soltanis on 2010-07-13
Yes, this is done according to the sockaddr structure that you pass to **bind**(2). If you want to bind to a particular interface then the easiest way is to pass it in dotted/colon form to **gettaddrinfo**(3) and then use the stuff it passes back to you.

Here's an excerpt from a function I use that does this (it uses UDP sockets, but you can adapt the code easily):

```

int
nst_listen(const char *iface, int port) {
    int fd = -1, rv;
    char service[smallstr];
    struct addrinfo hints, *info, *p;

    memset(&hints, 0, sizeof(struct addrinfo));
    hints.ai_family = AF_UNSPEC;
    hints.ai_socktype = SOCK_DGRAM;
    if (!iface) {
        hints.ai_flags = AI_PASSIVE;
    }

    snprintf(service, smallstr, "%d", port);
    if ((rv = getaddrinfo(iface, service, &hints, &info))) {
        warn("could not obtain addrinfo structure for port %d: %s\n", port, gai_strerror(rv));
        return -1;
    }

    for (p = info; p != NULL; p = p->ai_next) {
        if ((fd = socket(p->ai_family, p->ai_socktype, p->ai_protocol)) < 0) {
            syserror("socket failed");
            fd = -1;
            continue;
        }
        debug("fd %d was created successfully\n", fd);
        if (bind(fd, p->ai_addr, p->ai_addrlen) < 0) {
            syserror("fd %d could not be bound: ", fd);
            close(fd);
            fd = -1;
            continue;
        }
        debug("fd %d was bound successfully\n", fd);
        return fd;
    }
    warn("could not bind to any interfaces on port %d\n", port);
    return -1;
}

```

---

### Post by ju2wheels on 2010-07-14
Just to add to dwhitney67's comment, you can use the approach described and get around the problem with binding to 127.0.0.1 by modifying your network configuration settings and setting it to "manual" mode and as long as your router allows DHCP along a certain IP range you can force one interface to bind to two IP's from your router within the acceptable range.

This should then allow you run your client/server off one interface and force the communication out and back in to the same interface.

---

### Post by CelticFiddle on 2010-07-15
Thanks for the answers, guys :D

I will try that asap.

---

