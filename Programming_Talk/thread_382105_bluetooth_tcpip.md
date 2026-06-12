---
title: "bluetooth tcp/ip"
date: 2007-03-11
forum: Programming Talk
---

### Post by docetes on 2007-03-11
hi,

I'm trying to get my pda and laptop to talk to each other. I have coded up a chat server client that works over tcp/ip but i can't seem to get it working with bluetooth. It works on my machine when the client and the server are on the one machine. I have tried to use the laptops ip address but that doesn't seem to work. Any suggestions?

Thanks,
Dave

---

### Post by docetes on 2007-03-12
bump??

---

### Post by jblebrun on 2007-03-14
> **docetes said:**
> hi,

I'm trying to get my pda and laptop to talk to each other. I have coded up a chat server client that works over tcp/ip but i can't seem to get it working with bluetooth. It works on my machine when the client and the server are on the one machine. I have tried to use the laptops ip address but that doesn't seem to work. Any suggestions?

Thanks,
Dave

Have you set up PAND/BNEP so that you can run TCP/IP over a Bluetooth link? Your PDA will need to support this, as well. 

See if this link helps:
[http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)

---

