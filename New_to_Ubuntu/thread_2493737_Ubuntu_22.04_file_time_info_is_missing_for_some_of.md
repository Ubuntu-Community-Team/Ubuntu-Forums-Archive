---
title: "Ubuntu 22.04: file time info is missing for some of them"
date: 2023-12-23
forum: New to Ubuntu
---

### Post by maketopsite on 2023-12-23
```
ls -lt /var/log/ 
total 8628
[B]-rw-r-----  1 root              adm               97601 Dec  23  2023 dmesg
-rw-------  1 root              root               2164 Dec  23  2023 boot.log
drwxr-x---  2 mysql             adm                4096 Dec  23  2023 mysql
-rw-------  1 root              root              39013 Dec  23  2023 boot.log.1
drwxr-xr-x  2 root              root               4096 Dec  23  2023 atop
-rw-r--r--  1 root              root               2275 Dec  23  2023 gpu-manager.log[/B]
-rw-r-----  1 syslog            adm              305734 Dec  23 09:13 kern.log
-rw-r-----  1 syslog            adm             1844481 Dec  23 09:13 syslog
-rw-r-----  1 syslog            adm               44518 Dec  23 09:13 ufw.log
-rw-r-----  1 syslog            adm               13712 Dec  23 09:09 auth.log
-rw-rw-r--  1 root              utmp              29952 Dec  23 08:55 wtmp
-rw-r--r--  1 root              root              56526 Dec  23 08:54 ubuntu-advantage.log
-rw-r--r--  1 root              root               2282 Dec  23 08:53 gpu-manager-switch.log
-rw-r--r--  1 root              root             112342 Dec  22 21:55 dpkg.log
```

Anyone know please why ?

---

### Post by MAFoElffen on 2023-12-23
From an installer LiveUSB (so that the partitions are not mounted), do an fsck on the partition's filesystems...

I would say that it is highly suspect that there is a filesystem problem with that results.

---

### Post by maketopsite on 2023-12-26
> **MAFoElffen said:**
> From an installer LiveUSB (so that the partitions are not mounted), do an fsck on the partition's filesystems...

I would say that it is highly suspect that there is a filesystem problem with that results.

Thank you here seems to be correct answer: [https://www.linuxquestions.org/questions/ubuntu-63/ubuntu-22-04-file-time-info-is-missing-for-some-of-them-4175732084/#post6472217](https://www.linuxquestions.org/questions/ubuntu-63/ubuntu-22-04-file-time-info-is-missing-for-some-of-them-4175732084/#post6472217)

---

### Post by maketopsite on 2023-12-26
But I will try fsck

---

