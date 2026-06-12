---
title: "C++ and libpcap failing with examples from magazine"
date: 2010-07-07
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-07-07
I have been trying to run the sniffer projects found in Hackin9 magazine, but Listing two (Simle sniffer) and listing three (arp sniffer) don't work
here's my typed up versions of each:

Listing 2:
```

/* simple sniffer */

#include <pcap.h>
#include <string.h>
#include <stdlib.h>

#define MAXBYTES2CAPTURE 2048

void processPacket(u_char *arg, const struct pcap_pkthdr* pkthdr, const u_char *packet){

int i=0, *counter = (int *)arg;

printf("Packet Count: %d\n", ++(*counter));
printf("Received Packet Size: %d\n", pkthdr->len);
printf("Payload:\n");
for (i=0; i<pkthdr->len; i++){

    if  ( isprint(packet[i]) )
        printf("%c ", packet[i]);
    else
        printf(". ");

    if( (i%16 == 0 && i!=0) || i==pkthdr->len-1 )
        printf("\n");
    }
return;
}
int main( ){

    int i=0, count=0;
    pcap_t *descr = NULL;
    char errbuf[PCAP_ERRBUF_SIZE], *device=NULL;
    memset(errbuf,0,PCAP_ERRBUF_SIZE);

    device = pcap_lookupdev(errbuf);

    printf("Opening device %s\n", device);

    descr = pcap_open_live(device, MAXBYTES2CAPTURE, 1, 512, errbuf);

    pcap_loop(descr, -1, processPacket, (u_char *)&count);

return 0;
}

```
listing 3:
```

/* Simple arp sniffer                    */
/* to compile: gcc arpsniffer.c -o arpsniff -lpcap    */
/* run as root!                        */

#include <pcap.h>
#include <stdlib.h>
#include <string.h>

/* ARP header, (assuming Ethernet+IPv4)            */
#define ARP_REQUEST 1 /* request */
#define ARP_REPLY 2 /* reply */
typedef struct arphdr {
    u_init16_t htype;
    u_init16_t ptype;
    u_char hlen;
    u_char plen;
    u_init16_t oper;
    u_char sha[6];
    u_char spa[4];
    u_char tha[6];
    u_char tpa[4];
}arphdr_t;

#define MAXBYTES2CAPTURE 2048

int main(int argc, char *argv[]) {

    int i=0;
    bpf_u_int32 netaddr=0, mask=0;

    struct bpf_program filter;

    char errbuf[PCAP_ERRBUF_SIZE];

    pcap_t *descr = NULL;

    struct pcap_pkthdr pkthdr;

    const unsigned char *packet=NULL;

    arphdr_t *arpheader = NULL;

    memset(errbuf,0,PCAP_ERRBUF_SIZE);

if (argc != 2) {
    printf("USAGE: arpsniffer <interface>\n");
    exit(1);
}

descr = pcap_open_live(argv[1], MAXBYTES2CAPTURE, 0,  512, errbuf);

pcap_lookupnet( argv[1] , &netaddr, &mask, errbuf);

pcap_compile(descr, &filter, "arp", 1, mask);

pcap_setfilter(descr,&filter);

while(1){

    packet = pcap_next(descr,&pkthdr);
    arpheader = (struct arphdr *)(packet+14);

    printf("\n\nRecieved Packet Size: %d bytes\n", pkthdr.len);

    printf("Hardware type: %s\n", (ntohs(arpheader->htype) == 1) ? "Ethernet" : "Unknown");

    printf("Protocol type: %s\n", (ntohs(arpheader->ptype) == 0x0800) ? "IPv4" : "Unknown");

    printf("Operation: %s\n", (ntohs(arpheader->oper) == ARP_REQUEST) ? "ARP_REQUEST" : "ARP_REPLY");

if (ntohs(arpheader->htype) == 1 && ntohs(arpheader->ptype) == 0x0800) {
    printf("Sender MAC: ");
    for(i=0; i<6;i++)printf("%02X:", arpheader->sha[i]);
    printf("\nSender IP: ");
    for(i=0; i<4;i++)printf("%d.", arpheader->spa[i]);
    printf("\nTarget MAC: ");
    for(i=0; i<6;i++)printf("%02X:", arpheader->tha[i]);
    printf("\nTarget IP: ");
    for(i=0; i<4;i++)printf("%d.", arpheader->tpa[1]);
    printf("\n");
    }
}
return 0;
}

```
listing 2 compiles perfectly with gcc <...> -lpcap
but then when I run it, it says 
> 
Opening device (null)
Segmentation fault

and exits.
listing 3 says the following when I try to compile it:
> 
arpsniffer.c:13: error: expected specifier-qualifier-list before ‘u_init16_t’
arpsniffer.c: In function ‘main’:
arpsniffer.c:65: error: ‘arphdr_t’ has no member named ‘htype’
arpsniffer.c:67: error: ‘arphdr_t’ has no member named ‘ptype’
arpsniffer.c:69: error: ‘arphdr_t’ has no member named ‘oper’
arpsniffer.c:71: error: ‘arphdr_t’ has no member named ‘htype’
arpsniffer.c:71: error: ‘arphdr_t’ has no member named ‘ptype’
arpsniffer.c:73: error: ‘arphdr_t’ has no member named ‘sha’
arpsniffer.c:75: error: ‘arphdr_t’ has no member named ‘spa’
arpsniffer.c:77: error: ‘arphdr_t’ has no member named ‘tha’
arpsniffer.c:79: error: ‘arphdr_t’ has no member named ‘tpa’

thanks in advance!

---

### Post by gmargo on 2010-07-07
Why aren't you checking the return value from **pcap_lookupdev**?  It gave you an error message telling you what is wrong, but you're ignoring it.

---

### Post by Crazedpsyc on 2010-07-07
I'm sorry, did I forget to mention I am a noob to programming in general? I see that it says null instead of wlan0 or eth0, but I have no idea why.

---

### Post by xb12x on 2010-07-07
For the errors in listing 3 you might be missing a header file. It looks as if 'u_init16_t' is not defined anywhere.  Or perhaps it's a typo.

---

### Post by gmargo on 2010-07-07
> **Crazedpsyc said:**
> I'm sorry, did I forget to mention I am a noob to programming in general? I see that it says null instead of wlan0 or eth0, but I have no idea why.

Your output says "(null)" because pcap_lookupdev returned a null pointer.  As described in the pcap_lookupdev man page ("man pcap_lookupdev" to read it), on error, the function places an error message in the errbuf array and returns a null pointer.  So you need to print the contents of the errbuf.  It probably says "you need to be root to run this".

---

### Post by johnl on 2010-07-07
Replace this line:

```

    device = pcap_lookupdev(errbuf);

```

with:

```

    if (!(device = pcap_lookupdev(errbuf))) {
        fprintf(stderr, "error: %s\n", errbuf);
        return 1;
    }

```


Output:

```

user@host:~$ ./testpcap
error: no suitable device found
user@host:~$ sudo !!
sudo ./test
Opening device eth0
[...expected output...]

```

There are a couple ways you can handle a permission situation like this gracefully.  If an operation requires root privileges you can do:

```

#include <unistd.h>

if (geteuid() != 0) {
    fprintf(stderr, "error: you must be root to run this\n");
    return -1;
}

```

Or, more specifically, you can use the linux capabilities:

```

#include <sys/capability.h>
#include <stdbool.h>
/* link with -lcap */

/* 
 * returns true if we successfully acquired the requested 
 * capability.
 */
static bool capable(cap_value_t v)
{ 
    bool rc = false;
    cap_t caps;
    if ((caps = cap_get_proc()) == NULL) {
        return false;
    }

    if (cap_set_flag(caps, CAP_EFFECTIVE, 1, &v, CAP_SET) == -1) {
        goto cleanup;
    }

    rc = (cap_set_proc(caps) == 0);

cleanup:
    cap_free(caps);
    return rc;
}

/* ... later on, probably in main() ... */

/* these are the capabilities libpcap needs for live capture */
if (!capable(CAP_NET_ADMIN) || !capable(CAP_NET_RAW)) {
    fprintf(stderr, "You need CAP_NET_ADMIN/CAP_NET_RAW to run this program");
    return -1;
}

```

---

### Post by Crazedpsyc on 2010-07-08
Thanks guys! now it works great! (it did work when I just ran it as root after running sudo ifconfig eth0 down) But I fixed the rest anyway

---

