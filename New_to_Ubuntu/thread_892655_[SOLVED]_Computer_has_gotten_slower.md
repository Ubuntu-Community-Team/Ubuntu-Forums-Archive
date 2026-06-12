---
title: "[SOLVED] Computer has gotten slower"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-08-17
Topic. This has been happening ever since I started using emerald. I thought that it was the screenlets so I got rid of them, but the speed improved very little. This is what it says when i type top:

```
top - 13:21:36 up 13 min,  2 users,  load average: 0.41, 0.83, 0.73
Tasks: 133 total,   3 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.1%us,  3.5%sy,  0.0%ni, 89.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1034184k total,   908712k used,   125472k free,    35572k buffers
Swap:  3028212k total,        0k used,  3028212k free,   386336k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6398 sanat     20   0 25652  17m 5740 R   11  1.7   1:36.80 compiz.real        
 5904 root      20   0  250m  89m  22m R    7  8.9   2:32.32 Xorg               
 6251 sanat     20   0 48452  23m  13m S    1  2.3   0:02.78 gnome-panel        
 7369 sanat     20   0 65824  19m  10m S    1  1.9   0:00.50 gnome-terminal     
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.36 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1      
```

What should i do to fix this??

---

### Post by fahadsadah on 2008-08-17
How about getting rid of the following: Compiz, Emerald, Beryl, Proprietary hardware drivers

If you don't have one of those, miss it out of the apt command

---

### Post by Bigbob22 on 2008-08-18
I would but I like those effects. I would get rid of emerald if there was a way to install themes without using emerald.

---

### Post by RequinB4 on 2008-08-18
You just want to get rid of emerald?

```

sudo apt-get install simple-ccsm

```

Then go to apps - systools - compiz fusion icon and change the WM from emerald to something different.

You can get non-emerald themes at gnome-look.org.  First, check out system - prefs -art

---

### Post by Bigbob22 on 2008-08-21
What section of gnome-look.org should I look in and how to I use the theme.

---

### Post by Bigbob22 on 2008-08-25
Bump

---

### Post by Bigbob22 on 2008-09-13
bump again

---

### Post by aimpau on 2008-09-13
Um...Try GNOME themes? GTK2.x i think.

---

### Post by billgoldberg on 2008-09-13
> **Bigbob22 said:**
> What section of gnome-look.org should I look in and how to I use the theme.

metacity.

[http://www.gnome-look.org/index.php?xcontentmode=101&PHPSESSID=29c3dab1557310c73c449673733b14db](http://www.gnome-look.org/index.php?xcontentmode=101&PHPSESSID=29c3dab1557310c73c449673733b14db)

Just use "appearance" to install it.

Then pick "window borders" to select it.

---

### Post by Bigbob22 on 2008-09-13
thanks. Wheres window borders?

---

### Post by Bigbob22 on 2008-09-13
nvm, thanks a bunch.

---

