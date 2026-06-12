---
title: "[SOLVED] Could not connect to host localhost (port XXXX)"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by editrix on 2008-06-22
It doesn't matter which port, I can't connect. Polipo, wwwoffle and CUPS all use web-type pages which I *should* be able to open in a browser but I can't. I always get the same message: "Could not connect to host localhost (port 8080) [or whichever number they use]"

I connect to the internet with an external hardware modem. I have an ethernet card which doesn't seem to affect the hardware modem. But could it be affecting this localhost thing?

My /etc/hosts looks like this:
> 
127.0.0.1 localhost
127.0.1.1 darren

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I notice that whether knetworkmanager says I'm online or offline, it doesn't interfere with the modem, but could it be blocking access to localhost?

If I try to ping localhost I get one line:
> PING localhost (127.0.0.1) 56(84) bytes of data.
and then it hangs.

I've been on Kubuntu for a while, but in this I'm an absolute beginner--although I've been doing quite a bit of research.

---

### Post by cariboo on 2008-06-22
To find out what port a service is running use nmap. Nmap is available in the repositories. the gui for nmap is nmapfe when you run it you should get an output something like this:

```
Interesting ports on localhost (127.0.0.1):
Not shown: 1707 closed ports
PORT     STATE SERVICE
80/tcp   open  http
139/tcp  open  netbios-ssn
389/tcp  open  ldap
443/tcp  open  https
445/tcp  open  microsoft-ds
631/tcp  open  ipp
5432/tcp open  postgres
```

You can find a list of common port numbers here:

[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

As an aside I just tried the Network-Tools on Ubuntu and got no results from using localhost.

Jim

---

### Post by Dedoimedo on 2008-06-22
Hi,

Two things:

1. Are you blocking the localhost in firewall, perhaps?

2. Please check the following file: /etc/nsswitch.conf. 
In this file, please look for the entry hosts: dns files or hosts: files dns.

Do you have an entry like that? And if so, what is the order of the two entries files and dns.

Please make sure files is written before dns --> hosts: files dns

The nsswitch.conf determines how the lookup order of different databases on the machine is performed. Hosts refers to name resolution.

So, you want to resolve the local files first, then the DNS service.

Dedoimedo

---

### Post by editrix on 2008-06-22
> **Dedoimedo said:**
> 
Two things:

1. Are you blocking the localhost in firewall, perhaps?

Hi thanks for replying. No firewall, unless Kubuntu installed something they didn't tell me about.

> 2. Please check the following file: /etc/nsswitch.conf. 

Well, here it is:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```
> 
Please make sure files is written before dns --> hosts: files dns

Looks like it is :confused:

> So, you want to resolve the local files first, then the DNS service.

Makes sense.

---

### Post by editrix on 2008-06-22
> **cariboo907 said:**
> To find out what port a service is running use nmap. Nmap is available in the repositories. the gui for nmap is nmapfe 

Thanks for the tip. I will download and install once I finish up here (can't walk and chew gum at the same time on dialup).

> As an aside I just tried the Network-Tools on Ubuntu and got no results from using localhost.

Would you happen to know the kde equivalent? Or at least explain what you mean by "tried it"? IOW, if I un-try it, I might get a system where I can install a printer and a web caching proxy.
> 
LATER: Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-06-22 19:02 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 0.047 seconds

sudo nmap -PN 127.0.0.1

> Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-06-22 19:17 EDT
getinterfaces: SIOCGIFCONF claims you have no network interfaces!

---

### Post by editrix on 2008-06-24
/etc/localhost was incorrect. The first line should have read:

127.0.0.1 localhost.localdomain localhost computername

So now I can connect to localhost, but about six other things seem to be broken, including Firefox and my clipboard tool. Sigh!

---

