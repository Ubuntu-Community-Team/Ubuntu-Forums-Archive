---
title: "modify the tcp/ip stack"
date: 2008-04-07
forum: Programming Talk
---

### Post by NehaMehta on 2008-04-07
I need to modify the tcp/ip stack for which i must know where it resides. Can I get the exact path address to the interface between the data link layer and the network layer and any other that I should know. This is for my thesis. Thank you.

---

### Post by themusicwave on 2008-04-07
I'm not sure where it resides and I am not at my computer right now so I can't look.

What exactly are you trying to do?  It may not require modifying the stack.

---

### Post by pedro_orange on 2008-04-07
I've not done this before....

But I had a look and found the Makefile for the Linux TCP/IP (INET6) layer in ./usr/src/linux-headers-2.6.22-14/net/ipv6.

There is a v4 as well.

I'm sure if you download the source you can get the stuff you need.

---

