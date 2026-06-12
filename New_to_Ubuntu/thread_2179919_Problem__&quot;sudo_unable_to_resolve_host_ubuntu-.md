---
title: "Problem : &quot;sudo: unable to resolve host ubuntu-server&quot;"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by manfred2 on 2013-10-10
Hello everybody,

I got a problem with Sudo
everytime I use Sudo I got the following problem : "sudo: unable to resolve host ubuntu-server"
 
the /etc/hosts file  looks like this:
```
127.0.0.1       localhost
127.0.1.1       ubuntu-server

# The following lines are desirable for IPv6 capable hosts

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
FF02::2 ip6-allrouters 

```

What can I do to resolve this problem ?


i hope someone can help

grtz Manfred

---

### Post by plucky on 2013-10-10
From a terminal,what does ```
hostname
``` produce?

---

### Post by manfred2 on 2013-10-11
This produce :
```
ubuntu-server
```

---

### Post by manfred2 on 2013-10-12
hmm nobody who can help me ? :(

---

### Post by Iowan on 2013-10-12
One of my servers had a similar /etc/hosts file. I don't remember the reason, but I commented out the 127.0.1.1 line and replaced it with the static IP address.

---

### Post by steeldriver on 2013-10-12
Hmm... can you post these as well please?

```
ls -l /etc/nsswitch.conf
```

```
cat /etc/nsswitch.conf
```

Are you using any directory services like LDAP?

---

### Post by manfred2 on 2013-10-12
> **steeldriver said:**
> Hmm... can you post these as well please?

```
ls -l /etc/nsswitch.conf
```

```
-rw-r--r-- 1 root root 460 Oct  6 19:22 /etc/nsswitch.conf

```

> ```
cat /etc/nsswitch.conf
```

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.
passwd:         compat
group:          compat
shadow:         compat
hosts:  dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis


```

> Are you using any directory services like LDAP?

I think, no

---

### Post by steeldriver on 2013-10-12
Well your /etc/nsswitch definitely looks non-standard, in particular

```
hosts:  dns
```

tells the system to *only* use DNS, whereas the (default, afaik) config is to try files (i.e. /etc/hosts) first e.g. my 12.04 server has

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

I don't know enough about nsswitch to know why yours is different and I can't find what package supplies /etc/nsswitch.conf - what changes have you made / packages installed recently?

If this is just a personal PC (not a real server) then I'd probably suggest backing up the existing nsswitch.conf file and editing the hosts entry - you'll have to do this from recovery mode if you can't sudo.

EDIT: unless maybe it's a new 'feature' of dnsmasq that I don't know about?

---

### Post by manfred2 on 2013-10-12
Thnks for the answer, it solves my problem.


i have replaced :
```
Hosts:     dns
```

with :

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

after replacing my problem was solved

---

### Post by Jonathan Precise on 2013-10-12
Please mark this thread as solved by going to thread tools.

---

