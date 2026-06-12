---
title: "URLs blocked from hosts file still accessible"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by Dan Arbo on 2013-02-12
Hi all, I am using Xubuntu 11.10

I simply cannot understand why the sites blocked in the hosts file are still accessible. In my old laptop it was a very straightforward operation.

I know that the hosts file is being read, because localhosts and dan are both redirected to 127.0.0.1

Anyway, if I type the following in terminal

```
gedit /etc/hosts
```

The result is

```
127.0.0.1	localhost
127.0.0.1	dan
127.0.0.1		http://vast.adjug.com/
127.0.0.1		http://www.facebook.com/
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Any idea? Am I editing the wrong hosts file?
The only changes to the original hosts are the addition of the lines with the IPs, and I deleted some blank lines, before and after the IPV6 commented line, just to see if it would help.

Thank you very much for any tips :)

Dan

---

### Post by Cheesemill on 2013-02-12
You don't use the http prefix when editing the hosts file. Try this instead....
```
127.0.0.1    localhost
127.0.0.1    dan
127.0.0.1    vast.adjug.com
127.0.0.1    www.facebook.com
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

### Post by Dan Arbo on 2013-02-13
Thank you very much, the problem was the http:// bit, which I would never have spotted!

---

