---
title: "Problems compiling a .c file with GCC (worked great in FC6)"
date: 2007-02-27
forum: Programming Talk
---

### Post by somafm on 2007-02-27
Hello,
I WAS using FC6, installed GCC, and compiled a .c file. It worked fine and I was able to run my application in console. The command I used in terminal was:  **gcc -o final gsmsdisc.c**.

After installing ubuntu 6.10 and updating everything, I tried to compile the same .C file the same way, and I get a TON of errors. Could it have to do with the GCC versions, or should I be compiling it a different way? I'm a big noob when it comes to C programming, and this isn't my code. I just want to get it compiled so I can use it in Ubuntu. It's a single .C file, and I usually run it in console like so:    **./final argumentshere**

The gcc version I have running on FC6 is: 4.1.1-51.fc6.i386.
The gcc version on Ubuntu 6.10 is the default that came with it, and it's updated to the fullest.

I have FC6 on my laptop and Ubuntu6.10 on my desktop, so I can still access both if you guys need me to. Thanks for the help in advance  :) 

Here is the full .C code:
```
/*

by Luigi Auriemma

*/

#include <stdio.h>
#include <stdlib.h>
#include <stdint.h>

#ifdef WIN32
    #include <winsock2.h>
    #include <ws2tcpip.h>
    #include "winerr.h"

    #define close   closesocket
    #define sleep   Sleep
    #define ONESEC  1000
#else
    #include <unistd.h>
    #include <sys/socket.h>
    #include <sys/types.h>
    #include <sys/param.h>
    #include <arpa/inet.h>
    #include <netinet/in.h>
    #include <netdb.h>

    #define ONESEC  1
#endif



#define VER         "0.1.2"
#define MSHOST      "master.gamespy.com"
#define MSPORT      27900
#define BUFFSZ      2048
#define DISC        "\\heartbeat\\%hu" \
                    "\\gamename\\%s" \
                    "\\statechanged\\2"
#define IPSZ        sizeof(struct iphdr)
#define UDPSZ       sizeof(struct udphdr)
#define PSEUDOSZ    sizeof(struct pseudohdr)
#define PCKSIZE     (IPSZ + UDPSZ + pcklen)
#define PSSIZE      (PSEUDOSZ + UDPSZ + pcklen)



struct iphdr {
    uint8_t     ihl_ver;
    uint8_t     tos;
    uint16_t    tot_len;
    uint16_t    id;
    uint16_t    frag_off;
    uint8_t     ttl;
    uint8_t     protocol;
    uint16_t    check;
    uint32_t    saddr;
    uint32_t    daddr;
};

struct udphdr {
    uint16_t    source;
    uint16_t    dest;
    uint16_t    len;
    uint16_t    check;
};

struct pseudohdr {
    uint32_t    saddr;
    uint32_t    daddr;
    uint8_t     zero;
    uint8_t     protocol;
    uint16_t    len;
};



uint16_t in_cksum(void *data, int len);
uint32_t resolv(char *host);
void std_err(void);



int main(int argc, char *argv[]) {
    struct  sockaddr_in peer;
    struct  iphdr       *ip;
    struct  udphdr      *udp;
    struct  pseudohdr   *pseudo;
    uint32_t    ip_src,
                ip_dst;
    int         sd,
                i,
                pcklen,
                on = 1,
                timeout = 0;
    uint16_t    port_src,
                port_dst;
    uint8_t     buff[BUFFSZ],
                *data;

#ifdef WIN32
    WSADATA    wsadata;
    WSAStartup(MAKEWORD(1,0), &wsadata);
#endif

    setbuf(stdout, NULL);

    fputs("\n"
        "GS master server disconnector "VER"\n"
        "by Luigi Auriemma\n"
        "e-mail: aluigi@autistici.org\n"
        "web:    aluigi.org\n"
        "\n", stdout);

    if(argc < 4) {
        printf("\n"
            "Usage: %s <gamename> <server> <port> [timeout]\n"
            "\n"
            " timeout is the amount of time in seconds before resending the packet\n"
            " by default is sent only one packet and then exits\n"
            " for more informations: http://aluigi.org/papers/msdisc.txt\n"
            "\n", argv[0]);
        exit(1);
    }

#ifndef WIN32
    if(getuid()) {
        printf("\nError: you must be root to use raw sockets, I try to continue\n\n");
    }
#endif


    if(argc > 4) timeout = atoi(argv[4]);

    ip     = (struct iphdr *)buff;
    udp    = (struct udphdr *)(buff + IPSZ);
    data   = (uint8_t *)(buff + IPSZ + UDPSZ);
    pseudo = (struct pseudohdr *)(buff + IPSZ - PSEUDOSZ);

    printf("- resolv hostnames/IPs:\n");
    ip_src           = resolv(argv[2]);
    ip_dst           = resolv(MSHOST);
    port_src         = htons(atoi(argv[3]));
    port_dst         = htons(MSPORT);

    pcklen = sprintf(
        data,
        DISC,
        ntohs(port_src),
        argv[1]);

    pseudo->saddr    = ip_src;
    pseudo->daddr    = ip_dst;
    pseudo->zero     = 0;
    pseudo->protocol = IPPROTO_UDP;
    pseudo->len      = htons(UDPSZ + pcklen);

    udp->source      = port_src;
    udp->dest        = port_dst;
    udp->check       = 0;
    udp->len         = pseudo->len;
    udp->check       = htons(in_cksum(pseudo, PSSIZE));

    ip->ihl_ver      = (4 << 4) | (sizeof(struct iphdr) >> 2);
    ip->tos          = 0x10;
    ip->tot_len      = htons(PCKSIZE);
    ip->id           = htons(1);
    ip->frag_off     = htons(0);
    ip->ttl          = 128;
    ip->protocol     = IPPROTO_UDP;
    ip->check        = 0;
    ip->saddr        = ip_src;
    ip->daddr        = ip_dst;
    ip->check        = htons(in_cksum(ip, IPSZ));

    peer.sin_addr.s_addr = ip_dst;
    peer.sin_port        = port_dst;
    peer.sin_family      = AF_INET;

    printf("- from %15s : %hu\n",
        inet_ntoa(*(struct in_addr *)&(ip->saddr)), ntohs(udp->source));
    printf("- to   %15s : %hu\n",
        inet_ntoa(peer.sin_addr), ntohs(udp->dest));

    sd = socket(AF_INET, SOCK_RAW, IPPROTO_RAW);
    if(sd < 0) std_err();
    if(setsockopt(sd, IPPROTO_IP, IP_HDRINCL, (void *)&on, sizeof(on))
      < 0) std_err();

    for(;;) {
        if(sendto(sd, buff, PCKSIZE, 0, (struct sockaddr *)&peer, sizeof(peer))
          < 0) std_err();
        fputc('.', stdout);

        if(!timeout) break;
        for(i = timeout; i; i--) {
            printf("%5d\b\b\b\b\b", i);
            sleep(ONESEC);
        }
    }
    close(sd);

    printf("\nDone\n");
    return(0);
}



uint16_t in_cksum(void *data, int len) {
    uint32_t    sum    = 0;
    int         i      = len >> 1,
                endian = 1; // big endian
    uint16_t    crc,
                *p     = (uint16_t *)data;

    if(*(char *)&endian) endian = 0;
    while(i--) sum += *p++;
    if(len & 1) sum += *p & (endian ? 0xff00 : 0xff);
    crc = sum = (sum >> 16) + (sum & 0xffff);
    if(sum >>= 16) crc += sum;
    if(!endian) crc = (crc >> 8) | (crc << 8);
    return(~crc);
}



uint32_t resolv(char *host) {
    struct      hostent *hp;
    uint32_t    host_ip;

    host_ip = inet_addr(host);
    if(host_ip == INADDR_NONE) {
        hp = gethostbyname(host);
        if(!hp) {
            printf("\nError: Unable to resolv hostname (%s)\n", host);
            exit(1);
        } else host_ip = *(uint32_t *)hp->h_addr;
    }
    return(host_ip);
}



#ifndef WIN32
    void std_err(void) {
        perror("\nError");
        exit(1);
    }
#endif


```

Here are the errors:
```
psc@backuplinux:~/Desktop$ gcc -o final gsmsdisc.c
gsmsdisc.c:7:19: error: stdio.h: No such file or directory
gsmsdisc.c:8:20: error: stdlib.h: No such file or directory
gsmsdisc.c:9:20: error: stdint.h: No such file or directory
gsmsdisc.c:20:24: error: unistd.h: No such file or directory
gsmsdisc.c:21:28: error: sys/socket.h: No such file or directory
gsmsdisc.c:22:27: error: sys/types.h: No such file or directory
gsmsdisc.c:23:27: error: sys/param.h: No such file or directory
gsmsdisc.c:24:27: error: arpa/inet.h: No such file or directory
gsmsdisc.c:25:28: error: netinet/in.h: No such file or directory
gsmsdisc.c:26:23: error: netdb.h: No such file or directory
gsmsdisc.c:49: error: expected specifier-qualifier-list before &#8216;uint8_t&#8217;
gsmsdisc.c:62: error: expected specifier-qualifier-list before &#8216;uint16_t&#8217;
gsmsdisc.c:69: error: expected specifier-qualifier-list before &#8216;uint32_t&#8217;
gsmsdisc.c:78: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;in_cksum&#8217;
gsmsdisc.c:79: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;resolv&#8217;
gsmsdisc.c: In function &#8216;main&#8217;:
gsmsdisc.c:85: error: storage size of &#8216;peer&#8217; isn&#8217;t known
gsmsdisc.c:89: error: &#8216;uint32_t&#8217; undeclared (first use in this function)
gsmsdisc.c:89: error: (Each undeclared identifier is reported only once
gsmsdisc.c:89: error: for each function it appears in.)
gsmsdisc.c:89: error: expected &#8216;;&#8217; before &#8216;ip_src&#8217;
gsmsdisc.c:96: error: &#8216;uint16_t&#8217; undeclared (first use in this function)
gsmsdisc.c:96: error: expected &#8216;;&#8217; before &#8216;port_src&#8217;
gsmsdisc.c:98: error: &#8216;uint8_t&#8217; undeclared (first use in this function)
gsmsdisc.c:98: error: expected &#8216;;&#8217; before &#8216;buff&#8217;
gsmsdisc.c:106: error: &#8216;stdout&#8217; undeclared (first use in this function)
gsmsdisc.c:106: error: &#8216;NULL&#8217; undeclared (first use in this function)
gsmsdisc.c:116: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
gsmsdisc.c:123: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
gsmsdisc.c:128: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
gsmsdisc.c:135: error: &#8216;buff&#8217; undeclared (first use in this function)
gsmsdisc.c:137: error: &#8216;data&#8217; undeclared (first use in this function)
gsmsdisc.c:137: error: expected expression before &#8216;)&#8217; token
gsmsdisc.c:140: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
gsmsdisc.c:141: error: &#8216;ip_src&#8217; undeclared (first use in this function)
gsmsdisc.c:142: error: &#8216;ip_dst&#8217; undeclared (first use in this function)
gsmsdisc.c:143: error: &#8216;port_src&#8217; undeclared (first use in this function)
gsmsdisc.c:144: error: &#8216;port_dst&#8217; undeclared (first use in this function)
gsmsdisc.c:146: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
gsmsdisc.c:152: error: &#8216;struct pseudohdr&#8217; has no member named &#8216;saddr&#8217;
gsmsdisc.c:153: error: &#8216;struct pseudohdr&#8217; has no member named &#8216;daddr&#8217;
gsmsdisc.c:154: error: &#8216;struct pseudohdr&#8217; has no member named &#8216;zero&#8217;
gsmsdisc.c:155: error: &#8216;struct pseudohdr&#8217; has no member named &#8216;protocol&#8217;
gsmsdisc.c:155: error: &#8216;IPPROTO_UDP&#8217; undeclared (first use in this function)
gsmsdisc.c:156: error: &#8216;struct pseudohdr&#8217; has no member named &#8216;len&#8217;
gsmsdisc.c:158: error: &#8216;struct udphdr&#8217; has no member named &#8216;source&#8217;
gsmsdisc.c:159: error: &#8216;struct udphdr&#8217; has no member named &#8216;dest&#8217;
gsmsdisc.c:160: error: &#8216;struct udphdr&#8217; has no member named &#8216;check&#8217;
gsmsdisc.c:161: error: &#8216;struct udphdr&#8217; has no member named &#8216;len&#8217;
gsmsdisc.c:161: error: &#8216;struct pseudohdr&#8217; has no member named &#8216;len&#8217;
gsmsdisc.c:162: error: &#8216;struct udphdr&#8217; has no member named &#8216;check&#8217;
gsmsdisc.c:164: error: &#8216;struct iphdr&#8217; has no member named &#8216;ihl_ver&#8217;
gsmsdisc.c:165: error: &#8216;struct iphdr&#8217; has no member named &#8216;tos&#8217;
gsmsdisc.c:166: error: &#8216;struct iphdr&#8217; has no member named &#8216;tot_len&#8217;
gsmsdisc.c:167: error: &#8216;struct iphdr&#8217; has no member named &#8216;id&#8217;
gsmsdisc.c:168: error: &#8216;struct iphdr&#8217; has no member named &#8216;frag_off&#8217;
gsmsdisc.c:169: error: &#8216;struct iphdr&#8217; has no member named &#8216;ttl&#8217;
gsmsdisc.c:170: error: &#8216;struct iphdr&#8217; has no member named &#8216;protocol&#8217;
gsmsdisc.c:171: error: &#8216;struct iphdr&#8217; has no member named &#8216;check&#8217;
gsmsdisc.c:172: error: &#8216;struct iphdr&#8217; has no member named &#8216;saddr&#8217;
gsmsdisc.c:173: error: &#8216;struct iphdr&#8217; has no member named &#8216;daddr&#8217;
gsmsdisc.c:174: error: &#8216;struct iphdr&#8217; has no member named &#8216;check&#8217;
gsmsdisc.c:178: error: &#8216;AF_INET&#8217; undeclared (first use in this function)
gsmsdisc.c:181: error: &#8216;struct iphdr&#8217; has no member named &#8216;saddr&#8217;
gsmsdisc.c:181: error: &#8216;struct udphdr&#8217; has no member named &#8216;source&#8217;
gsmsdisc.c:183: error: &#8216;struct udphdr&#8217; has no member named &#8216;dest&#8217;
gsmsdisc.c:185: error: &#8216;SOCK_RAW&#8217; undeclared (first use in this function)
gsmsdisc.c:185: error: &#8216;IPPROTO_RAW&#8217; undeclared (first use in this function)
gsmsdisc.c:187: error: &#8216;IPPROTO_IP&#8217; undeclared (first use in this function)
gsmsdisc.c:187: error: &#8216;IP_HDRINCL&#8217; undeclared (first use in this function)
gsmsdisc.c: At top level:
gsmsdisc.c:209: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;in_cksum&#8217;
gsmsdisc.c:227: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;resolv&#8217;
gsmsdisc.c: In function &#8216;std_err&#8217;:
gsmsdisc.c:247: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;

```

---

### Post by lnostdal on 2007-02-27
in short: ```
sudo aptitude install build-essential
```

for more details see: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/)

edit: minor correction; thanks WW :)

---

### Post by somafm on 2007-02-27
Wahoo thanks! Got it to work now.

I ended up using:
```
sudo aptitude install build-essential manpages manpages-dev manpages-posix-dev
```
.. the one you posted didn't want to install anything :confused: 

Working fine though, thanks again!

---

### Post by WW on 2007-02-27
Stage whisper: *Inostdal... no **s** at the end of **build-essential***

---

