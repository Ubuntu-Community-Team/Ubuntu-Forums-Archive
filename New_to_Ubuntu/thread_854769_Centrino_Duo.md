---
title: "Centrino Duo"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by jaymacs on 2008-07-09
Hey all,

I have a Dell Latitude D620 with the Intel Centrino Duo processor.  How do I ensure that I am using it properly?  Am I supposed to select a different kernel, if so, which one? Thank you.

---

### Post by Vivaldi Gloria on 2008-07-09
> **jaymacs said:**
> Hey all,

I have a Dell Latitude D620 with the Intel Centrino Duo processor.  How do I ensure that I am using it properly?  Am I supposed to select a different kernel, if so, which one? Thank you.

Ubuntu works out of the box with duo/quad processors. The kernel has SMP support built in. See that

```
uname -a
```

contains the word "SMP". So you don't have to do anything. If you want you can use

```
sudo lshw -class system -class processor
```

and see that you indeed have cpu0 and cpu1.

---

### Post by jaymacs on 2008-07-09
Thanks, wanted to be sure.

---

