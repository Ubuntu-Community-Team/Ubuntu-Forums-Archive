---
title: "so_original_dst problem for orginal destination ip"
date: 2007-12-07
forum: Programming Talk
---

### Post by zxiion86 on 2007-12-07
hello im making a transparent proxy like program..i have my linksys wrt54gs running dd-wrt as the iptables server with the following ip tables command on it 

iptables -t nat -A PREROUTING -i br0 -s ! 10.10.10.106 -p tcp --dport 80 -j DNAT --to 10.10.10.106:2000

and i have an ubuntu box connected via hardwire so my configuration looks like this
                                  
                                    internet via wireless cause im using it as a repeater
                                   |
                                    |
          wireless             |              hardwire
laptop ----------> router dd-wrt ----------> ubuntu proxy

the iptables rule is working and redirecting the traffic to my proxy program and i get the connection except that getsockopt(so_original_dst) is returning the incorrect ip address its returning the ip aaddress of the laptop instead of the ip address that im originally trying to connect to
so when i connect to [www.google.com](www.google.com) 80 i should get the ip adress of google.com returned but i dont 

here is the source code

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#include <unistd.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/ioctl.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <errno.h>
#include <dlfcn.h>
#include <linux/netfilter_ipv4.h>

#define SD_BOTH             2
#define SOCKET              int
#define INVALID_SOCKET      (SOCKET)(~0)
#define SOCKET_ERROR        (-1)

int main(void)
{
    SOCKET listen_sock, new_sock;
    struct sockaddr_in client;
    struct sockaddr_in me;
    struct sockaddr_in peer;

    unsigned long sockmode = 0;
    socklen_t SLen = sizeof(client);

    if ((listen_sock = socket(AF_INET, SOCK_STREAM, 0))== 
INVALID_SOCKET) {
        exit(1);
    }

    /* Local address and port */
    me.sin_family = AF_INET;
    me.sin_port = htons(10101);
    inet_aton("10.0.0.1", &me.sin_addr);

    if (ioctl(listen_sock, FIONBIO, &sockmode) == SOCKET_ERROR) {
        close(listen_sock);
        exit(1);
    }

    if (bind(listen_sock, (struct sockaddr *)&me, sizeof(me)) == 
SOCKET_ERROR) {
        close(listen_sock);
        exit(1);
    }

    if (listen(listen_sock, SOMAXCONN) == SOCKET_ERROR) {
        shutdown(listen_sock, SD_BOTH);
        close(listen_sock);
        exit(1);
    }

    while ((new_sock = accept(listen_sock, (struct sockaddr *)&client, 
&SLen))
            != INVALID_SOCKET)
    {
        SLen = sizeof(peer);
        memset(&peer, 0, SLen);
        getsockopt(new_sock, SOL_IP, SO_ORIGINAL_DST, &peer, &SLen);
        printf( "Client: %s:%hu\n", inet_ntoa(peer.sin_addr), ntohs(peer.sin_port));

        if ( shutdown(new_sock, SD_BOTH) == SOCKET_ERROR ||
             close(new_sock) == SOCKET_ERROR )
        {
            shutdown(listen_sock, SD_BOTH);
            close(listen_sock);
            exit(1);
        }
    }
    if(new_sock == INVALID_SOCKET) {
        shutdown(listen_sock, SD_BOTH);
        close(listen_sock);
        exit(1);
    }

    if (shutdown(listen_sock, SD_BOTH) == SOCKET_ERROR ||
        close(listen_sock) == SOCKET_ERROR)
    {
        exit(1);
    }

    exit(0);
}


any help would be appreciated i have been working on this for days and its driving me nuts... is there a coding problem an iptables problem or a kernel problem?

---

