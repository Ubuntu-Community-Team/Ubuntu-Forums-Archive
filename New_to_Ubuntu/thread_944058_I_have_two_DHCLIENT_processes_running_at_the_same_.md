---
title: "I have two DHCLIENT processes running at the same time?"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Sarah L on 2008-10-10
```

:~$ ps ax | grep dhc
 4848 ?        Ss     0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
 5668 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 6073 ?        S<s    0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
 9278 pts/1    S+     0:00 grep dhc

```

Is this normal behavior?

```

:~$ cat /var/run/dhclient.wlan0.pid
6073

```

Interestingly...
```

:~$ sudo chkrootkit 
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/dhclient3[6073], /sbin/wpa_supplicant[4815], /sbin/dhclient3[4848])

```

---

### Post by Sarah L on 2008-10-11
bump

---

### Post by Sarah L on 2008-10-15
bump

---

