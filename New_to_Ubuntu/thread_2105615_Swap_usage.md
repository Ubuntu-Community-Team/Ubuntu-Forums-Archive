---
title: "Swap usage?"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-16
Ideally when should swap usage should start, have 2 GiB of RAM memory & dont see it start till approx 700-800 MiB?

Thanks.

---

### Post by arpanaut on 2013-01-16
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by sandyd on 2013-01-16
> **Yezinki said:**
> Ideally when should swap usage should start, have 2 GiB of RAM memory & dont see it start till approx 700-800 MiB?

Thanks.

Depends on the value of vm.swappiness, which can be viewed by
```

sysctl vm.swappiness

```

and changed by

```

sysctl -w vm.swappiness

```
The higher the number, the more the system will use the swap

---

### Post by Yezinki on 2013-01-16
```
vaio@VGC-LS1:~$ sysctl vm.swappiness
vm.swappiness = 60
vaio@VGC-LS1:~$ 

```

What does this mean & can it changhed so that swap is used only after physical memory?

Thanks.

---

### Post by jerome1232 on 2013-01-16
With only 2 Gigs of ram, 60 is probably a sane default. There are reasons that memory might be swapped out (like an application only uses the data during initialization, and never touches it again).

The lowest I would ever go with swappiness is 10, and that's if I had a ton of ram (8+ gigs).

---

### Post by Yezinki on 2013-01-16
Thanks sandyd & jerome1232 for your expert views.

---

