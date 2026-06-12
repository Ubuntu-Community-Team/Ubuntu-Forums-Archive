---
title: "Can Only Ping in One Direction"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by andy51 on 2014-06-15
Hi all,

I am a complete Linux/Ubuntu newbie, and I'm hoping someone can help me with a problem I'm having. I have two PCs connected together through a Netgear switch that I'm trying to get to talk to each other.  I've created a new Ethernet connection in the network options, and I manually assigned IP addresses to my computers - one as 10.0.0.1 and the other as 10.0.0.2. 
To check I had the connection set up correctly I opened the terminal and just entered 'ping 10.0.0.1' which returned ok.  But when I tried to ping the other with 'ping 10.0.0.2' I get a message back saying 'host unreachable'.

If anyone can help me with suggestions I'd be very grateful! I'm assuming its an error I've made in the network configuration or some such.

Many thanks!!

---

### Post by brantcgardner on 2014-06-16
Based on your description you pinged yourself and got a reply and then pinged the other host and did not.  That's not actually a successful ping, since it never actually traversed your network.  Start by showing us the output of:

```

ifconfig

```

and

```

cat /etc/network/interfaces

```

returns on **both** hosts.  From there we should be able to help you pretty quickly.

---

### Post by andy51 on 2014-06-16
Hi and thanks for the reply.

i just managed to get this fixed it was a setting in the firewall on one of the pcs that was preventing the connection.

thanks!

---

