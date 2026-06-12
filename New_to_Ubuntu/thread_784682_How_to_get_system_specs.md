---
title: "How to get system specs"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by TekmonX on 2008-05-06
Hello Ubuntu forums, I was wondering how to get system specs through the terminal, because I'll need them to work with Ubuntu.

---

### Post by tamoneya on 2008-05-06
depends what you want. Here are a couple of standard ones
```
cat /proc/cpuinfo
cat /proc/meminfo
cat /proc/diskstats
sudo lshw
```

---

### Post by TekmonX on 2008-05-06
> **tamoneya said:**
> depends what you want. Here are a couple of standard ones
```
cat /proc/cpuinfo
cat /proc/meminfo
cat /proc/diskstats
sudo lshw
```

I needed the specs on the laptops wireless card, so I figure out what I need to get on the internet with it.

---

### Post by tamoneya on 2008-05-06
```
lspci
```

---

