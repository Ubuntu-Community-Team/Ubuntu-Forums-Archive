---
title: "How do I create the same effect as the Ubuntu password prompt?"
date: 2013-06-08
forum: Programming Talk
---

### Post by GeoMX on 2013-06-08
When you try to run a command/program that requires administrative privileges, Ubuntu shows a password prompt that also dims the screen, I'd like to be able to include this behaviour in my application, does anybody know how could I do it?

Thanks.

---

### Post by micahpage on 2013-06-09
```
sudo apt-get install xcalib
```

to dim
```
xcalib -co 50 -a
```
to clear
```
xcalib -c
```

---

