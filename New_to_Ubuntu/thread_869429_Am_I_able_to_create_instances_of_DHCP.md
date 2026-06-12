---
title: "Am I able to create instances of DHCP?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by sgscit on 2008-07-24
Hi Folks

I've been a long time lurker in the forums and have finally decided to see if I can get Ubuntu doing what I need at work.

Am I able to create instances of DHCP or similar so that I can run 1 DHCP server and serve multiple subnets?  

In other words, can I have 
eth0 serving 192.168.0.0
eth1 serving 192.168.1.0
eth2 serving 192.168.2.0
etc

I think this would be a neater solution that creating new installs of Ubuntu on ESX to do our 9 subnets!

Windows is hopeless at this sort of thing though it "sort of" works.

Cheers

Pete

---

### Post by NetworkGuy on 2008-07-24
I'm not sure what you are asking here?   

From what I get -> You have 9 subnets that do not see each other.  You do not have any routers between the subnets?

If the above is true, I think you will can use 1 DHCP server, but I'm not sure on the actual configuration.

If you do have routing between the interfaces, you can use the dhcp-helper command or whatever your router uses to forward the broadcast to the DHCP server that resides on one subnet.

Also remember that ESX only supports 8 GB Ethernet Interfaces or 16 100MB Ethernet Interfaces total.  The easy way to calculate this is each Gig interface counts as 2 and each 100MB interface counts as 1.  When you hit 16, you are at the limit.

---

### Post by sgscit on 2008-07-24
Thanks for the reply NetworkGuy. 

We have a number of subnets all hanging off one subnet with layer 3 switches seperating them.  I can get windows 2003 to serve the addresses using a superscope but it can be a bit hit and miss especially if a portable PC moves sites.

*********              *********              *********
*subnet1*----Router----*Subnet2*----Router----*Subnet3*
*********              *********              *********
                           |
                          DHCP
                          Server

The reason I was asking for seperate eth's is that I can assign seperate IP's to them and simply point the helper-address to the IP.

A superscope that works properly (unlike the windows one!) would be perfect and not require multiple eth's.

Cheers

Pete

---

### Post by bab1 on 2008-07-24
I believe that the notion of subnets is not really correct here.  The examples you have listed are separate networks of their own.  Do you really want to experiment with "sub" netting?  As in splitting 192.168.1.0/24 into 2 networks?  This would get you "network" addresses of 192.168.1.0/25 and 192.168.1.128/25.  Each subnetwork would have 126 addresses available.

As network guy stated, you have to use dhcphelper to cross any network or subnet.  You should use a separate dhcp server for each subnet to reduce problems.  You should look for containment and reliability.

By supercope, could you mean (using my example) of 1 dhcp server for both 192.168.1.x subnets?  If so you would need to have 2 ranges - 192.168.1.1 to 192.168.1.126 and 192.168.1.129 to 192.168.1.254

---

