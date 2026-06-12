---
title: "How-To: Accent on: Do a successeful NAT (Anti-NastyISP Edition)"
date: 2006-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by EmanuilTolev on 2006-11-26
Startup Script for successeful IP Masquerading (under the following conditions):
 1. When your nasty ISP doesn't allow more than 1 computer to use the Internet and wants you to buy another static real IP from them just for the sake of having access to Internet on your laptop, which you rarely plug into your home network. This goal is actually achieved by setting the TimeToLive of all packets which go through their Gateway computer to 1, which effectively disrupts their ability to go beyond 1 routing machine. Thus you have to pay for the additional cable and unneeded IP. Well... no more.

Your kernel must be configured to support IP Masquerading (the whole netfilter thing,ip_conntrack, procfs and so on [see the official Linux IP Masquerading How-To]), be version 2.6 and up and you should use iptables v.1.3.6+ (at least this is the testing configuration).

Written by Emanuil Tolev, Bulgaria on 26.11.2006
The script basically normally enables IP Masquerading and then sets a rule to mangle all packets that go through it, effectively setting their TTL to 64. I know it's cruel, but if I use the '-m ttl --ttl-eq (or ttl-lt, respectively ttl-gr)' option of iptables it can't catch the packets. I couldn't find the reason for this, was nervous and a bit angry at my ISP and thus decided to hammer through all routedpackets >.< . Won't do much harm though, just some more longer-lived packets, no big deal.

Put this script in your startup sequence AFTER THE NETWORK INITIALIZATION!
(i.e. : 1. Give it executable properties 'chmod a+x ipmasq'
        2. cp ipmasq /usr/bin/
        3. cd /etc/rcS.d/
        4. ln -s /usr/bin/ipmasq S41ipmasq
        5. reboot )

NOTE: TAKE A LOOK AT THE SCRIPT AND CHANGE IPs AND INTERFACES WHERE APPROPRIATE! THIS SCRIPT IS NOT FOR COMPLETE BEGINNERS, WHO DON'T KNOW WHICH INTERFACE THEY ARE USING TO CONNECT TO THE INTERNET OR EVEN WORSE - DON'T KNOW WHAT iptables IS ;) !

---

