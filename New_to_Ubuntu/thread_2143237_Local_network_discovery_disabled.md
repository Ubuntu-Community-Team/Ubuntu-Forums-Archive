---
title: "Local network discovery disabled"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by raequin on 2013-05-08
We recently canceled our home internet service.  We have a network drive (WD My Book Live) and a wi-fi printer, so I'm keeping the router on.  This worked fine after the internet service was shut off, until we disconnected the modem.  Now on startup I get an error (running 12.04, by the way) that says

"Network service discovery disabled
Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery.  The service has been disabled."

Is there an alternative to Avahi that might work?  The router is an Asus RT-N66U.  Maybe there's a way to change the domain name on there?  Thanks.

---

### Post by steeldriver on 2013-05-08
There are a few recent threads about this - you can try specifying different DNS servers, if that is not possible (or doesn't work) then someone else suggested modifying /etc/avahi/avahi-daemon.conf to use a different domain-name value (I haven't tried this, but it sounds like it should work)

---

### Post by grahammechanical on 2013-05-08
I get that when the computer connects to the router before the router has established the link to my ISP. I never worry about it. You can enter the router set up program. You do this by directing a web browser to the router's IP address 

This will give a download of a user guide that may give you accurate information

[http://uk.asus.com/Networks/Wireless_Routers/RTN66U/#download](http://uk.asus.com/Networks/Wireless_Routers/RTN66U/#download)

By the way Avahi will be very useful in the situation that you have of a home network. > [COLOR=#333333][FONT=Ubuntu]Avahi is a fully LGPL framework for Multicast DNS Service Discovery. It allows programs to publish and discover services and hosts running on a local network with no specific configuration. For example you can plug into a network and instantly find printers to print to, files to look at and people to talk to.[/FONT][/COLOR]

Regards.

---

### Post by raequin on 2013-05-08
Thanks for your input.

> you can try specifying different DNS servers

Do you mean on the router?  The only thing on the router that I could find was to set the DHCP domain name.  I changed that, but got the same message from Avahi.

> ... someone else suggested modifying /etc/avahi/avahi-daemon.conf to use a different domain-name value

I do not know how to do this.  The server field in that file says "local".

I edited /etc/default/avahi-daemon, changing 1 in the following to 0.  I guess that just sets Avahi to not even try to scan a .local domain, though.

> # 1 = Try to detect unicast dns servers that serve .local and disable avahi in
# that case, 0 = Don't try to detect .local unicast dns servers, can cause
# troubles on misconfigured networks
AVAHI_DAEMON_DETECT_LOCAL=1

The problem is, that now that the daemon is disabling Avahi, I cannot mount the Windows Network drive (cannot get the shares list from the server).  Since I have not heard of anything other than Avahi for this DNS-SD process (what about Bonjour on this computer?), do you know of any way to A) make my domain something other than ".local" or B) get Avahi to work with a .local domain?

---

### Post by steeldriver on 2013-05-08
I *think* the idea is that you change the value of the actual domain-name parameter in /etc/avahi/avahi-daemon.conf, basically changing

```

[server]
#host-name=foo
[B][COLOR=#ff0000]#[/COLOR]domain-name=[COLOR=#ff0000]local[/COLOR]
[/B]#browse-domains=0pointer.de, zeroconf.org
use-ipv4=yes
use-ipv6=yes

```
to
```

[server]
#host-name=foo
[B][COLOR=#0000ff]domain-name=alocal[/COLOR]
[/B]#browse-domains=0pointer.de, zeroconf.org
use-ipv4=yes
use-ipv6=yes

```

and then restarting the avahi service

```
sudo service avahi-daemon restart
```
However I just tried it and it seems to just break my Avahi / mDNS resolution completely (although I *was* able to make it work if I changed it to a .local *subdomain *i.e. [FONT=courier new]domain-name=kitchen.local[/FONT] - unfortunately that won't help you)

---

### Post by raequin on 2013-05-09
I don't know exactly what Avahi does.  Could I get by without it if I know the ip address of my NAS drive and of the printer?

---

### Post by Morbius1 on 2013-05-09
Avahi ( aka zerconf, bonjour, etc.. ) allows hosts find each other by specifying a .local at the end of the host name as in hotsname.local without the benefit of a LAN side DNS server or some other mechanism ( like netbios name broadcasts ). Everyone who is enabled with this feature will respond to queries for that address. All apple products ( bonjour ) depend on it to find each other so it seems odd that a router would disable it.

Can you access the NAS by ip address? Yes. Just make sure it has a static ip address.

BTW, I was looking at the simulator for your router: [http://event.asus.com/2012/nw/dummy_ui/EN/Advanced_WAdvanced_Content.html](http://event.asus.com/2012/nw/dummy_ui/EN/Advanced_WAdvanced_Content.html)

You might want to toggle the "Wireless Multicast Forwarding" setting and see if that resolves the avahi issue. It's not clear what they mean by "multicast" in this situation - local lan or global - so I'm not sure if it should be enabled or disabled.

---

### Post by steeldriver on 2013-05-09
Yes IP addresses should work fine, or you can add the IP addresses and hostnames of each device into the hosts file (/etc/hosts) on each machine that needs to know them

---

### Post by raequin on 2013-05-09
> Yes IP addresses should work fine, or you can add the IP addresses and hostnames of each device into the hosts file (/etc/hosts) on each machine that needs to know them

I don't understand the "or" in that response.

For the hosts file, you're saying I could just add the (static) IP addresses of the NAS and the printer and things could then work?

Thanks.

---

### Post by steeldriver on 2013-05-09
I meant you can EITHER use the numeric IP address anytime you need to address a device, OR add the IP addresses --> name translations into your /etc/hosts files in which case you will be able to refer to the hosts by their unqualified names in the absence of any DNS / mDNS (Avahi) service e.g.

```

steeldriver@lap-t61p:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    lap-t61p

[COLOR=#0000ff][B]# added local hosts IPv4 lookups so I can accesss them without DNS or mDNS/Avahi
192.168.1.65    htpc-01
[/B][/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
steeldriver@lap-t61p:~$ 

```
Then I can just do
```

steeldriver@lap-t61p:~$ ping -q -c1 **[COLOR=#0000ff]htpc-01[/COLOR]**
PING **[COLOR=#0000ff]htpc-01 (192.168.1.65)[/COLOR]** 56(84) bytes of data.

--- htpc-01 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 7.459/7.459/7.459/0.000 ms

```

---

### Post by raequin on 2013-05-12
Well, I do not really know how to take advantage of that edit to /etc/hosts.  Fortunately, though, Nautilus "smb://192.168.1.250/Public" lets me access the Shares folders.  The printer I assigned an IP based on its mac ID.  I guess that was necessary?  I also went into the printer and manually set up the network (gateway, etc.) rather than letting DHCP or something else do it automatically.  It was a couple days ago, so not too clear anymore.  It works now and so does the NAS, therefore I'll mark this solved.  Thanks to all for the input.

---

