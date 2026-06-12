---
title: "[SOLVED] .h file missing"
date: 2007-09-14
forum: Programming Talk
---

### Post by chongchongworks on 2007-09-14
Hi, yesterday I re-installed my Ubuntu for some reason, and run my programming assignment, but it noticfies the following message. I am sure I coded and run it in my previous system, but why it does not work this time, do i miss anything. As I know , both linux and unix shoud have those libraries, thanks.

client.c:3:23: error: sys/types.h: No such file or directory
client.c:4:24: error: sys/socket.h: No such file or directory
client.c:5:24: error: netinet/in.h: No such file or directory
client.c:6:23: error: arpa/inet.h: No such file or directory
client.c:7:20: error: string.h: No such file or directory
client.c:8:19: error: stdio.h: No such file or directory
client.c:9:20: error: stdlib.h: No such file or directory
client.c:10:22: error: sys/stat.h: No such file or directory
client.c:11:19: error: fcntl.h: No such file or directory
client.c:12:21: error: pthread.h: No such file or directory
client.c:26: error: field ‘addr’ has incomplete type

---

### Post by Soybean on 2007-09-14
You may need to install "build-essential".

Either find it in Synaptic, or do the following in a terminal:
```
sudo aptitude install build-essential
```

I don't know if that'll cover everything, but it should help. :)

---

### Post by chongchongworks on 2007-09-15
Thanks a lot.

It solved, but just for curiousness, why did I miss those packages when I installed Ubuntu? Are they not the default packages should be installed?

---

### Post by aks44 on 2007-09-15
> **chongchongworks said:**
> Are they not the default packages should be installed?

No, that's not part of the default packages.

The average Joe will never use programming tools, so why clutter his computer with useless stuff, when programmers are expected to be able to figure out how to correctly configure their working environment?

The fact is, you didn't know *why* you had those errors, but anyway you managed to find the adequate solution (ie. coming here for help)... so I guess that the assumption above is quite correct. :)

---

