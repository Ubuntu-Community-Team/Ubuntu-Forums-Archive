---
title: "'AMD Unsupported Hardware' message"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by dmallory42 on 2012-03-28
So, I recently installed the 'ATI/AMD proprietary FGLRX graphics driver' from 'System Settings -> Additional Drivers' because I was having a problem which made HD videos appear choppy when I tried to watch them. 

This seems to have fixed my problem, however, I now have a small box in the bottom right corner of my screen saying "AMD unsupported hardware". 

Anybody know why I'm getting this problem, and how to fix it?

---

### Post by Mark Phelps on 2012-03-28
Would help to know some details -- like what hardware you have.

Open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA" -- and post the results back here.

---

### Post by dmallory42 on 2012-03-28
```
VGA compatible controller: ATI Technologies Inc Device 9806

```

---

### Post by Krytarik on 2012-03-28
> **dmallory42 said:**
> I recently installed the 'ATI/AMD proprietary FGLRX graphics driver' from 'System Settings -> Additional Drivers' ... I now have a small box in the bottom right corner of my screen saying **"AMD unsupported hardware"**.
Please see this thread:

[http://ubuntuforums.org/showthread.php?t=1947390](http://ubuntuforums.org/showthread.php?t=1947390)

Regards.

---

### Post by Mark Phelps on 2012-03-29
> **dmallory42 said:**
> ```
VGA compatible controller: ATI Technologies Inc Device 9806

```

Just so you know, that indicates that you have an AMD Radeon HD 6320 video chip.

---

