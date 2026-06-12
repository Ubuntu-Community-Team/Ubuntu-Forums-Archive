---
title: "ubuntu 13.04, static ip and comcast xFinity internet"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by squakie on 2013-07-11
I don't know where else to post this.  I have a thread open in the networking forum where someone very kind and VERY patiant is helping with getting my attempts at 2 servers working correctly on the local net.  Nobody has replied back in the middle of that thread when these problems were first encountered, so I hope posting here will perhaps find someone who doesn't watch the networking forum but has this working.

Scenario:
[LIST]
[*]Ubuntu 13.04 
[*]Comcast xFinity internet/cable/phone using their access point gateway/router 
[*]need to set up a static IP connection and get the DNS working 
[/LIST]

I have tried:
[LIST]
[*]defining the connection in network manager as manual (there's no static entry), entered in the information and tried to use nothing in the DNS servers.  Since it was no longer DHCP, no DNS servers where returned to the PC so it can't go anywhere. 
[*]same as above, but putting the 2 DNS server addresses in that show with a "regular" (DHCP) connection - can't resolve anything. 
[*]same as above, but putting the 2 Google public DNS server addresses in.  Still nothing 
[*]setting up an /etc/interfaces file with the connection as static and all the information (address, gateway, netmask, wpa-passphrase and wpa-ssid) to see if would at least connect to the local network.  EDIT: (corrected original):  on trying ifup it bombs out with a message about not being able to start wpa-supplicant.  Now, I do still have network manager running, but the wireless is disconnected.  I tried about a week ago to install wicd and remove network manager, which resulted in a non-usable system so I had to completely rreinstall Ubuntu.  In the process I lost the disk contents that included 280+ videos I had run through Handbrake and stored on the disk (needless to say, a LOT of time lost). 
[*]same as above, adding dns-nameservers with the Google public DNS server addresses. The same wpa-supplicant problems.  Never connects to a network. 
[/LIST]

So, what do I need?
[LIST]
[*]a true static IP address, defined in /etc/interfaces as a static connection 
[*]DNS working 
[/LIST]

I suspect this is something with comcast setting my search to 127.0.1.1 followed by the 2 nameservers, and using a search prefix.

Does anyone have anything like this working, and if so, can you tell me how you got the DNS working - how they are defined?

Your help is GREATLY appreciated!

---

### Post by Gone fishing on 2013-07-11
Here's a very easy gui way [http://radu.cotescu.com/ubuntu-internet-connection-sharing-wireless/](http://radu.cotescu.com/ubuntu-internet-connection-sharing-wireless/)

Not done that - I've used a squid proxy but I would think a commandline method will be - get rid of network manager on the gateway server and use /etc/interfaces I guess you are using 2 nics one connected to the router and the other to your internal network. To see howto use the /etc/interfaces see  [http://wiki.debian.org/NetworkConfiguration](http://wiki.debian.org/NetworkConfiguration). This howto also explains how you setup the DNS resolve. You could uninstall network manager and resolvconf program and the manually edit resolv.conf or add a dns-nameservers line to the /etc/interfaces (I would do that). 

You will need to setup port forwarding so the PCs connected to one nic can communicate with the other see [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) the section on Ubuntu Internet Gateway Method (iptables). Then install the DNS server see [http://lani78.wordpress.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/](http://lani78.wordpress.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/).

I would also install Webmin a browser based admin program it just makes things easier [http://www.webmin.com/](http://www.webmin.com/)

To test first make sure the clients get an IP address > can they ping theserver > can they ping the gateway > can they ping the DNS servers > can they ping websites if so it all works.

---

### Post by squakie on 2013-07-11
Thanks for the reply.  I'm not doing any connection sharing.  I simply have their access point, 2 computer that I'm making into servers, each wireless, a total of 4 possible tablet or ereader devices that might come on the network off and on, and a couple of Windows laptops that will come on and off the network.  Everything is wireless.

If I go into the router portion of the access point I can set what they call "static" addresses by lowering the DHCP limit and defining connections with fixed addresses by MAC address.  That works, but the PC still thinks it DHCP, so it is provided with the dns servers, etc., yet via the downloads from the server because of DHCP.

I want truely static addresses - those you actually declare as static in the /etc/interfaces file.  I have found by leaving network manager up, just the wireless disconnected from the network, that I can connect.  But I still have no DNS.  I have put everything in just as the contents of the resolv.conf shows when the connection is using network manager and DHCP.  With what I currently have in the /etc/interfaces file it connects to the wpa2 network fine, as witnessed in the output of iwconfig.  The IP address is the one defined, as witnessed by the output of ifconfig.  The problem comes in trying to use anything that requires DNS - it doesn't work.  So, I need to know 2 things:

1. how to get the DNS servers defined so they will work in the /etc/interfaces file - and this seems to be related directly to how the access point is configured somewhere.

2. without network manager at all, how to get wpa-supplicant to start correctly when the ifup is given for the wireless interface.

---

### Post by Gone fishing on 2013-07-11
Don't you just need the dns-nameservers line in the /etc/interfaces file.

I'm not dead sure quite what you are doing but on the  Iclients why not use network manager dhcp etc. The turn off DHCP in the router and then setup the server to do DHCP and tell the clients where the gateway is what the DNS servers are etc?

---

### Post by steeldriver on 2013-07-11
It sounds like you have at least 2 separate problems (DNS resolution and wpasupplicant)

Aside from possible wpasupplicant issues, two of the things you tried *should* have worked (setting a 'Manual' IPv4 config in the network manager applet, with specified DNS servers; and setting everything via /etc/network/interfaces with a dns-nameservers entry). The fact that they didn't suggests a problem somewhere else in the name resolution subsystem, possibly the resolvconf service - start by checking

```

service resolvconf status

ls -l /etc/resolv.conf

cat /etc/resolv.conf

```

```
dpkg -l | grep supplicant
```

Why exactly can't you do what you want via DHCP reservation based on interface MAC at the router?

---

### Post by squakie on 2013-07-11
I've actually used exactly what showed in resolv.conf (with the correct keywords) in interfaces but to no avail.

I can actually do the reservation at the router - set the DHCP limit down so there is a pool of addresses above DHCP (that's the way the router wants it) and it does work.  I was hoping I could get this working via the interfaces file and learn something along the way, but the DNS seems to be a barrier.  I read a thread somewhere about the gateway/router I have from Comcast actually does some sort of "prozy" (I *think that's what they called it) for DNS.

At any rate, doesn't seem to want to work for DNS.

For your other question:
```
dave@dwezbox1:~$ dpkg -l | grep supplicant
ii  wpasupplicant                             1.0-3ubuntu1                           amd64        client support for WPA and WPA2 (IEEE 802.11i)
dave@dwezbox1:~$ 
```

I would like to get this working so it matches what the kind knowledgable helper in my thread in the networking forum had wanted.  I think he decided that as long as I can guarantee a fixed address that is the same each time it would be okay just so we can go on and try to solve the rest of my problem(s).

I wanted to take at least today "off" from that thread to give them a break from me - they have been extremely helpful and extremely tolerant of me, but they deserve a break.  So, if I could get this working via interfaces it would be great, otherwise I'll just leave it as being handled by the router with the "fixed" address requested.

I also need to find out about some other things before posting back on the other thread, so I've got a lot of research to do and hope I get solutions and the appropriate knowledge for those - things I don't know squat about.

EDIT:  I found what was being mentioned about Comcast and this access point - it's doing something they call a transparent DNS proxy where they intercept any DNS request and route them themselves.  It seems this is a problem for more than me.  I did a search on that DNS proxy stuff and found [this]("http://www.dnsleaktest.com/what-is-transparent-dns-proxy.php") link which helped me understand a little better.  So, I have to stick to doing it on the router.

---

### Post by squakie on 2013-07-11
Well, I'm just going to leave it at the router for now.  I think this DNS proxy stuff is what is messing everything up (EDIT: I should say the DNS assignment stuff).

I probably won't be watching this thread now very often since I need to move on.  I consider it solved for me, but I got reported by someone for marking threads solved (as in my problem is solved) but there wasn't any solution posted.  So......this will just be another dangling thread some admin will have to clean out in a year or two.

---

