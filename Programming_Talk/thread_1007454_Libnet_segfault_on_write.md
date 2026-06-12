---
title: "Libnet segfault on write"
date: 2008-12-10
forum: Programming Talk
---

### Post by band-aid on 2008-12-10
I'm playing around with libnet as a way to get a better handle on various protocols and C in general. I am attempting to send a single ARP reply to the broadcast address but my program segfaults when I I do libnet_write(). I think I may have a problem with my parameters for the two build functions, potentially a network byte order issue. My code is a bit long (102 lines) so I'll put it up on pastebin. Any ideas?

[http://pastebin.com/m494cf2d8](http://pastebin.com/m494cf2d8)

Thanks

band-aid

---

### Post by odyniec on 2008-12-10
In the two libnet_build_* calls, shouldn't you set the eth and arp variables to zero prior to passing them as parameters?

---

### Post by band-aid on 2008-12-11
Yep, that was it. It was not creating the pblocks because that a non-zero value in that parameter means that it is supposed to edit an existing pblock rather than create a new one.

Cheers! :popcorn:
band-aid

---

