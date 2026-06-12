---
title: "Configure network through terminal"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by lalit0611 on 2013-02-24
I am trying to configure static ip network. I opened /etc/network/interfaces and it looks like this

auto eth0
iface eth0 inet static
address "IP address"
gateway "gateway ip"
netmask "subnermask ip".

I also set the DNS server in /etc/resolv.conf under nameserver. I then restarted networking.
It shows this error:

root@bt:/etc/network# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                       
SIOCDELRT: No such process
SIOCADDRT: No such process
Failed to bring up eth0.

Did i do something wrong? Pls help.

---

### Post by steeldriver on 2013-02-24
Hello and welcome to the forums

What version and type (desktop/server) of Ubuntu are you running please?

---

### Post by lordievader on 2013-02-24
The IP-addresses between the "" are actual IP-addresses I presume?
Is there in the 'interfaces' file also a dot after the netmask IP-address? If so it shouldn't be there.

-lordievader.

---

### Post by lalit0611 on 2013-02-24
yeah the ip address is the actual ip and there is no dot at the end.

---

### Post by lalit0611 on 2013-02-24
@Steeldriver I am using ubuntu 10.04desktop with kde environment

---

### Post by prodigy_ on 2013-02-24
Are you sure the gateway address you specified belongs to the subnet?

---

### Post by matt_symes on 2013-02-24
Hi

Try removing the quotes around the ip addresses.

Can you post the entire file as well.

Kind regards

---

### Post by lalit0611 on 2013-02-24
auto eth0
iface eth0 inet static
address 10.6.22.173
gateway 10.6.70.250
netmask 255.255.224.0

I have used the same configuration in the windows and it is working.
To be precise i'm using BackTrack 5 R3.

---

### Post by matt_symes on 2013-02-24
Hi

That is a configuration problem.

> 
address 10.6.22.173
gateway 10.6.70.250

Put these two on the same subnet or they will not talk to each other.

maybe.....
```

address 10.6.70.173
gateway 10.6.70.250
```

Kind regards

---

### Post by lalit0611 on 2013-02-24
Tried it in other room, problem solved. Seems like ip config of my room is bit unusual but the same config works in the windows. Anyway  thanks for such quick replies :)

---

