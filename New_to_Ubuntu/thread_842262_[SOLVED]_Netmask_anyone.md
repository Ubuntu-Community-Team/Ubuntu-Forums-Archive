---
title: "[SOLVED] Netmask anyone?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-06-27
I`m trying to install Gutsy on a laptop with a broken cd drive using [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Now I`ve learned a lot  in a short space of time using ubuntu but I have to ask what might be  a really dumb question -
What is a netmask and how do I find out what mine is?
I`m in the configure the network stage of the installation.
Thanks

---

### Post by wrtpeeps on 2008-06-27
Netmask is usually 255.255.255.0

---

### Post by nothingspecial on 2008-06-27
I`ll try that then. Thanks.

---

### Post by bcom on 2008-06-27
This is not a dumb question at all; in fact, the issue of tcp/ip addressing and masks is fairly complicated.

A mask is defined as: a 32-bit number that is used to divide an IP address into 2 parts, a network ID and a host ID.

To identify your mask, open Terminal and type ifconfig at the prompt.  The mask will be identified after the inet address and bcast address.

---

