---
title: "Help! Runaway process!!!"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by chadwit on 2008-08-26
my "apt-cache" process all of a sudden started pegging my proc @ 100% upon booting. If I try to kill it I get this response: 

Cannot kill process with pid 16271 with signal 19.
No such process

I tried rebooting using a previous kernel version and it's still pegged.

What is "apt-cache"? Why is it all of a sudden doing this? How do I make it stop?

Thanks..............

---

### Post by neurostu on 2008-08-27
try:
```

sudo kill -9 16271

```

---

