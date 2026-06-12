---
title: "File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.4.0-149-generic (deleted))"
date: 2023-07-12
forum: New to Ubuntu
---

### Post by maketopsite on 2023-07-12
```
#apt autoremove
...
Found memtest86+ image: /boot/memtest86+.bin
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.4.0-149-generic (deleted)) leaked on lvs invocation. Parent PID 107072: /bin
/sh
...
```

Ubuntu 20.04. Is there please some action needed ?

---

### Post by Xian on 2023-07-14
It requires no action. 
I've seen this occurrence reported as far back as 2006. 

One of those can be found here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1313784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1313784)

---

### Post by maketopsite on 2023-07-19
> **Xian said:**
> It requires no action. 
I've seen this occurrence reported as far back as 2006. 

One of those can be found here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1313784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1313784)

Thank you.

---

