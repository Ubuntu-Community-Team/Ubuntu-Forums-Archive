---
title: "Packet sniffer in C"
date: 2008-10-21
forum: Programming Talk
---

### Post by pokerbirch on 2008-10-21
Hi, i'm new to the forum but have been lurking around for several months. A brief background:
[LIST]
[*]My main O.S. *used* to be Windows XP but i am now a Linux convert and haven't booted my Windows partition for about 2 months
[*]I am a hobby programmer and previous to installing Ubuntu 8.04, i used VB6 for about 5 years
[*]I "dabbled" with C++ and Java under Windows but always returned to VB6 as i was very comfortable with it
[*]I have now decided to learn C as it is a more powerful language and i am more comfortable with procedural programming, although i'm also familiar with OOP
[*]I'm not particularly keen on frameworks but decided that it would better to learn Java rather than .Net, although i'm not a big fan of Java either
[*]Had VB.Net been similar to VB6, i *may* have moved to .Net instead, but then i would never have discovered Ubuntu. So we can thank M$ that i'm here. :wink:
[/LIST]

I have written several small programs in C on my Linux box in order to understand the language better, but am now working on a "proper" project. As part of this project, i need to monitor internet packets. I have read a couple of articles and played around with PCAP, however i feel that a RAW socket sniffer will suit my needs better as i have a specific target. My code so far is:
```
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include <unistd.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <linux/if_ether.h>
#include <net/if.h>
#include <linux/filter.h>
#include <sys/ioctl.h>
#include <string.h>

int main(int argc, char **argv) {
    int sock, i;
    unsigned char buffer[2048];
    unsigned char *iphead, *ethhead;
    struct ifreq ethreq;

    // NOTE: use TCPDUMP to build the filter array.
    // set filter to sniff only port 443
    // $ sudo tcpdump -dd port 443

    struct sock_filter BPF_code[] = {
        { 0x28, 0, 0, 0x0000000c },
        { 0x15, 0, 8, 0x000086dd },
        { 0x30, 0, 0, 0x00000014 },
        { 0x15, 2, 0, 0x00000084 },
        { 0x15, 1, 0, 0x00000006 },
        { 0x15, 0, 17, 0x00000011 },
        { 0x28, 0, 0, 0x00000036 },
        { 0x15, 14, 0, 0x000001bb },
        { 0x28, 0, 0, 0x00000038 },
        { 0x15, 12, 13, 0x000001bb },
        { 0x15, 0, 12, 0x00000800 },
        { 0x30, 0, 0, 0x00000017 },
        { 0x15, 2, 0, 0x00000084 },
        { 0x15, 1, 0, 0x00000006 },
        { 0x15, 0, 8, 0x00000011 },
        { 0x28, 0, 0, 0x00000014 },
        { 0x45, 6, 0, 0x00001fff },
        { 0xb1, 0, 0, 0x0000000e },
        { 0x48, 0, 0, 0x0000000e },
        { 0x15, 2, 0, 0x000001bb },
        { 0x48, 0, 0, 0x00000010 },
        { 0x15, 0, 1, 0x000001bb },
        { 0x6, 0, 0, 0x00000060 },
        { 0x6, 0, 0, 0x00000000 }
    };
    struct sock_fprog Filter;

    Filter.len = sizeof(BPF_code) / 8;
    Filter.filter = BPF_code;

    if ((sock = socket(PF_PACKET, SOCK_RAW, htons(ETH_P_IP))) == -1) {
        perror("socket");
        exit(1);
    }

    // set network card to promiscuos
    strncpy(ethreq.ifr_name, "eth0", IFNAMSIZ);
    if (ioctl(sock,SIOCGIFFLAGS, &ethreq) == -1) {
        perror("ioctl");
        close(sock);
        exit(1);
    }
    ethreq.ifr_flags |= IFF_PROMISC;
    if (ioctl(sock, SIOCSIFFLAGS, &ethreq) == -1) {
        perror("ioctl");
        close(sock);
        exit(1);
    }

    // attach filter to socket
    if(setsockopt(sock, SOL_SOCKET, SO_ATTACH_FILTER, &Filter, sizeof(Filter)) == -1) {
        perror("setsockopt");
        close(sock);
        exit(1);
    }

    while (1) {
        printf("----------------------\n");
        i = recvfrom(sock, buffer, sizeof(buffer), 0, NULL, NULL);
        printf("%d bytes read\n", i);

        // check header size: Ethernet = 14, IP = 20, TCP = 8 (sum = 42)
        if (i < 42) {
            perror("recvfrom():");
            printf("Incomplete packet (errno is %d)\n", errno);
            close(sock);
            exit(0);
        }
        ethhead = buffer;
        iphead = buffer + 14; // (skip ethernet  header)

        if (*iphead == 0x45) {
            printf("Source Address: %d.%d.%d.%d, Port: %d\n",
                iphead[12], iphead[13], iphead[14], iphead[15], (iphead[20] << 8) + iphead[21]);
            printf("Dest Address: %d.%d.%d.%d, Port: %d\n",
                iphead[16], iphead[17], iphead[18], iphead[19], (iphead[22] << 8) + iphead[23]);
        }
    }
    // clean up
    close(sock);
}

```

This seems to be working ok as simple sniffer, however a couple of questions:
1) The most important information is the actual packet data, however i can't figure out *where* this data is or how to display it
2) The code only appears to capture incoming packets, however i need to capture packet data in both directions

Any help would be much appreciated as Google doesn't seem to be helping much.

---

### Post by dwhitney67 on 2008-10-21
You should look at the source code for Ethereal, or just use it as your application.

---

### Post by pokerbirch on 2008-10-21
Hmmmmm, i previously looked at Ethereal source code but it has a LOT of files and is a bit overwhelming. As i say, this will be part of a larger project so my intentions are to put the sniffer code into a single source file. I like to write minimal code and the RAW socket approach seemed to be less bulky than using PCAP.

In your honest opinions, which approach would you use? Can i realistically write a minimal packet sniffer within a few hundred lines of code or am i a little disillusioned?

---

### Post by dwhitney67 on 2008-10-21
> **pokerbirch said:**
> ...
In your honest opinions, which approach would you use? Can i realistically write a minimal packet sniffer within a few hundred lines of code or am i a little disillusioned?
I have no idea; I've never written one.  I have used Ethereal in the past.  It is bulky because it provides a GUI and lots of nifty tools.

Your best bet may be to Google to find this "minimal" packet sniffer you seek.

---

### Post by Rich78 on 2008-10-21
I think what you require is to write a small proxy to sniff the traffic from.  A proxy allows you sniff traffic between two points, rather than at one end.  

Which is why all you can see is traffic incoming.

I believe this is how packet sniffing programs work.

---

### Post by pokerbirch on 2008-10-21
Hi Rich, thanks for the useful response. Can you give more detail on how the proxy should work? Correct me if i'm wrong, but wouldn't i have to force all programs to connect to LOCALHOST which would be the "server" end of my proxy??

---

### Post by Rich78 on 2008-10-21
Essentially all that should be necessary is to setup a proxy to run on a particular port (80 for example).  

This would mean all traffic that runs on port 80 (http traffic) will pass through the proxy and can be sniffed.

That's my understanding from a conceptual basis so shouldn't be taken as gospel.

I actually intend to do something similar for a different project.  I intend to sniff for traffic on particular ports and trigger events based on the traffic.  

So this project does actually interest me.

I also like the idea of sticking with ansi C or C++ for compatibility for other platforms to make my application more universal.

I did try compiling the code you posted but had an error followed by warnings based on the struct sock_filter, however this may be due to the initial error I received.  I've little experience with C as I'm more from a C#, but I intend on picking up C as I go along.

The error I got was to do with the <linux/filter.h> include, I don't remember the error sorry as it was on an old Red Hat box at work.

I haven't tried it yet on my other machines, but it would be nice to use something other than <linux/filter.h> as it's Linux specific and not Ansi C.

---

### Post by pokerbirch on 2008-10-21
I've actually gone full circle and am now looking at the PCAP library again. If you want multi platform code, then pcap is the way forward. I've read several articles but am not a copy and paste merchant - i much prefer to write own code while referencing to the tutorials. I find i learn much better that way.

You may find these useful:
[http://www.geocities.com/amit_saha_works/linux/html/sniff.html]("http://www.geocities.com/amit_saha_works/linux/html/sniff.html")
[http://yuba.stanford.edu/~casado/pcap/section1.html]("http://yuba.stanford.edu/~casado/pcap/section1.html")
[http://www.everything2.com/e2node/Writing%2520a%2520Packet%2520Sniffer]("http://www.everything2.com/e2node/Writing%2520a%2520Packet%2520Sniffer")


EDIT:
If it's of any use, i use the Code::Blocks IDE. I think it's rather nice... ;)

---

### Post by Rich78 on 2008-10-21
Thanks, a quick look at the first link suggests PCAP is certainly the simplest implementation.

---

### Post by pokerbirch on 2008-10-21
This is what i have so far. It compiles and works ok in Code::Blocks latest build (Oct 18th) and on Ubuntu Hardy 8.04. I'm a bit confused with printing the actual packet data. Anyone familiar with PCAP??

```
/*
NOTES:
1) a TCP packet consists of:
    a) ethernet header (always 14 bytes)
    b) ip header (variable)
    c) tcp header (variable)
    d) the packet data (payload)
*/

#include <pcap.h> // ADD REF: Project > Build Options > Linker Settings > Add > "/usr/lib/libpcap.a"
#include <netinet/ether.h>
#include <netinet/ip.h>
#include <netinet/tcp.h>

void PacketHandler(unsigned char *arg, const struct pcap_pkthdr *pkthdr, const unsigned char *packet) {
    int eth_hdr_size = 0;
    int ip_hdr_size = 0;
    int tcp_hdr_size = 0;
    int offset = 0;
    unsigned char *payload;

    // get header sizes
    eth_hdr_size = sizeof(struct ether_header);
    ip_hdr_size = sizeof(struct iphdr);
    tcp_hdr_size = sizeof(struct tcphdr);
    // calc payload memory offset
    offset = eth_hdr_size + ip_hdr_size + tcp_hdr_size;
    // get payload and print
    payload = (unsigned char *)(packet + offset);


// TODO
// print payload in ascii and/or hex format

}

int PacketSniff() {
    char *device;
    static char errbuf[PCAP_ERRBUF_SIZE];
    bpf_u_int32 mask = 0;
    bpf_u_int32 net = 0;
    char filter[] = "port 443";
    struct bpf_program fp;
    pcap_t *handle;
    int pkt_count = 3; // (infinite = -1)

    // get compatible device
    device = pcap_lookupdev(errbuf);
    if (device == NULL) return -1;
    // get netmask
    if (pcap_lookupnet(device, &net, &mask, errbuf) == -1) return -2;
    // open device
    handle = pcap_open_live(device, BUFSIZ, 1, 500, errbuf);
    if (handle == NULL) return -3;
    // set packet filters
    if (pcap_compile(handle, &fp, filter, 0, net) == -1) return -4;
    if (pcap_setfilter(handle, &fp) == -1) return -5;
    // start sniffing
    pcap_loop(handle, pkt_count, PacketHandler, NULL);
    // clean up
    pcap_freecode(&fp);
    pcap_close(handle);
    return 0;
}

```

---

### Post by rnodal on 2008-10-22
Sorry I can't help much here since I don't have that much experience. Programming a packet sniffer is a tricky thing to do. You have to listen to all the incoming traffic that passes through your machine and make a copy of the packages that are intended for your machine plus the ones intended for others. I was planning on doing something like what your are trying to do I have not had the time to get into raw sockets and refresh TCP/IP stuff. Keep us updated about your progress.

-r

---

### Post by pokerbirch on 2008-10-25
So is there anyone with PCAP experience?

---

