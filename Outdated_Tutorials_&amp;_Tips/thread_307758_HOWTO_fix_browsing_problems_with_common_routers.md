---
title: "HOWTO: fix browsing problems with common routers"
date: 2006-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by stream303 on 2006-11-27
A quick summary on how to fix the most common dns issues when using **dhcp** behind an inexpensive router and why editing **/etc/resolv.conf** manually _doesn't work for very long_:

When manually adding a nameserver to /etc/resolv.conf, it is only a *temporary* solution since **dhclient** (actually dhclient-script) **overwrites this file on re-lease or reboot**. This only happens when using dhcp. Thus manually editing resolv.conf might only be useful during a "live-cd" session or when you are running a static ip.

Various tricks like changing the permissions of resolv.conf eventually fail because dhclient runs as root and overwrites it. Other tricks like making the file immutable (using chattr) are also not recommended.

Of course one could always run static where nothing overwrites resolv.conf, but the following is what I recommend for the anyone behind an inexpensive router running dhcp when they only see their router's dns server (actually a dns forwarder masquerading as a dns server in many cases) in resolv.conf.  Typically this is a private-ip address such as 172.16.0.254 etc.

**Option 1**: place your **isp's** primary and backup dns server addresses in the router setup page.

**Option 2**: Uncomment and edit (as root, ie sudo nano) the PREPEND line of **/etc/dhcp3/dhclient.conf** and place your isp's dns nameserver(s) there. In the case of multiple nameservers, be sure to separate them with a comma, and end the line with a semicolon;

**Option 3**: Edit (as root) dhclient-script and remove all the commands in the mk_resolv.conf{} function so your edited resolv.conf won't be overwritten. Not recommended as option 1 or 2 usually suffices and many of us (myself included) can mess up the edit.

After applying one of these fixes, you should bring your interface down and up again, or maybe the easiest is to just reboot.

example:
```
sudo ifdown eth0
sudo ifup eth0
```

**IPV6** - even after all this, sometimes our inexpensive hardware may have trouble with IPV6. Normally I don't recommend disabling it, but if you feel you should, you can disable it globally by creating a file titled "**bad_list**" in **/etc/modprobe.d** directory. bad_list can contain just this line:

**alias net-pf-10 off**

**UPDATE:** the above technique used to work, but now thanks to dbott67, the following is what works to disable ipv6 on my system:

```
sudo -s
echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6
exit
```

You can test to see if IPV6 has been disabled by running

```
ip a | grep inet6
```

If there is no output from this command, (after you have cycled your interface, or rebooted) you are good to go.  Lately I just run ifconfig and see if any inet6 addresses show up on my interface after rebooting.  Not elegant I know...

You can also **disable IPV6 in Firefox** by entering

about:config

in the url bar. Once the configurations are found, in the filter bar, search for IPV6. Once found, doubleclick the search result to change the boolean value from false to true. Restart Firefox.

Tip: When you purchase a router, make sure to check the router configuration to be sure it doesn't have the same ip address as your modem.

Hope this helps...

---

### Post by YumaJim on 2006-12-07
I have found that some routers and some WiFi Hot spots when connecting leave
the Ubuntu routing table empty. Looking at the end of the dmesg data one sees
that no IPV6 routes are defined. This seems strange since an IP address was assigned
to my connection. This seems to verify that the dhcp code is overwriting the route
data or is never writing the route data. Either way it is messed up!

The way I fixed the problem was to do the following:

```
sudo route add default gw dev wlan0
```

This tells the system to send the internet commands through the WiFi device, in my case 'wanl0'.
I added the above command to a bash script that I use to connect to the Internet. I saw in one
of the other threads that 'wifi-radar' worked. I'll gave it a try.

YumaJim

---

### Post by YumaJim on 2006-12-11
> **YumaJim said:**
> I have found that some routers and some WiFi Hot spots when connecting leave
the Ubuntu routing table empty. Looking at the end of the dmesg data one sees
that no IPV6 routes are defined. This seems strange since an IP address was assigned
to my connection. This seems to verify that the dhcp code is overwriting the route
data or is never writing the route data. Either way it is messed up!

The way I fixed the problem was to do the following:

```
sudo route add default gw dev wlan0
```

This tells the system to send the internet commands through the WiFi device, in my case 'wanl0'.
I added the above command to a bash script that I use to connect to the Internet. I saw in one
of the other threads that 'wifi-radar' worked. I'll gave it a try.

YumaJim

I installed 'wifi-radar' and it works. All the other wifi 
managers need to operate like wifi-radar. It fills in the router table correctly.
YumaJim

---

### Post by tnjed111 on 2006-12-19
Hi,
I have the problem where I can connect to my wireless network and go to my router's configuration page, but I can't access the internet.  Ping also does not work to any site on the internet. If I use a wired connection, I can access the internet just fine.

I tried: 

sudo route add default gw dev eth1

and got this:

dev: Unknown host

My wireless interface is eth1 not wlan0. Is there anything else I have to change based on what the names of things are in my setup?

Also, I was going to try the how-to in this thread, but how to I find out the primary and backup name servers of my isp? I have just switched from Windows to linux and I never had to worry about the nameservers before.

---

### Post by YumaJim on 2007-01-08
You should be able to find your isp's dns addresses on another computer connected
to you isp or on the isp's wed site. They should have setup information some place on their site.

When you run command: ifconfig
Does it show your wi-fi device as eth1?
Seems strange that when tring to add the default gw to the routing table that 'eth1'
is UNKOWN.

YumaJim

---

### Post by tnjed111 on 2007-01-16
> **YumaJim said:**
> You should be able to find your isp's dns addresses on another computer connected
to you isp or on the isp's wed site. They should have setup information some place on their site.

When you run command: ifconfig
Does it show your wi-fi device as eth1?
Seems strange that when tring to add the default gw to the routing table that 'eth1'
is UNKOWN.

YumaJim

Thanks for your reply. I actually got my wan to work for a while by entering the DNS servers in my router's configuration page. Now, however, it has stopped working for some reason. I can still connect to lan and my router's config page. But I have no internet. Yes, ifconfig says eth1 is my wi-fi device, but route tells me  	

dev: Unknown host 

when I do 

sudo route add default gw dev eth1. 

I tried wi-fi radar, too, but It doesn't let me do anything. It lists the wireless networks in range but doesn't give me any option to do anything. (It says I am connected to my network actually, but when I push "disconnect" it doesn't do anything).

Before when I was troubleshooting I edited my /etc/network/interfaces file to say:
iface eth1 inet dhcp
wireless-essid cougar[name of my network]
wireless-key s: [I have no security]

Do you think that might be the problem?

---

### Post by sonnenenergie on 2010-09-01
Thank you very much for your information!! It is really very useful[IMG]http://sunrent.de/smileyhappy.ico[/IMG].........

---

