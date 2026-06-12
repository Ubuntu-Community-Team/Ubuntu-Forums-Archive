---
title: "Create an ISO from /dev/scd0 using command line?"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by honeybear on 2012-03-15
Hello,

I would like to know what can be the recent command to create an ISO from a cdrom at the location /dev/scd0 using command line?

thank you

---

### Post by VH-BIL on 2012-03-15
Use dd:
```
dd if=/dev/scd0 of=~/Desktop/MyIsoFile.iso
```

if=<device>
of=<file to save>

---

### Post by Kevin McCready on 2012-03-15
what sort of iso will this create? all packages installed? configuration settings?

---

### Post by chipbuster on 2012-03-15
dd basically copies over data 1 to 1. Whaveter was on the input device will be copied over verbatim.

---

### Post by VH-BIL on 2012-03-15
> **Kevin McCready said:**
> what sort of iso will this create? all packages installed? configuration settings?

I have used dd to backup CD and DVD media and have been able to mount it in Linux using mount. I usually backup purchased CD and DVD media like X-Plane and mount it when I want to install it.

---

### Post by yetiman64 on 2012-03-15
The dd command VH-BIL gave would be my first pick for command line cd/dvd replicating. 

Another option is the cat command,

```
cat /dev/scd0 > ~/Desktop/MyIsoFile.iso
```

---

### Post by honeybear on 2012-03-15
Thank you !!!!

---

