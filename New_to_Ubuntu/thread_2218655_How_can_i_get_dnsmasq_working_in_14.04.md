---
title: "How can i get dnsmasq working in 14.04?"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by genejohnson55 on 2014-04-21
i consulted here: [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

there is no dnsmasq.conf file present in /etc on my brand new desktop install of 14.04.

using lsof, i can see dnsmasq is installed and listening on 127.0.1.1:53. but testing with dig clearly shows masq is not working.


How do I disable the DHCP function of dnsmasq? i only want to use the caching function.

---

### Post by sandyd on 2014-04-21
DNSMasq is managed by NetworkManager by default - as a result, DHCP is disabled by default.

does
```

dig @127.0.0.1 google.com
```
return anything?

---

### Post by genejohnson55 on 2014-04-21
> **sandyd said:**
> DNSMasq is managed by NetworkManager by default - as a result, DHCP is disabled by default.

does
```

dig @127.0.0.1 google.com
```
return anything?

no, server timed out. nothing reached.

do u hav a dnsmasq.conf file in /etc?

---

### Post by bab1 on 2014-04-21
> **genejohnson55 said:**
> no, server timed out. nothing reached.

do u hav a dnsmasq.conf file in /etc?

There is only a piece of the dnsmasq code being used.  All the settings are hard coded and managed by Network Manager.  There is no conf file for this at all.  It's either on or off.

This system was introduced in Ubuntu 12.04 and you can read about it [here]("https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/").  Look for the section with the title "Using dnsmasq as local resolver by default on desktop installations"

Read the latest release (14.04) notes too.  The IP address has been changed from 127.0.0.1 to 127.0.1.1.  I minor difference but I'm sure the devs had their reasons.

---

### Post by genejohnson55 on 2014-04-21
> **bab1 said:**
> There is only a piece of the dnsmasq code being used.  All the settings are hard coded and managed by Network Manager.  There is no conf file for this at all.  It's either on or off.

This system was introduced in Ubuntu 12.04 and you can read about it [here]("https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/").  Look for the section with the title "Using dnsmasq as local resolver by default on desktop installations"

Read the latest release (14.04) notes too.  The IP address has been changed from 127.0.0.1 to 127.0.1.1.  I minor difference but I'm sure the devs had their reasons.

I read the link u provided before i posted here. Also, I can see that the local address is 127.0.1.1 from the lsof output I posted about above.

Any ideas why dnsmasq is not working on an out of the box install of 14.04?

---

### Post by bab1 on 2014-04-21
> **genejohnson55 said:**
> I read the link u provided before i posted here. Also, I can see that the local address is 127.0.1.1 from the lsof output I posted about above.

Any ideas why dnsmasq is not working on an out of the box install of 14.04?

Which part?  DNS resolution or DHCP?  I doubt that DHCP is running on a default install.  DHCP is for the entire network, not just one workstation or laptop.

What makes you think you have a DNSmasq problem?

---

### Post by genejohnson55 on 2014-04-21
> **bab1 said:**
> Which part?  DNS resolution or DHCP?  I doubt that DHCP is running on a default install.  DHCP is for the entire network, not just one workstation or laptop.

What makes you think you have a DNSmasq problem?

ah, yes. my assumption is that dnsmasq would be shortening the lookup time of dns addresses once the domain has already been visited. many report lookup times of 0ms once the domain is visited. I do not see this. is my expectation wrong?

here's a site reporting 0ms lookup times. [http://www.webupd8.org/2009/12/faster-browsing-in-linux-with-local-dns.html](http://www.webupd8.org/2009/12/faster-browsing-in-linux-with-local-dns.html)

---

### Post by bab1 on 2014-04-21
> **genejohnson55 said:**
> ah, yes. my assumption is that dnsmasq would be shortening the lookup time of dns addresses once the domain has already been visited. many report lookup times of 0ms once the domain is visited. I do not see this. is my expectation wrong?

here's a site reporting 0ms lookup times. [http://www.webupd8.org/2009/12/faster-browsing-in-linux-with-local-dns.html](http://www.webupd8.org/2009/12/faster-browsing-in-linux-with-local-dns.html)

So we are chasing zephyrs now...  

The article you are referring to was written well before 2012 (e.g. December 09, 2009).  The reference is ***not*** to the stripped down version of DNSmasq that Network-Manager uses at all.  My guess is that the Network-Manager version of DNSmasq provides out of the box repeatability and stability rather than speed.  The aim is to make setup just work.

If you can resolve names then it's working fine.

---

### Post by genejohnson55 on 2014-04-21
> **bab1 said:**
> So we are chasing zephyrs now...  

The article you are referring to was written well before 2012 (e.g. December 09, 2009).  The reference is ***not*** to the stripped down version of DNSmasq that Network-Manager uses at all.  My guess is that the Network-Manager version of DNSmasq provides out of the box repeatability and stability rather than speed.  The aim is to make setup just work.

If you can resolve names then it's working fine.

thx, i appreciate the feedback. but i don't understand what it is doing listening on local host. if I disable dnsmasq by commenting it out then my lookups are just the same ms speed and everything works fine. so why have it running at all?

---

### Post by bab1 on 2014-04-21
> **genejohnson55 said:**
> thx, i appreciate the feedback. but i don't understand what it is doing listening on local host. if I disable dnsmasq by commenting it out then my lookups are just the same ms speed and everything works fine. so why have it running at all?

I think this is the cogent part of the article I referenced by [Stéphane Graber]("https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/").> 
*[COLOR="#0000FF"]This was done to better support split DNS for VPN users and to better handle DNS failures and fallbacks.[/COLOR]* [B][COLOR="#FF0000"]

This dnsmasq server i_*sn’t a caching server*_ for security reason to avoid risks related to local cache poisoning and users eavesdropping on other’s DNS queries on a multi-user system.[/COLOR][/B]

**The big advantage is that if you connect to a VPN, instead of having all your DNS traffic be routed through the VPN like in the past, you’ll instead only send DNS queries related to the subnet and domains announced by that VPN. **This is especially interesting for high latency VPN links where everything would be slowed down in the past.


If you want other than the default setup you will have to remove all of Network-Manager and roll your own configuration.  This means configuring the interfaces and resolvconf or resolv.conf (whichever you use) besides installing the full DNSmasq.

The real question is why do that for a few miliseconds of time you will never notice in real life?

---

### Post by genejohnson55 on 2014-04-21
.thx for explaining this. I did not and still do not fully understand the VPN references. this led to my confusion. 

is this saying that local-area network traffic won't go thru the VPN when dnsmasq is running? Isn't it a good thing for privacy/security to have the DNS lookups go thru the VPN? could you kindly explain "queries related to subnet and domains announced by that VPN."?


thx so much for helping explain this stuff and educate us how to understand.

edit: as I understand the reasoning behind this dnsmasq setup, it is for people who trust the LAN dns source. But if you are connecting to VPN on the road and know nothing (do not trust) the local dns server, then you should disable dnsmasq so that all lookups go to the VPN dns server. Do I understand this accurately?

---

### Post by bab1 on 2014-04-21
> **genejohnson55 said:**
> .thx for explaining this. I did not and still do not fully understand the VPN references. this led to my confusion. 

is this saying that local-area network traffic won't go thru the VPN when dnsmasq is running? Isn't it a good thing for privacy/security to have the DNS lookups go thru the VPN? could you kindly explain "queries related to subnet and domains announced by that VPN."?


thx so much for helping explain this stuff and educate us how to understand.

edit: as I understand the reasoning behind this dnsmasq setup, it is for people who trust the LAN dns source. But if you are connecting to VPN on the road and know nothing (do not trust) the local dns server, then you should disable dnsmasq so that all lookups go to the VPN dns server. Do I understand this accurately?
In a sense you have part of it right.  With Network-Manager controlled interfaces you have a choice of using DNSmasq or not.  You would not need to use the VPN encrypted tunnel for local "trusted" DNS lookups.  VPN encryption comes at a cost (CPU cycles).  If you don't need to use it or the link is very slow (high latency) then you should have a cheaper alternative.  You can have multiple configurations for multiple situations.

DNS lookups only resolve the IP address to FQDN (host.domain.tld).  What privacy is needed.  Secure DNS is a concern but not privacy.  You don't want mis-directed resolution to a malware site (DNS poisoning).

---

### Post by Tom_Bosmans on 2014-08-19
> **bab1 said:**
> There is only a piece of the dnsmasq code being used.  All the settings are hard coded and managed by Network Manager.  There is no conf file for this at all.  It's either on or off.



Not true .  In 12.04, indeed, you couldn't configure anything in the dnsmasq version managed by Networkmanager.  But that has changed since 12.10 .  

So you can find the configuration file for dnsmasq (managed by NetworkManager) here : /etc/NetworkManager/dnsmasq.d/

Enjoy.

---

### Post by egalua2 on 2014-09-10
@tom
I am in 14.04 and I have read in many places that it should be possible to configure dnsmasq  (managed by NetworkManager) as you said: for example, also in 
[https://wiki.archlinux.org/index.php/dnsmasq](https://wiki.archlinux.org/index.php/dnsmasq)

Now, what I want is to enable caching for my pc. According to this, I created a file "cache" containing 
```
$ cat /etc/NetworkManager/dnsmasq.d/cache 
cache-size=1000
```
then "sudo service network-manager restart".
Nevertheless, I get
```
$ ps ax | grep dns
11724 ?        S      0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
11913 pts/7    S+     0:00 grep --color=auto dns
```

so it seems that caching is not working.

My question is: is there a way to enable caching (and configure other options of dnsmasq) in 14.04 or is it blocked? 
According to [http://cweiske.de/tagebuch/networkmanager-dnsmasq.htm](http://cweiske.de/tagebuch/networkmanager-dnsmasq.htm) it looks like the dnsmasq managed by NM is blocked.

Another problem: if I want to activate a personal hotspot using the ap-hotspot script then the "standard" package dnsmasq is required, so I end up having two instances of dnsmasq: the one started by NM (which comes from the dnsmasq-base package) and the plain one. 
If I get it right, the standard dnsmasq package is necessary because the dnsmasq from dnsmasq-base is just a dns forwarding service and has no dhcpd service.
The question is: can this cause conflicts? 

The fact that the standard package is requested suggests me that it is not possible to configure the dnsmasq from dnsmasq-base as a dhcpd server (and, probably, it is not possible to configure it at all!)

TIA

---

### Post by yonsy-s-p on 2015-08-06
> **egalua2 said:**
> @tom
Now, what I want is to enable caching for my pc. According to this, I created a file "cache" containing 
```
$ cat /etc/NetworkManager/dnsmasq.d/cache 
cache-size=1000
```
then "sudo service network-manager restart".
Nevertheless, I get
```
$ ps ax | grep dns
11724 ?        S      0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
11913 pts/7    S+     0:00 grep --color=auto dns
```

so it seems that caching is not working.
TIA

In my config i have /etc/NetworkManager/dnsmasq.d/cache.conf (remember the extension .conf for any file here)
and after put the file, I do a kill sighup to dnsmasq ```
sudo kill -HUP `pidof dnsmasq`
``` with this, the dns caching works for me (the first dig mydomain.com will take a few milliseconds, the next try to the same domain, 0 milliseconds)

---

