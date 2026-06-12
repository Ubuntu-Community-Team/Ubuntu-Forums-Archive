---
title: "Ethernet Not Working"
date: 2018-09-02
forum: New to Ubuntu
---

### Post by jt2k on 2018-09-02
I have Ubuntu Server and the Ethernet randomly stopped working.
I don't know what commands I need to run to be able to fix the problem.
I tried the /etc/networking/interfaces... But it says I need to install "ifupdown"....But I can't install it if I don't have internet. HELP

---

### Post by TheFu on 2018-09-03
Welcome to the forums.

Which Ubuntu release?  Networking has changed drastically with recent releases.
Running these commands should tell us some stuff:
```

$ sudo lshw -C network
$ ip addr
$ route -n
$ ping 8.8.8.8
```

Please post the output here using **code tags**. Use "adv reply" and the # to do that. The post should like like mine.

Often, things that appear to be a network failure are just a DNS failure.

---

### Post by NM5TF on 2018-09-03
@jt2k....FYI

in case you don't know....to stop the ping command from running forever, key in CTL+C after it runs 2-4 times...that will get plenty of data
to be sure it is working....it should look something like this...

```
[tommy@tommy ~]$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=121 time=50.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=121 time=50.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=121 time=50.8 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 6ms
rtt min/avg/max/mdev = 50.503/50.730/50.891/0.165 ms

```

tommy

---

