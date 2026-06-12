---
title: "Do not hibernate the system"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by aju1991 on 2011-09-20
My ubuntu 11.04 do not go to hibernate mode.
They shows that 'not enough cache' and system goes to stand by(sleep)


What is the problem??????????
Can any one help me???????????

---

### Post by technosysind on 2011-09-20
How much free space do you have on the partition on which you have installed Ubuntu??

---

### Post by Elfy on 2011-09-20
Please open a terminal and run 

```
free -m
```

post the output

---

### Post by aju1991 on 2011-09-20
> **technosysind said:**
> How much free space do you have on the partition on which you have installed Ubuntu??


20 gb tokk for the partition and now system has above 9 gb free space

---

### Post by Elfy on 2011-09-20
Please run the command I gave you.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

We need to check your swap and ram, not how big your partition is.

---

### Post by shubham1 on 2011-09-20
try insatlling hibernate
sudo apt-get install hibernate
open system monitor and tell your swap size in resoures tab

---

### Post by Elfy on 2011-10-05
From a PM 

free -m gives

```
total used free shared buffers cached
Mem: 2886 2873 13 0 687 1587
-/+ buffers/cache: 598 2288
Swap: 876 0 876
```

You need to increase your swap.

---

