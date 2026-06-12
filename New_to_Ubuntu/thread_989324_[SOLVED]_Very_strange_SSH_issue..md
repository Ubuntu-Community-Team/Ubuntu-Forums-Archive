---
title: "[SOLVED] Very strange SSH issue."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Maverick1712 on 2008-11-21
Hi all

I use SSH to go from my laptop to my desktop when doing any sort of coding. SSH works just fine when I use the IP address. I edited the hosts files yesterday so that they look like this:

laptop:
```
127.0.0.1	localhost
127.0.1.1	adam-laptop
127.168.2.6     adam-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

desktop:
```
127.0.0.1	localhost
127.0.1.1	adam-desktop
127.168.2.5     adam-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

The problem is, from the laptop when I try to ssh to the desktop using the hostname, this is what I get:

```
adam@adam-laptop:~$ ssh adam-desktop
adam@adam-desktop's password: 
Linux adam-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Fri Nov 21 14:06:34 2008 from adam-desktop
adam@adam-laptop:~$ 
```

As you can see, it prompts me for my desktop password, but then I am connected to the laptop (confirmed with an ls to show folder contents).

I have confirmed the IP addresses multiple times. Any help is appreciated

Cheers,
Adam

---

### Post by silverglade00 on 2008-11-21
I think it might be confused about your use of 127.168. addresses along with 127.0.1.1 addresses. Try using 192.168 instead of 127.168. 127.x.x.x are for loopback, which is the local machine.

---

### Post by Maverick1712 on 2008-11-21
Serious noob move on my part. Thanks a ton silverglade.

Cheers,
Adam

---

### Post by silverglade00 on 2008-11-21
No prob. If it helps, it took me 5 times reading through before I noticed anything wierd about the addresses. :)

---

