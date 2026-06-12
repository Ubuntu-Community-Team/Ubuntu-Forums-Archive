---
title: "Ubuntu Epic Fail"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by sdfdsfsfsf on 2012-08-21
Hello,

Just did a brand new install of Ubuntu 10.04 and right out of the box DNS is broken for SSH, for Firefox, etc. 

And know this isn't because of /etc/resolv.conf being overwritten by "Network Manager"

Basically 'nslookup' and host and so forth will work find and do DNS lookups, but nothing else will: Chrome, Firefox, ping, telnet, ssh, whatever you name it, no DNS.

----------

] nslookup sys2.dev.boats.local
Server:		192.168.12.13
Address:	192.168.12.13#53

Non-authoritative answer:
Name:	sys2.dev.boats.local
Address: 192.168.13.167                 <<<< Ah look, DNS

[[17] Tue Aug 21 13:33:02 tnewman@tnewman-laptop.:~ ]
] ping sys2.dev.boats.local
ping: unknown host sys2.dev.boats.local

----------

As you can see, DNS resolves just fine. Then it says Oh unknown host 2 seconds later. There is no connectivity problem, I just can't use DNS, period. 

Perhaps the Ubuntu team hasn't heard of DNS but rather a lot of people use it. Better luck next time??

---

### Post by papibe on 2012-08-21
Hi sdfdsfsfsf. Welcome to the forums.

That looks like a conflict between .local domain used on avahi-daemon (zero configuration networking).

Stop the service, and try again:
```
sudo service avahi-daemon stop
```
Let us know how it goes so we can help you uninstall the service.
Regards.

---

### Post by sdfdsfsfsf on 2012-08-21
> **papibe said:**
> Hi sdfdsfsfsf. Welcome to the forums.

That looks like a conflict between .local domain used on avahi-daemon (zero configuration networking).

Stop the service, and try again:
```
sudo service avahi-daemon stop
```
Let us know how it goes so we can help you uninstall the service.
Regards.

Hi there yep that was it, I've deleted every trace of "avahi" now (it won't uninstall easily will it?) 

Out of curiosity what is the method to diagnose this: Nslookup/dig/etc/ works but *everything* else says it can't resolve, ah it must avahi...?

---

### Post by papibe on 2012-08-21
To uninstall avahi-daemon is pretty simple:
```
sudo apt-get remove avahi-daemon
```
The rules for resolving names are stored in the file:
```
/etc/nsswitch.conf
```
The line that starts with 'hosts:' hold the rules.

Note that using specific programs like 'nslookup' won't follow those rules, since nslookup, in particular, uses directly DNS.

Regards.

---

