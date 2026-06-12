---
title: "Help"
date: 2024-10-20
forum: New to Ubuntu
---

### Post by ubuyo on 2024-10-20
I'm doing a new Ubuntu install and am getting an error 'temporary failure resolving us.archive.ubuntu.com'.

I noticed I sometimes can't even ping Ubuntu.com. I'm using 8.8.8.8 dns

185.125.190.20 <- can't ping

185.125.190.29 <- can ping

can anyone here ping that .20 ip?

---

### Post by ian-weisser on 2024-10-20
Nothing wrong with that domain.
Curious why you picked that IP address, which is indeed unavailable at this particular moment.

```

$ ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.91.81) 56(84) bytes of data.
64 bytes from ubuntu-mirror-1.ps6.canonical.com (91.189.91.81): icmp_seq=1 ttl=49 time=300 ms
64 bytes from ubuntu-mirror-1.ps6.canonical.com (91.189.91.81): icmp_seq=2 ttl=49 time=224 ms
64 bytes from ubuntu-mirror-1.ps6.canonical.com (91.189.91.81): icmp_seq=3 ttl=49 time=167 ms
64 bytes from ubuntu-mirror-1.ps6.canonical.com (91.189.91.81): icmp_seq=4 ttl=49 time=121 ms
64 bytes from ubuntu-mirror-1.ps6.canonical.com (91.189.91.81): icmp_seq=5 ttl=49 time=129 ms
64 bytes from ubuntu-mirror-1.ps6.canonical.com (91.189.91.81): icmp_seq=6 ttl=49 time=82.3 ms
64 bytes from ubuntu-mirror-1.ps6.canonical.com (91.189.91.81): icmp_seq=7 ttl=49 time=339 ms
^C
--- us.archive.ubuntu.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6004ms
rtt min/avg/max/mdev = 82.282/194.635/338.807/89.277 ms

```

---

### Post by ubuyo on 2024-10-20
I'm confused why I can't ping ubuntu.com same with .21. I figured it was related to my new install problems but maybe the problem is on my end. I performed the same install 2 weeks ago on a different machine and never ran into these issues.

---

