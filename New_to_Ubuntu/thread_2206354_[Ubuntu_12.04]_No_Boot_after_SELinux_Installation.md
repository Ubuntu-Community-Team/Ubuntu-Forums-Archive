---
title: "[Ubuntu 12.04] No Boot after SELinux Installation"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by david157 on 2014-02-18
Hi guys,

Like a lot of people I am discovering Linux with Ubuntu. I use the version 12.04 and I wanted to install SELinux.

I installed it :
```

sudo apt-get install selinux
```

Then, impossible to boot. I quickly have a look at the system logs at /var/log/ to see what happened, here is the blocking line :
```

cat syslog | grep SELinux

kernel: [   40.840869] SELinux:  Context system_u:object_r:ntpdate_exec_t:s0 is not valid (left unmapped).

```

After this line, I can't see anything so I suppose this is what prevents my computer from booting properly (no X, just accessible in command line).
Any ideas please ?

Thanks in advance ! :P

---

### Post by david157 on 2014-02-21
Nobody ? No ideas ? :(

---

### Post by Vladlenin5000 on 2014-02-21
Hi, welcome.

1. Read the note here [https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)
2. Apparently the now recommend packages/installation is the same as Debian's: [https://wiki.debian.org/SELinux/Setup](https://wiki.debian.org/SELinux/Setup) 
3. Try uninstalling & reboot

You can try the procedure mentioned in #2 if you succeeded in reverting the changes.

---

### Post by david157 on 2014-02-25
Thanks Vladlenin5000, I'll have a look :)

---

