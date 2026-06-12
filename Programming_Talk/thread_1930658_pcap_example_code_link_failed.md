---
title: "pcap example code link failed"
date: 2012-02-24
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2012-02-24
Hi

I'm trying to test the pcap however I can't link the following code:
```

#define HAVE_REMOTE

#include <pcap.h>
#include <stdlib.h>

#define PCAP_SRC_IF_STRING   "rpcap://" 

int main()
{
    pcap_if_t *alldevs;
    pcap_if_t *d;
    int i=0;
    char errbuf[PCAP_ERRBUF_SIZE];

/* Retrieve the device list from the local machine */
    if (pcap_findalldevs_ex(PCAP_SRC_IF_STRING ,NULL ,&alldevs, errbuf) == -1)
    {
        fprintf(stderr,"Error in pcap_findalldevs %s\n", errbuf);
        exit(1);
    }

/* Print the list */
    for(d= alldevs; d != NULL; d= d->next)
    {
        printf("%d. %s", ++i, d->name);
        if (d->description)
            printf(" (%s)\n", d->description);
        else
        printf(" (No description available)\n");
    }

    if (i == 0)
    {
        printf("\nNo interfaces found!\n");
        return (1);
    }
    pcap_freealldevs(alldevs);
    return 0;
}

```I have tested it with libpcap 1.1.1-2 from the ubuntu repozitory and also I downloaded the latest version from [http://www.tcpdump.org/](http://www.tcpdump.org/) and compiled it myself with prefix and then invoked gcc with that particular pcap-config but it is still giving me that error.

How can I solved it?

Thanks in advance.

EDIT:
forgot to add the error :)
```

/tmp/ccGQPBkK.o: In function `main':
device_list.c:(.text+0x48): undefined reference to `pcap_findalldevs_ex'
collect2: ld returned 1 exit status

```

---

### Post by Mr.Pytagoras on 2012-02-24
well

I figured that it can't be figured :D because the 

```

int pcap_findalldevs_ex (char *source, struct pcap_rmtauth *auth, pcap_if_t **alldevs, char *errbuf)

```

is windows specific extension to pcap

NICE :)

anyway, I'm going to keep this thread unsolved for some time and if someone managed to somehow run those function on linux please don't keep it for yourself.

---

