---
title: "Space required"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by Sunfist on 2011-10-02
I was wondering how much HD space I would need for a full install of Ubuntu 11.04 I looked on the website but didn't really see any kind of system requirements.

---

### Post by TeoBigusGeekus on 2011-10-02
You should be fine with ~10gb.

---

### Post by peter d on 2011-10-02
Generally, I think, a minimum of about 4GB. Allow about 10GB for the system.

---

### Post by mibart on 2011-10-02
On my computer, Ubuntu 10.04 took over 4GB. Installed "as is" from Desktop Live CD, updated and filled with some software development tools (Java SDK, Eclipse etc.) and non-free mutimedia support (all stuff avaliable from medibuntu.org).
```

mikolaj@desktop32:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              30G  4.3G   24G  16% /
none                  2.0G  664K  2.0G   1% /dev
none                  2.0G  116K  2.0G   1% /dev/shm
none                  2.0G   92K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda3             425G  304M  404G   1% /home

```By the way: You can always check Your current hard disk usage by typing df -h (df means disk free, -h is from "huma readable").

---

### Post by Blasphemist on 2011-10-02
As described above it will require 4-5GB as installed. From there add a couple more for what you install. That is the minimum. From there add space for any pictures, music, documents, downloads, etc. You should also have a swap partition a bit larger than the amount of memory that you have. So together, 10GB or so minimum. Plan at least twice that unless you are real pressed for space.

---

