---
title: "Trouble Setting Up Static IP"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by littleteapot on 2008-10-06
Well, I have one foot in the door when it comes to Linux, but there's a vicious dog inside that wants to eat my foot. 

Anyway, I've been trying to set up a static IP for port forwarding, but the network manager didn't work for me (and even when I switched it back to roaming, I still had to restart the computer to get it to work again). And everything I read relates to wireless, or doesn't work for me otherwise. My router is a linksys wrt54gs, so I can't just set the IP in the router. 

So my question is essentially this, how do I set up a static IP for a wired connection in Ubuntu 8.04? 

As I said, I've looked around at how-tos, etc, and been confused for the last couple hours.

---

### Post by imperius69 on 2008-10-06
i don't understand you problem but ill try to help, in top right there the network icon, just click and choose manual configuration. There you have to choose your network card then properties, choose static IP, write the ip you want, set the gateway. also you need to set up the DNS (usually the same ip as you gateway). It should work flawless.

---

### Post by hyper_ch on 2008-10-06
what version of ubuntu are you using?

---

### Post by halitech on 2008-10-06
you could try using a different firmware like DD-WRT to give you additional features for the router, like static IPs based on the MAC address

---

### Post by kpkeerthi on 2008-10-06
> **littleteapot said:**
> Well, I have one foot in the door when it comes to Linux, but there's a vicious dog inside that wants to eat my foot. 

Anyway, I've been trying to set up a static IP for port forwarding, but the network manager didn't work for me (and even when I switched it back to roaming, I still had to restart the computer to get it to work again). And everything I read relates to wireless, or doesn't work for me otherwise. My router is a linksys wrt54gs, so I can't just set the IP in the router. 

So my question is essentially this, how do I set up a static IP for a wired connection in Ubuntu 8.04? 

As I said, I've looked around at how-tos, etc, and been confused for the last couple hours.

I suggest you leave your PC in roaming mode (the default) and change your router settings to serve a 'fixed' IP to your PC. Most routers can do this based on MAC address.

---

### Post by halitech on 2008-10-06
the wrt54gs doesn't have that option unless he changes the firmware

---

### Post by casper_2095 on 2008-10-08
Try a torrent client which has uPnP?

---

### Post by taladan on 2008-10-08
you can set a static IP address on your computer outside the range of DHCP on the router.

If your router gives out

192.168.1.100-192.168.1.150

(standard for the linksys routers)

And your netmask is 

255.255.255.0

Then you can statically assign an ip address from 192.168.1.2-192.168.1.99 & 192.168.1.151-192.168.1.254

This will remain in your subnet, outside of your DHCP pool and you can port forward to that address.

The 54g will route this way.

Tal

---

### Post by Iowan on 2008-10-08
> **littleteapot said:**
> So my question is essentially this, how do I set up a static IP for a wired connection in Ubuntu 8.04? 
Edit **/etc/network/interfaces**. From my (Breezy) server:```
# The primary network interface
iface eth0 inet static
        address 192.168.1.9
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
auto eth0

```Your information may be slightly different.  After this - **/etc/init.d/networking restart**.  Check **ifconfig** to see if the address stuck.

---

### Post by littleteapot on 2008-10-11
Iowan, I tried that. But it doesn't connect. ifconfig does seem to indicate that the settings stuck, but it won't connect to the internet. Out of curiosity, when I go into System -> Admin -> Network Tools, and choose network device to be eth0, and then click configure, it says the interface doesn't exist, is it possible it's related to that? eth0 has always shown up on ifconfig though.

---

### Post by wizard10000 on 2008-10-11
> **littleteapot said:**
> Well, I have one foot in the door when it comes to Linux, but there's a vicious dog inside that wants to eat my foot. 

Anyway, I've been trying to set up a static IP for port forwarding, but the network manager didn't work for me (and even when I switched it back to roaming, I still had to restart the computer to get it to work again). And everything I read relates to wireless, or doesn't work for me otherwise. My router is a linksys wrt54gs, so I can't just set the IP in the router. 

So my question is essentially this, how do I set up a static IP for a wired connection in Ubuntu 8.04? 

As I said, I've looked around at how-tos, etc, and been confused for the last couple hours.

IMO the best way to do this is to use a MAC reservation on the router and continue to use a DHCP client on the Linux box.  You can set a static IP outside the DHCP scope but on the same subnet and then use the router to assign the address - that's the way I do it on both home and work networks.

Just my opinion, but if you're using DHCP then all devices on the subnet should get their address from the same place - make for much easier troubleshooting  ;)

---

### Post by littleteapot on 2008-10-11
I can't set static IPs in my router. And I'd rather not change the firmware unless I really have to.

---

### Post by wizard10000 on 2008-10-11
> **littleteapot said:**
> I can't set static IPs in my router. And I'd rather not change the firmware unless I really have to.

I've never seen a SOHO router that *couldn't* assign static IPs  ;)

No firmware installation required.

edit:  y'all are correct - the WRT54GS can't do DHCP reservations without a firmware upgrade, which sucks mightily.  My WRT54GC can and is configured that way - I've also done it with Netgear and US Robotics routers.

---

### Post by Louis de Broglie on 2008-10-11
> **littleteapot said:**
> when I go into System -> Admin -> Network Tools, and choose network device to be eth0, and then click configure, it says the interface doesn't exist, is it possible it's related to that? 

Maybe not. Because i have internet with static ip and I also receive that message :)

Try this : go to System -> Administration -> Network tools -> ping. Then try pinging. If you get echo , then check dns server settings in /etc/resolv.conf . If you don't get echo , then set up your connection manually they way others said. Then reboot. This should work. :)

---

