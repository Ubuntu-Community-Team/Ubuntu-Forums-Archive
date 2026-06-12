---
title: "How do i Find out what kind of wireless card i have"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by ranger5664 on 2008-11-29
Is there a terminal command that will tell me the exact type of wireless card i have? I threw away the box (im stupid apparently) and now i have no idea and dont wanna have to open up the computer to find out. If push comes to shove i will open it up tho.

---

### Post by MrWES on 2008-11-29
open a terminal; Applications | Accessories | Terminal and type lspci. Your card should be towards the bottom of the output.

Bill

---

### Post by ranger5664 on 2008-11-29
Thanks man.

---

### Post by night_fox on 2008-11-29
Theres also 

```
lshw -C network
```

---

### Post by nhasian on 2008-11-29
try this from a terminal

```
lshw -C network
```

---

