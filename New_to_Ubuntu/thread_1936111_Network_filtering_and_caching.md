---
title: "Network filtering and caching"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by familyitmom on 2012-03-05
Hello. I am new to Ubuntu. We have several laptops in the family on which we've recently installed ubuntu 11.10. Several are dual boot with Windows Vista and a few are Ubuntu only. I also have an older desktop - 512MB Ram on the network. Our internet connection is via satellite because we live in the country, so we have severe limitations on bandwidth available. I have three things I would like to accomplish, possibly using the desktop as a server(?).
 
1. Create some content controls for laptops connected to the network (main priority). Because we have satellite, OpenDNS will not work (I've already looked into it).
2. Monitor the amount of internet traffic and possibly alert when a certain threshhold has been exceeded (nice but not necessary).
3. Create a caching server for Ubuntu package updates so we only have to download them once and reuse for all machines (would really be helpful).
 
I have done a lot of reading, but I am really a Linux noobie, and don't know that much about network configurations, DHCP, etc. so I'm just not sure of the best way to go about this. Things that seem simple usually still assume some knowledge that I don't yet have.
 
So, is it possible to do all 3 of these? If not, what is the best way to implement content controls for my network? I think a transparent proxy sounds like what I want, but I still don't understand exactly what that is or how to set it up. Can I use Ubuntu (or Lubuntu) desktop or do I need server? Can I use my old desktop for this? And how do I hook it up, considering I have a wireless router right now connected to my satellite modem?
 
Sorry to have so many questions; if someone could get me started somewhere I would be very grateful.

---

### Post by jailbait on 2012-03-05
> **familyitmom said:**
> Hello. I am new to Ubuntu. We have several laptops in the family on which we've recently installed ubuntu 11.10. Several are dual boot with Windows Vista and a few are Ubuntu only. I also have an older desktop - 512MB Ram on the network. Our internet connection is via satellite because we live in the country, so we have severe limitations on bandwidth available. I have three things I would like to accomplish, possibly using the desktop as a server(?).
 
1. Create some content controls for laptops connected to the network (main priority). Because we have satellite, OpenDNS will not work (I've already looked into it).
2. Monitor the amount of internet traffic and possibly alert when a certain threshhold has been exceeded (nice but not necessary).
3. Create a caching server for Ubuntu package updates so we only have to download them once and reuse for all machines (would really be helpful).
 
I have done a lot of reading, but I am really a Linux noobie, and don't know that much about network configurations, DHCP, etc. so I'm just not sure of the best way to go about this. Things that seem simple usually still assume some knowledge that I don't yet have.
 
So, is it possible to do all 3 of these? If not, what is the best way to implement content controls for my network? I think a transparent proxy sounds like what I want, but I still don't understand exactly what that is or how to set it up. Can I use Ubuntu (or Lubuntu) desktop or do I need server? Can I use my old desktop for this? And how do I hook it up, considering I have a wireless router right now connected to my satellite modem?
 
Sorry to have so many questions; if someone could get me started somewhere I would be very grateful.
1. Squid + DansGuardian [https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian) . Make sure you __only__ allow users to connect to the internet through the proxy. This means an iptables rule to deny access for LAN -> INTERNET, but to allow LAN -> SQUID.

2. As long as you don't shutdown the server, ifconfig will show the amount of data sent. VNStat does this ([https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals](https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals)) by polling the amount of data transfered every few minutes, but theirs an app that runs as a daemon too.

3. Try apt-cache-ng. This guide is for Debian, but it works for Ubuntu as well. [http://www.unix-ag.uni-kl.de/~bloch/acng/html/index.html]("http://www.unix-ag.uni-kl.de/%7Ebloch/acng/html/index.html") .

---

### Post by familyitmom on 2012-03-05
So I would put Dansguardian and Squid on the desktop machine, just running Ubuntu desktop, correct? Do I need to put the desktop between the modem and the router or do I leave it on the network side of the router?

---

### Post by jailbait on 2012-03-06
> **familyitmom said:**
> So I would put Dansguardian and Squid on the desktop machine, just running Ubuntu desktop, correct? Do I need to put the desktop between the modem and the router or do I leave it on the network side of the router?

You could deny all LAN -> WAN access, except for the desktop machine. Make sure you allow LAN-> LAN access. Leave the desktop on the network side of the router.

---

### Post by familyitmom on 2012-03-09
Ok I've downloaded Dansguardian and Squid per the link. However, I need a more basic instruction - your note about the iptables rule has me lost. Is there anything available for beginners? Or should I not even be attempting this until I know a lot more about all of this?

---

