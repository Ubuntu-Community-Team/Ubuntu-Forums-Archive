---
title: "QT libraries changing location"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wgarcia on 2011-09-06
After upgrading from 11.04 to Ubuntu 11.10 Beta 1, I have noticed that most QT libraries have moved from "/usr/lib" to "/usr/lib/x86_64-linux-gnu/". This is causing that some programs that I'm compiling don't find their libraries any more. 

Anybody else noticed this or is it just my system (my upgrade had some rough edges but I finished it and everything else seems to be OK)?

In any case, can any kind soul with qt-sdk installed do a "ls /usr/lib/libQt*" and "ls /usr/lib/x64_86-linux-gnu/libQt*$ and tell me where most of the libQt* libraries end up sitting?

---

### Post by sumski on 2011-09-06
qt (among other packages) is now multiarch enabled

---

### Post by wgarcia on 2011-09-06
Thanks Sumski for the prompt response!

So should anything further be done so that old configurations find the libraries? Something that can be touched in "/etc/ld.so.conf.d" or similar?

---

### Post by dino99 on 2011-09-06
> **wgarcia said:**
> Thanks Sumski for the prompt response!

So should anything further be done so that old configurations find the libraries? Something that can be touched in "/etc/ld.so.conf.d" or similar?

you should get good answer from devs:

[https://answers.launchpad.net/ubuntu/+addquestion](https://answers.launchpad.net/ubuntu/+addquestion)

---

### Post by wgarcia on 2011-09-06
Thanks dino99, I'll ask and if I get an answer I'll post the results here.

---

