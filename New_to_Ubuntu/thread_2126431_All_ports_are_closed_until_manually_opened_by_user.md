---
title: "All ports are closed until manually opened by user - is that correct?"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by regency on 2013-03-17
I am new to Linux and Ubuntu. I googled and read some articles stating that all ports are closed until they are opened manually by the user. Is it correct?

And what do you mean by "listening on a port" and "a port is established" in simple terms?

---

### Post by 3rdalbum on 2013-03-17
> **regency said:**
> I am new to Linux and Ubuntu. I googled and read some articles stating that all ports are closed until they are opened manually by the user. Is it correct?

And what do you mean by "listening on a port" and "a port is established" in simple terms?

On Ubuntu, when you boot it up, there are no programs listening for connections. If you open a program that listens, for instance Transmission or Apache Web Server, then anyone remotely can establish a connection to those programs.

What you are asking is "Does Ubuntu have a fully set-up firewall". By default Ubuntu has a firewall, but set to "allow all". This is not a security risk, as a remote computer can only connect to any programs that are listening for connections. And there are none that will do that in the default Ubuntu install unless you actually start them up or install them.

If incoming connections are being denied, either you don't have the necessary program running or you have a firewall in your modem.

---

### Post by haqking on 2013-03-17
On a default 12.10 intall for example then Ports 68/UDP, 5353/UDP and 631/TCP are listening.

from [https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

> 

  Default  installations of Ubuntu must have no listening network services after  initial install. **Exceptions to this rule include network infrastructure  services such as the DHCP client and mDNS (Avahi/ZeroConf**, see [ZeroConfPolicySpec]("https://wiki.ubuntu.com/ZeroConfPolicySpec")  for implementation details and justification). When installing Ubuntu  Server, the administrator can, of course, select specific services to  install beyond the defaults (e.g. Apache


And you can run a NMAP scan on your install to show it, Canonicals "no listening services" means that some are, bit like Microsofts UNC is not universal ;-)

If you are concerned with security you can read the daily security vulnerabilities here [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

But more accurately from somewhere like [http://www.exploit-db.com/](http://www.exploit-db.com/) or [https://cve.mitre.org/](https://cve.mitre.org/)

Peace

---

### Post by regency on 2013-03-18
> **haqking said:**
> Default installations of Ubuntu must have no listening network services after initial install. 


What sudo command should I issue to find out that my default installation of Ubuntu 12.10 has no listening network services?

---

### Post by regency on 2013-03-18
> **3rdalbum said:**
> By default Ubuntu has a firewall, but set to "allow all". This is not a security risk, as a remote computer can only connect to any programs that are listening for connections. And there are none that will do that in the default Ubuntu install unless you actually start them up or install them.

I plan on installing OpenVPN and route all network traffic through the VPN tunnel. Whenever the VPN disconnects, all network traffic to and from my computer should terminate immediately. How do I go about routing all network traffic through the VPN tunnel?

Any help would be most appreciated.

---

### Post by haqking on 2013-03-18
> **regency said:**
> What sudo command should I issue to find out that my default installation of Ubuntu 12.10 has no listening network services?

From the link that I posted from which that was quoted it explains to use the following:

```
netstat -an --inet | grep LISTEN | grep -v 127.0.0.1 
```

There are many variations on this command including tools such as NMAP.

LIke I said though canonical prefer to say there "no listening" and then add exceptions rather than clearly state there "are listening" ;-)

Peace

---

### Post by haqking on 2013-03-18
> **regency said:**
> I plan on installing OpenVPN and route all network traffic through the VPN tunnel. Whenever the VPN disconnects, all network traffic to and from my computer should terminate immediately. How do I go about routing all network traffic through the VPN tunnel?

Any help would be most appreciated.

as soon as you connect to a VPN all traffic will go through the VPN, that is the point.

as soon as you disconnect from the VPN then it will default to your standard connection.

---

### Post by regency on 2013-03-18
> **haqking said:**
> as soon as you disconnect from the VPN then it will default to your standard connection.

That is why when my computer disconnects from the VPN, all network connections should be killed. How do I do that on Ubuntu 12.10?

---

