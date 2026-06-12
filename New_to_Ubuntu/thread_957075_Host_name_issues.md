---
title: "Host name issues"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Tpolich on 2008-10-23
I recently changed the host name on my ubuntu server and now I can't use the local ip (192.168.5.159) for cups printing. It auto changes it to the Tpolich.homelinux.org when I hit get queue in gnome printing.

/etc/hostname
```
Tpolich.homelinux.org
```

/etc/hosts
```
127.0.0.1	localhost
192.168.5.159	Tpolich.homelinux.org

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


Is there anyway to change it so I could still use the local but have the host name still be 'Tpolich.homelinux.org'?

---

