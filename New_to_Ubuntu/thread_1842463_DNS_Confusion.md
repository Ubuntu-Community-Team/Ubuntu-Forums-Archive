---
title: "DNS Confusion"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by pgp_protector on 2011-09-11
I'v got a Domain hosted externally at xyz.com

I wan't to have an internal domain sub.xyz.com for inhouse use.

Now I know I can modify the HOST files on all the computers to point to 192.168.1.50 (my ubuntu server address), and it works.

Right now the Router/Firewall (Netgear) assigns the IP Address for the computers on the network & acts as the DNS for the network.

but like this, I can't access my domain (as it's really just an internal address, and I'm not needing external access to it yet)

What I want to do (if possible) is instead of having the firewall get the DNS from the ISP, is have it set to use the UBUNTU Box
so I set the Primary DNS to 192.168.1.50 (this appears to work) as I'm still able to find external stuff.

But when I try to go to sub.xyz.com I can't find it (so it appears as though the DNS isn't actually working)

Using UBUNT 11.04 With ISPConfig 3.0.3.3 & Webmin.
DNS = BIND DNS.

---

### Post by terrykiwi83 on 2011-09-11
If your hosting xyz.com externally and you edit the DNS record to point to your internal Ubuntu machine you would not point it to 192.168.1.50 you would point it to your WAN address and have your router forward the traffic to 192.168.1.50. Thats what I see as being wrong?

---

### Post by Drenriza on 2011-09-11
Strange way of doing stuff?

This is how i see it.

#1 Connect your router to your wan.
#2 Connect your ubuntu server to the router, and get it to point at your wan address. To get outside your network. Set DHCP to point at itself for clients to use as DNS server.
#3 Connect your clients through the server.

---

### Post by pgp_protector on 2011-09-11
> **terrykiwi83 said:**
> If your hosting xyz.com externally and you edit the DNS record to point to your internal Ubuntu machine you would not point it to 192.168.1.50 you would point it to your WAN address and have your router forward the traffic to 192.168.1.50. Thats what I see as being wrong?

On the external server (web host) I assign the IP address to my ISP's assigned address.
On the Firewall I was trying to use that to assign the IP address for the network, as every time I try to use webmin to configure the DHCP server, it isn't saving any of the changes ???.

---

### Post by pgp_protector on 2011-09-11
> **Drenriza said:**
> Strange way of doing stuff?

This is how i see it.

#1 Connect your router to your wan.
#2 Connect your ubuntu server to the router, and get it to point at your wan address. To get outside your network. Set DHCP to point at itself for clients to use as DNS server.
#3 Connect your clients through the server.

1) works
2) ???
3) Only one connection on this box

---

### Post by pgp_protector on 2011-09-13
Ok, got it working.

Router Changed Get DNS from Server to the IP Address of my Box.

ISPConfig. 
   Create Sites like testing.realsite.com
                  or beta.realsite.com
WebMin Create "Master Zone" for each Subdomain 
So for each Master Zone I use the domain of testing.realsite.com or beta.realsite.com (not realsite.com)

Masterserver -> my Linux box
IP Address -> Internal IP Address of Box.

for each new MasterZone I just add 
   www -> Internal IP Address of Box
   blank -> Internal IP Address of Box
   ftp -> Internal IP Address of Box

this allows me to go to [www.realsite.com](www.realsite.com) on the Internet
or testing.realsite.com on the Intranet without messing with each computers HOST File.

---

