---
title: "setting static ip"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by pbarkati on 2019-01-28
Hi.I want to set a static Ip in my ubuntu by editing /etc/network/interfaces with this command:

 sudo nano /etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.200

and I edited IP there
 
But I cant ping that Ip !

---

### Post by jdeca57 on 2019-01-28
What's with that gateway? Wouldn't 192.168.1.0 make more sense?

---

### Post by pbarkati on 2019-01-28
my gateway is 192.168.1.200

---

### Post by The Cog on 2019-01-28
192.168.1.0 would not be a valid host address: it's the network address. Hosts can be 1-255.

The /etc/network/interfaces contents look OK to me. Three things come to mind: 
1: need to restart networking after changing the config, and
2: Network Manager might be changing the settings again if it's still running, and
3: Maybe sone firewall settings blocking pings. 

The command **ip addr** will list your interfaces and addresses - see if the config is applying properly there.
The command **sudo iptables-save** will print all your uptables firewall rules.

---

### Post by jdeca57 on 2019-01-28
OK and you can ping the gateway?

---

### Post by pbarkati on 2019-01-28
i can not ping 192.168.1.103 (ubunto ip) therefor can not ping gateway

---

### Post by pbarkati on 2019-01-28
when I ping 192.168.1.103
 comes:

connect:network is unreachable

---

### Post by pbarkati on 2019-01-29
any one for help??

---

### Post by SeijiSensei on 2019-01-29
What is the result when you run the command "route -n"?

Which version of Ubuntu are you running?  (You should always include that in any request since things can change quickly in the Linux world.)

---

### Post by The Cog on 2019-01-29
> **SeijiSensei said:**
> What is the result when you run the command "route -n"?

Which version of Ubuntu are you running?  (You should always include that in any request since things can change quickly in the Linux world.)

Or even just "**ip addr**"?

---

