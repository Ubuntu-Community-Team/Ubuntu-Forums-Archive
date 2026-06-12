---
title: "High buff/cache memory"
date: 2018-04-08
forum: New to Ubuntu
---

### Post by josephschultz on 2018-04-08
During/after doing file transfers with WinSCP, I find that there is a very large amount of buffed/cached memory on the target machine (Image below). I can clear it by using:

```
sudo sync; echo 3 > /proc/sys/vm/drop_caches
sudo sync; echo 2 > /proc/sys/vm/drop_caches
sudo sync; echo 1 > /proc/sys/vm/drop_caches
```

But I am just wondering why it is not cleared after the file transfer is over.

[ATTACH=CONFIG]279203[/ATTACH]

---

### Post by kerry_s on 2018-04-08
most likely because the space is not needed by any other app/process.

---

