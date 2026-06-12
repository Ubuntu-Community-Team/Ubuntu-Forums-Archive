---
title: "ethernet adapters info"
date: 2011-04-29
forum: Programming Talk
---

### Post by mayapower on 2011-04-29
Hi,

I am using this code to get info of all the ethernet adaptes on Mac OS X 10.5 Leapord.
[http://pastebin.com/fwRMAjuZ](http://pastebin.com/fwRMAjuZ)

My linux development machine is Ubuntu 8.04 hardy. On My machine "net/if_dl.h" and "net/if_types.h" are not available. How do I install them? The other method to fetch info about adapters is based in "ioctl" which is working fine but I have read in couple of articles that it has been discouraged. Using "getifaddrs", I am getting most of the required info about adapters but I am limited when using "ioctl" info. I would prefer to use same code base for both platforms.

Is it possible to compile and link above example of ubuntu 8.04?

What I need from adapters:
1. mac address
2. media status (up or down)
3. media type (wired or wireless)
4. baudrate

I am not able to get 3 and 4 using 'ioctl' method as described below:
```

     /* Iterate through the list of interfaces. */
    ifr         = ifc.ifc_req;
    nInterfaces = ifc.ifc_len / sizeof(struct ifreq);
    
    for(i = 0; i < nInterfaces; i++)
    {
        struct ifreq *item = &ifr[i];
        
        if(ioctl(sck, SIOCGIFFLAGS, &ifr[i]) >= 0)
        {
            if (!(ifr[i].ifr_flags & IFF_LOOPBACK))
            {
                printf("Name : %s\n", item->ifr_name);
                printf("Media : %s\n", (ifr->ifr_flags)&IFF_UP ? "Up" : "Down");
                printf("Bandwidth : %d\n", item->ifr_bandwidth);
                /*
                Get media type : wired or wireless 
                Get correct baudrate, baudrate is not bandwidth, am I correct?
               */
            }
        }
    }
```Cheers

Prashant

---

