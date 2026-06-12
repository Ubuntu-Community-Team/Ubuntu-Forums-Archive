---
title: "Using date command: i want AAAA-MM-DD HH:MM:SS instead of AAAA-MM-DDHH:MM:SS"
date: 2009-07-08
forum: Programming Talk
---

### Post by tirengarfio on 2009-07-08
Hi,

im trying to use date command to show the date in this format:

AAAA-MM-DD HH:MM:SS

I got this format with "date +%Y-%m-%d%H:%M:%S":

AAAA-MM-DDHH:MM:SS

But i want to leave a space between the date and the time, 

Any way?

Ciao

---

### Post by unutbu on 2009-07-08
```
date "+%Y-%m-%d %H:%M:%S"
```

---

### Post by tirengarfio on 2009-07-08
Thanks! it worked

---

