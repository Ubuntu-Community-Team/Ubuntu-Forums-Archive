---
title: "DNS cache and ports"
date: 2023-01-13
forum: New to Ubuntu
---

### Post by a-k-i-r-a on 2023-01-13
Hello everyone o/

I just came from Windows to Ubuntu, sorry if the questions are silly but I've tried reading apropos/man and wasn't able to grasp some stuff.

1 - DNS cache - How do I now if Ubuntu is using the OS cache or the browser cache? How do I list both? (I could not achieve it with host, dig, ip or resolvectl)

2 - Ports - Basically I would like to achieve what netstat achieves on Windows but on Ubuntu, i.e. list all ports, their protocol and current stat (Maybe with nc? I also couldn't understand its man page)

---

### Post by TheFu on 2023-01-14
> **a-k-i-r-a said:**
> Hello everyone o/

I just came from Windows to Ubuntu, sorry if the questions are silly but I've tried reading apropos/man and wasn't able to grasp some stuff.

1 - DNS cache - How do I now if Ubuntu is using the OS cache or the browser cache? How do I list both? (I could not achieve it with host, dig, ip or resolvectl)

2 - Ports - Basically I would like to achieve what netstat achieves on Windows but on Ubuntu, i.e. list all ports, their protocol and current stat (Maybe with nc? I also couldn't understand its man page)

When posting questions, you need to say which release you are using and which DE to get the best answers.  The way that name resolution happens has drastically changed from 16.04 until today.  Or you might not be using any of the stuff that Canonical has decided average people need, because it seems to break far too often.

Tip: If you can't figure out what the options mean in a manpage, sometimes they are less than clear, google for "{command} examples" .... so "linux  netstat examples" would be the search I use.  I haven't seen Windows in a few years and nothing later than Win7, so I don't know what MSFT is inflicting on those poor users today.
netstat isn't the only method.  There's 'ss', 'nmap', 'lsof', 'nettop', and a number of monitoring tools that are probably too much hassle for typical end users to setup.  Some useful examples to try:
```
ss -lnt|egrep -v 127
netstat -tunl|grep LISTEN|grep -v 127
netstat -tulpn |grep LISTEN|grep -v 127
sudo lsof -Pni:53
```
Note that I only specify sudo when required.  I'm assuming you understand piping output and greping for stuff you'd like to see.  Run without the 'grep' part to see the full output so you know what to filter on (positive filter or negative filter).

DNS for the system is controlled by 1 file.  /etc/resolv.conf.  This file should have 2 nameserver lines and perhaps a search line.
The order that files, mdns, dns, nis, nis+, ldap are used to resolve hosts is specified in the /etc/nsswitch.conf file.  For Linux desktops, files, mdns, and DNS are expected.  For servers, files, dns, and ldap are common.  NIS used to be used in the 1990s, before security became more important.  NIS+ is used in some networks, but since the NIS+ server only runs on Solaris, fewer and fewer environments will have it.  NIS+ clients are available for nearly every OS.  Oracle wants their pay.  I miss NIS, but not the poor security. Sigh.

resolvconf was deprecated a few releases ago and a systemd-resolved was put in-place.  This subsystem fails all the time.  If you have a local DNS server, there is little need for either of these, since you want the local DNS to perform all the caching, not the workstation or server.  For example, lots of people run pi-hole DNS filters, which can also be a LAN DNS.  Or perhaps your router has a built-in DNS.  No need for your workstation to do caching if either of those systems does it, right?   I don't use either systemd-resolved or resolvconf. I find them complexities that just get in the way.  What did Scotty say?  > The more they overthink the plumbing, the easier it is to stop up the drain.  Sadly, that is true.

Perhaps someone with current Windows knowledge will respond with better answers. We can hope.

---

### Post by MAFoElffen on 2023-01-14
Either of these will flush the DNS Caches
```

sudo systemd-resolve --flush-caches
sudo systemctl restart systemd-resolved

```

---

### Post by a-k-i-r-a on 2023-01-14
Hmmmm, I guess ss is what I was looking for, thanks, I can start from there. My version does not have netstat by default, I'll check how to install if necessary.

Don't know what DE stands for, but lsb_release -a returns the following:

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy
```

About the file at /etc/resolv.conf, mine displays the following:

```
nameserver 127.0.0.53
options edns0 trust-ad
search .
```

127.0.0.0 / 8 is the network of the loopback localhost but not the same host/ip (127.0.0.1), currently I don't know from where 127.0.0.53 comes from.

resolvectl status returns only the ip of the DNS server (which is not my router) and the following protocols:

```
Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
```

but no information about the cache itself.

---

### Post by a-k-i-r-a on 2023-01-14
> **MAFoElffen said:**
> Either of these will flush the DNS Caches
```

sudo systemd-resolve --flush-caches
sudo systemctl restart systemd-resolved

```

Thanks, that's definitely helpful for troubleshooting and network issues, but my question was more directed on how to retrieve/manipulate the cache itself.

---

### Post by MAFoElffen on 2023-01-14
The closest I can seem to get on a default install that hasn't been tweaked is 

```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo systemctl status systemd-resolved

systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-01-10 07:30:18 PST; 4 days ago
       Docs: man:systemd-resolved.service(8)
             man:org.freedesktop.resolve1(5)
             https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers
             https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients
   Main PID: 938 (systemd-resolve)
     Status: "Processing requests..."
      Tasks: 1 (limit: 9304)
     Memory: 8.1M
        CPU: 1min 29.137s
     CGroup: /system.slice/systemd-resolved.service
             &#9492;&#9472;938 /lib/systemd/systemd-resolved

Jan 10 07:30:23 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client set DNS server list to: 75.75.75.75, 75.75.76.76
Jan 10 07:30:24 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client set DNS server list to: 75.75.75.75, 75.75.76.76, 2001:558:feed::1, 2001:558:feed::2
Jan 13 04:19:07 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client reset search domain list.
Jan 13 04:19:07 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client set default route setting: no
Jan 13 04:19:07 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client reset DNS server list.
Jan 13 08:20:43 Mikes-ThinkPad-T520 systemd-resolved[938]: Clock change detected. Flushing caches.
Jan 13 08:20:48 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client set search domain list to: hsd1.wa.comcast.net
Jan 13 08:20:48 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client set default route setting: yes
Jan 13 08:20:48 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client set DNS server list to: 75.75.75.75, 75.75.76.76
Jan 13 08:20:49 Mikes-ThinkPad-T520 systemd-resolved[938]: wlp3s0: Bus client set DNS server list to: 75.75.75.75, 75.75.76.76, 2001:558:feed::1, 2001:558:feed::2


```

---

### Post by TheFu on 2023-01-14
> **a-k-i-r-a said:**
> 
About the file at /etc/resolv.conf, mine displays the following:

```
nameserver 127.0.0.53
options edns0 trust-ad
search .
```


that's using the local system resolver ... systemd-resolved.  It is common on Unix systems to use any of the localhost address space to communicate between different processes.

> **a-k-i-r-a said:**
> 
127.0.0.0 / 8 is the network of the loopback localhost but not the same host/ip (127.0.0.1), currently I don't know from where 127.0.0.53 comes from.

That **is** all the localhost IPs.  All of them.  If you want to setup a daemon that is only available to other processes from the same system, any IP that starts with 127.x.x.x can be used.  They are all localhost.  If you use an ipcalc tool, you'll get this result:
```
$ ipcalc 127.0.0.1/8
Address:   127.0.0.1            01111111. 00000000.00000000.00000001
Netmask:   255.0.0.0 = 8        11111111. 00000000.00000000.00000000
Wildcard:  0.255.255.255        00000000. 11111111.11111111.11111111
=>
Network:   127.0.0.0/8          01111111. 00000000.00000000.00000000
HostMin:   127.0.0.1            01111111. 00000000.00000000.00000001
HostMax:   127.255.255.254      01111111. 11111111.11111111.11111110
Broadcast: 127.255.255.255      01111111. 11111111.11111111.11111111
Hosts/Net: 16777214              Class A, Loopback
```
Note the HostMin and HostMax values.  Thats a huge range, right?

> **a-k-i-r-a said:**
> 
resolvectl status returns only the ip of the DNS server (which is not my router) and the following protocols:

```
Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
```

but no information about the cache itself.

The manpage for 'resolvectl' has lots of options. A worthy read.

---

