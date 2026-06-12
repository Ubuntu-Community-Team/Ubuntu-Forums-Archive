---
title: "Storing connection state information in NetFilter Kernel Module"
date: 2013-05-13
forum: Programming Talk
---

### Post by mikeduk on 2013-05-13
Hi, I'm fairly new to Linux and very new to Linux programming, especially anything near the Kernel so I'm having a little trouble with something.

I have written a NetFilter module using the nf_register_hook hooks to trap packets going in and out of the system. This works great and I've even got the connection tracking module working so I can call nf_ct_get to get some connection information relating to the packet. I've now come to the bit that *should* be the easiest! Basically what I want to do is record some information along with the connection that I can access / change for each packet sent associated with that connection.

Ideally this would be done by accessing some sort of user data in the nf_conn* structure but I cannot see any obvious way of doing that. Something like:

```

ct = nf_ct_get(skb, &ctinfo);

if (ct != 0)
{
    if (ct->userData == 0)
        ct->userData = malloc(...)

    ...blah..blah
}

```

But of course userData does not exist!!

Failing that I could simply use my own hash set and store the data myself in the module using some sort of hash key like srcIP:port-dstIP:port allowing me to access the data each time a packet comes through.

I understand that there are hash libraries available and I've tried a few but they all appear to use the std libraries which according to ([http://lwn.net/Articles/113349/](http://lwn.net/Articles/113349/)) should not be used in Kernel space.

So the question is, what is the best way of storing this data in memory so that I can access it for each packet that comes through?

---

