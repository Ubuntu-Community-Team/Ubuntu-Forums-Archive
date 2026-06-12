---
title: "problem with Comer's UDP connection implementation in my copy word"
date: 2008-05-20
forum: Programming Talk
---

### Post by iceman_sean on 2008-05-20
hi, all!
i just copied the C binding implementation of UDP conncetion of Comer's prestige three-volume series to my own ubuntu 8.04, but unfortunately, it got wrong with the following: /usr/bin/ld: errno: TLS definition in /lib/libc.so.6 section .tbss mismatches non-TLS reference in /tmp/ccYD5ZG8.o
/lib/libc.so.6: could not read symbols: Bad value
collect2: ld returned 1 exit status
any advice would be appreciated.

code:
/* UDPecho.c - main, UDPecho */
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#define LINELEN 128

extern int errno;

int UDPecho(const char *host, const char *service);
int errexit(const char *format, ...);
int connectUDP(const char *host, const char *service);

/* main - UDP client for echo servie */
int main(int argc, char *argv[]) {

    char *host = "localhost";
    char *service = "echo";

    switch(argc) {

        case 1:

            host = "localhost";
            break;

        case 2:

            host = argv[1];
            break;

        case 3:

            service = argv[2];      /* fall through */

        default:

            fprintf(stderr, "usage: UDPecho[host [port]]\n");
            exit(1);

    }

    UDPecho(host, service);
    return 0;

}

/* UDPecho */
int UDPecho(const char *host, const char *service) {

    char buf[LINELEN + 1];
    int s, nchars;

    s = connectUDP(host, service);

    while(fgets(buf, sizeof(buf), stdin)) {

        buf[LINELEN] = '\0';
        nchars = strlen(buf);
        (void)write(s, buf, nchars);
        
        if(read(s, buf, nchars) < 0)
            errexit("socket read failed: %s\n", strerror(errno));

        fputs(buf, stdout);

    }

}


/* connectsock.c - connectsock */

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <string.h>
#include <stdlib.h>

#ifndef INADDR_NONE
#define INADDR_NONE    0xffffffff
#endif /* INADDR_NONE */

extern int errno;

int errexit(const char *format, ...);

int connectsock(const char *host, const char *service, const char *transport) {

    struct hostent *phe;
    struct servent *pse;
    struct protoent *ppe;
    struct sockaddr_in sin;
    int s, type;

    memset(&sin, 0, sizeof(sin));
    sin.sin_family = AF_INET;

    /* map servie name to port number */
    if(pse = getservbyname(service, transport))
        sin.sin_port = pse -> s_port;

    else if((sin.sin_port = htons((unsigned short)atoi(service))) == 0)
        errexit("can't get \"%s\" service entry\n", service);

    /* map host name to IP address, allowing for dotted decimal */
    if(phe == gethostbyname(host))
        mencpy(&sin.sin_addr, phe -> h_addr, phe -> h_length);

    else if((sin.sin_addr.s_addr = inet_addr(host)) == INADDR_NONE)
        errexit("can't get \"%s\" host entry\n", host);

    /* map transport protocol name to protocol number */
    if(ppe = getprotobyname(transport) == 0)
        errexit("can't get \"%s\" protocol entry\n",transport);

    /* use protocol to choose a socket */
    if(strcmp(transport, "udp") == 0)
        type = SOCK_DGRAM;

    else
        type = SOCK_STREAM;

    /* allocate a socket */
    s = socket(PF_INET, type, ppe -> p_proto);
    if(s < 0)
        errexit("can't create socket: %s\n", strerror(errno));

    /* connect the socket */
    if(connect(s, (struct sockaddr *)&sin, sizeof(sin)) < 0)
        errexit("can't connect to %s.%s: %s\n", host, service, strerror(errno));

    return s;    

}


/* conncetUDP.c - connectUDP */

int connectsock(const char *host, const char *service, const char *transport);

int connectUDP(const char *host, const char *service) {

    return connectsock(host, service, "udp");

}


/* errexit.c - errexit */

#include <stdarg.h>
#include <stdio.h>
#include <stdlib.h>

int errexit(const char *format, ...) {

    va_list args;
    
    va_start(args, format);
    vfprintf(stderr, format, args);
    va_end(args);
    
    exit(1);

}

---

