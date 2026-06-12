---
title: "bash sort file of numbers onto new lines"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by kenny5 on 2013-10-01
Hi,
How do I sort a file of numbers that looks like this: 
2 1 4 6 7 8 6 5 6 9 3 2 4 0 

to look like this:
0
1
2
2
3
4
5
6
6
7
8
9

Thanks!

---

### Post by The Cog on 2013-10-01
```
cat filename | tr ' ' '\n' | sort
```

---

### Post by kenny5 on 2013-10-01
Thanks The Cog

---

