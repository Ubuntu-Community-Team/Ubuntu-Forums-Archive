---
title: "sudo unable to resolve host and can't edit hostnames"
date: 2019-04-26
forum: New to Ubuntu
---

### Post by sirbob77 on 2019-04-26
After rebooting my server to test if sambashare auto-mounting was working, upon restart, everything seemed to stop working. No docker containers started. I proceeded to try and manually start the docker-compose and that failed. sudo commands return:
```
sudo: unable to resolve host cbserver2: Resource temporarily unavailable
```

I've done some google-fu and checked my /etc/hosts
```
127.0.0.1       localhost.localdomain   localhost
::1             localhost6.localdomain6 localhost6


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

and /etc/hostname
```
cbserver2
```

I believe if I add the following to my /etc/hostname it should work:
```
127.0.1.1       cbserver2
```

But the odd thing is that I cannot save any of these files due to read-only and sudo isn't working to override that.
```
[ Error writing /etc/hosts: Read-only file system ]
```

So how can I fix this sudo resolve host issue if I can't use sudo and am unable to edit any files?

---

### Post by TheFu on 2019-04-26
Use the "recovery console" option at boot or boot from installation media and "Try Ubuntu", then mount the partition/LV where /etc is and modify the file.

I'd do this:

```
127.0.0.1      cbserver2  localhost.localdomain   localhost
```

---

### Post by sirbob77 on 2019-04-26
> **TheFu said:**
> Use the "recovery console" option at boot or boot from installation media and "Try Ubuntu", then mount the partition/LV where /etc is and modify the file.

I'd do this:

```
127.0.0.1      cbserver2  localhost.localdomain   localhost
```

This worked, thank you!

---

### Post by TheFu on 2019-04-26
Please use the Thread Tools button to mark this thread as "SOLVED", to help out the community.

---

