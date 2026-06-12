---
title: "I can't connect my ubuntu via windows remote"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by neolestro on 2015-06-12
Hello,

i'm quite newbie.

Firstly, i tried to read almost all threads about my issue and tried all commands but didn't figure out why my problem still exist.

i'll give all information about my steps and info..

i have vps which has Ubuntu 14.04 32bit. i totally installed my "xrdp" without any error(via putty with full root control) and also installed "LDXE Desktop Interface"

i have one more vps which has same OS on different server. I'm able to connect on it. So i mean, i have no issue about "port" thing.

But this one totally messed up for me..

my host file;

```

ff02::1         ip6-allnodes
ff02::2         ip6-allrouters

127.0.1.1 neolestro
127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
2a02:4780:1:1::1:108a neolestro
::1             localhost ip6-localhost ip6-loopback


```

my hostname file;

```
neolestro
```

my resolve.conf; (actually it was empty, i added myself)

```
nameserver 10.222.1.151
```

my ```
hostname -I
``` result;

```
127.0.0.2 
10.222.1.151 
2a02:4780:1:1::1:108a

```

and  maybe i can't add correct ip so this is from my hosting service information;

```
ssh root@31.220.49.11 -p 2215
Your VPS details:
                    **IP:** 2a02:4780:1:1::1:108a
```


I definately doing something wrong but i lack of knowledge. Can you help me to fix this? Don't hesitate to ask for more information. i'll be online on this forum until find a fix this. So it's not just a drop by question. Thanks

---

### Post by cariboo on 2015-06-18
How are you trying to connect to the second vps? Via ip address, I don't see anything in your /etc/hosts file about either of them,

---

