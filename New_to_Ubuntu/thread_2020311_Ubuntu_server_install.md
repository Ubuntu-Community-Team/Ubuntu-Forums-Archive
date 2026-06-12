---
title: "Ubuntu server install"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by wiradog on 2012-07-08
Hi guys,
I have just installed Ubuntu server on a new set-up, with the intention of creating a home NAS.
I could do with some advice on connecting the system to a wireless router, which at present is my home network.
I will need to access the NAS from outside, and presume I will need to set up a VPN to connect to the NAS, but am not sure of what the setup with the wireless router would be with regard to IP configuration at the moment the router is running a DHCP server. I am reluctant to set fixed IP addresses on the router as it would mean setting a fixed address every time I wanted to connect to the router with a portable device like my laptop.
Any advice on this part of the setup would be appreciated.
](*,)

---

### Post by Ms. Daisy on 2012-07-09
You need to assign the server a static IP address, otherwise how will you access it consistently from outside the LAN?  Some ISPs won't allow you to set an external static IP, but if that's the case you probably won't get a new IP often unless you shut off the router or lose power a lot.  If your router uses DHCP to assign IP addresses to internal devices you can always reserve a 192.168.x.x IP for the server, then you can port forward permanently on your router.  See this post for more info on setting a static IP: [http://ubuntuforums.org/showpost.php?p=11817884&postcount=3](http://ubuntuforums.org/showpost.php?p=11817884&postcount=3)
 
For accessing the NAS from outside your LAN, I would recommend ssh.

---

### Post by wiradog on 2012-07-10
Thanks Ms Daisy, I have a Belkin F5D7632-4 router, I have been on to Belkin and they say this router does not support reserve IP addressing. I suppose I could set all devices to fixed IP, but this would mean me changing my laptop to a fixed IP to access the system, the other devices it would not matter-or of course buy a new router!

---

### Post by Bucky Ball on 2012-07-10
Don't set the static IP on the router, set it on the local machine in Network Manager (or /etc/network/interfaces from memory). You can then switch the DHCP server and static IPs on the router off or you can leave the DHCP server on and limit the range. For instance:

Your server = 192.168.0.100
Router DHCP server set to serve in the range 192.168.0.110-120, in case you have visitors or the router needs to serve and IP to other machines on the LAN.

That way the server forces the 192.168.0.100 and the router doesn't bother because it's not trying to serve in that range. Just accepts the static IP from your local machine. Easy. ;)

As mentioned by Ms Daisy, you need a static IP on the server if you want to accomplish your intentions. Makes life easier anyhow, I think. I have six devices on the router with static IPs, but when people visit and want to get their machine online, the router serves them an IP in the range I have set, no problems, and all good.

---

### Post by wiradog on 2012-07-11
Thanks Bucky Ball, that works, just got to see the server from beyond the router now.

---

### Post by Bucky Ball on 2012-07-11
Great news. Enjoy. ;)

---

