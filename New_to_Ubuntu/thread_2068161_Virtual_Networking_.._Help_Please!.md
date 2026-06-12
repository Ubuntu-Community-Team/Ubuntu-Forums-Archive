---
title: "Virtual Networking .. Help Please!"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by 14309 on 2012-10-08
Hi.
I am working on Ubuntu 12.04 as host for Virtualbox VMs. In virtualbox I am running **two** Debian 6 DHCP servers for **different networks.**

Now, I want those two DHCP server virtual NICs to share one Physical NIC of my host, so that I can connect manageable switch (having VLANs) and connect client machines.

**In BRIDGED NETWORKING, for both DHCP SERVERS**
When I run my first DHCP server it gives as IP to physical NIC and if connect switch to that NIC, client PCs get IP. 
But, when I start my 2nd DHCP server, both servers conflict (as expected) i.e. other DHCP wants to give IP address to the same Physical NIC.

How can I do this? Please Help!

---

### Post by jingaling on 2012-10-08
In short, it can't be done.

To clarify, you have 2 DHCP servers that provide leases for two different networks on two different subnets.

You then want these two virtual subnets to connect to a single managed switch that has VLAN's to seperate the networks...all though one physical NIC on your host machine. Is that correct?

If so, then you can't do it. You see, the switch will only have one physical connection to your host. A NIC can only exist on a single network at any one time. Therefore this architecture won't work as you physical NIC will need to be bridged to a virtual NIC on one of your DHCP servers.

I would recommend putting a cheap secondary NIC in your host you can then have two physical connections to your managed switch. These can then be bound to a DHCP server each and then on to a VLAN.

I really don't think this post is apporiopriate for "absolute beginner talk", I would see it more in the networking section, or even on the VirtualBox forums. Anyway, I hope this information helps.

If I have you setup wrong, please sketch up a quick topology with subnets and I will take a look for you.

Jing

---

### Post by 14309 on 2012-10-08
Hi. Thank you for the reply.  You got all that right. 
I am newbie in Linux and Networking, so posted here. 

Is it possible to split my physical NIC in two virtual NICs e.g. 'Eth0' and 'Eth0:0 or Eth0:1' .. and then I can assign IPs to them?

---

### Post by lemming465 on 2012-10-08
To slightly amend jingaling's "It can't be done"; it's going to be somewhere between impossible and very hard, and success is not solely under the control of your host but depends critically on the behaviors of the upstream switch and network.  If you are trying to connect outside clients via a single physical interface to two different virtual subnets, you either have to:

1) have the outside LAN routing multiple subnets, and your host doing proxy ARP for all the inside clients

2) Or better, have the uplink between your host and the managed switch be a "trunk" port, using 802.1Q vlan tags to differentiate the traffic of the two subnets.

Without knowing a lot more about your firewall, routing, layer 2 switch layout, etc. it's going to be hard to give any decent advice.  E.g. are the inside network IPv4 or IPv6, and if IPv4, are they on public IP space or private?  If private, who is trying to get to the clients, and are they going through NAT44, and for which protocols.

---

### Post by pqwoerituytrueiwoq on 2012-10-08
yes you can split a net card to eth0:X
but you can't run (technically shouldn't) run 2 HDCP servers on 1 nic card
if you connect 2 DHCP servers to a unmanaged switch which will be assigning addresses
i have done something similar
cable modem -> unmanaged switch -> Desktop (eth0) -> eth0:1 -> unmanaged switch -> laptop/Virtualboxes on bridged adapter
the modem only supplies one address and it locks on to a single MAC address
DHCP's server configuration
```
shared-network 224-29 {
    subnet 10.0.0.0 netmask 255.255.0.0 {
        range 10.0.0.100 10.0.0.199;
        option routers 10.0.0.1;
        option domain-name-servers 8.8.8.8,8.8.4.4;
    }
}
# don't assign own address
host dhcp-server {
   #MAC for eth0
   hardware ethernet 00:00:00:00:00:00 ;
   deny booting ;
}
```from my /etc/rc.local
```
echo 1 > /proc/sys/net/ipv4/ip_forward
while [ 0`pidof NetworkManager` -eq 0 ]; do
    sleep 1
done
#wait for modem to assign address
while [ "`ifconfig eth0 | grep 'inet addr:'`" = "" ]; do
    sleep 2
done
#create virtual NIC
while [ "`ifconfig eth0:1 | grep 'inet addr:'`" = "" ]; do
    sleep 2
    ifconfig eth0:1 10.0.0.1 netmask 255.255.0.0
done
#port forwarding (not sure if i ever got that working)
#iptables -t nat -A PREROUTING -o eth0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.75:80
#allow others to access internet
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -P FORWARD ACCEPT
service dhcp3-server start
```

---

### Post by jingaling on 2012-10-08
Basically its extremely difficult and would make things much simpler if you just use 2 nics on your host.

Ever heard of the KISS principle? It stands for Keep It Simple Stupid (im not calling you stupid by the way). Its a metaphor meaning you should always keep things as simple as possible. Theres no point in over complicating things of you dont need to?

Maybe it would be a better idea to tell us what you're trying to achieve, ie why do you need 2 dhcp servers? Then se may be able to offer up some advice on how best to achieve your aim.

Sorry for any poor spelling or grammar, im on my tablet.

---

### Post by 14309 on 2012-10-09
> **jingaling said:**
> Basically its extremely difficult and would make things much simpler if you just use 2 nics on your host.

Ever heard of the KISS principle? It stands for Keep It Simple Stupid (im not calling you stupid by the way). Its a metaphor meaning you should always keep things as simple as possible. Theres no point in over complicating things of you dont need to?

Maybe it would be a better idea to tell us what you're trying to achieve, ie why do you need 2 dhcp servers? Then se may be able to offer up some advice on how best to achieve your aim.

Sorry for any poor spelling or grammar, im on my tablet.

I also, want to keep is simple. But my project is a bit complected itself i.e. virtually connecting the DHCP servers and behind those server will be a SIP server to provide service to the clients of respective subnets. 
For now, it is with 2 DHCP servers/ 2 networks, in future it might expand if everything goes smooth for now. 
Also, Security is not main concern for now .. but i will have to implement some.

---

### Post by lemming465 on 2012-10-10
I agree with jingaling that this would be easier with two NIC's.  I also concur with pqwoerituytrueiwoq that it might be easier to have one DHCP daemon servicing the multiple subnets.  If things get really complicated you might have to instantiate extra kernel routing tables to handling the packet forwarding properly.

---

