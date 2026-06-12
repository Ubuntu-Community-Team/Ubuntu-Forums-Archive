---
title: "Custom C Wireless Application"
date: 2007-04-22
forum: Programming Talk
---

### Post by GaryH on 2007-04-22
Hi Everybody,
I assume tools like iwlist and iwconfig use an API to read/write from/to the wireless stack or physical driver. Does anybody out there know where I can look to find out the details of how to install and use said API?
Much thanks in advance,
GaryH

---

### Post by ssam on 2007-04-22
there are a few programs that manage wifi that you might want to look at. You might be able to figure stuff out from their code, or modify them to do what you need.

network-manager
wifi-radar
kwifimanager

i think these days its best to use the wireless extensions rather than the wireless-utils.

---

### Post by amo-ej1 on 2007-04-23
The prototypes are defined in /usr/include/linux/wireless.h communication is mainly done using ioctl()'s.

in order to know what happend when using iwlist and iwconfig you might use strace e.g.

```

e@lape:/usr/include/linux$ sudo strace iwlist eth1 scan

<SNIP>

socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 3
ioctl(3, SIOCGIWRANGE, 0xbfa69428)      = 0
ioctl(3, SIOCSIWSCAN, 0xbfa699b0)       = 0
<SNIP>

```

---

### Post by GaryH on 2007-04-23
Thank you ssam and amo-ej1 for the very good suggestions! Might either of you know the source location for iwlist and iwconfig? I found neither a iwlist.c nor a iwconfig.c module in the linux tree.
Thanks in advance,
GaryH

---

### Post by amo-ej1 on 2007-04-24
they're userspace applications, not part of the kernel source. You can get their source by getting the source of the 'wireless tools package'

```

apt-get source wireless-tools

```

---

### Post by GaryH on 2007-04-24
> **amo-ej1 said:**
> they're userspace applications, not part of the kernel source. You can get their source by getting the source of the 'wireless tools package'

```

apt-get source wireless-tools

```

Sorry to be so slow amo-ej1 but I still can't find iwlist.c.

> gary@gary-laptop:~$ apt-get source wireless-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'wireless-tools_28-1ubuntu3.dsc'
Skipping already downloaded file 'wireless-tools_28.orig.tar.gz'
Skipping already downloaded file 'wireless-tools_28-1ubuntu3.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in wireless-tools-28
gary@gary-laptop:~$ whereis iwlist.c
iwlist: /sbin/iwlist /usr/share/man/man8/iwlist.8.gz
gary@gary-laptop:~$ 

What am I doing wrong?

Thanks in advance.
GaryH

---

### Post by amo-ej1 on 2007-04-24
whereis can't be used for that ;-)
```

edb@lapedb:~$ whatis whereis
whereis (1)          - locate the binary, source, and manual page files for a command

```
When readning man whereis it will show you that it only searches in a very limited subset of directories.

You should 've used find 

```

find . -name iwlist.c

```

---

### Post by GaryH on 2007-04-24
Thanks for your patience amo-ej1.:oops:

---

### Post by amo-ej1 on 2007-04-25
No problem ;-) everybody needs to learn ;)

---

