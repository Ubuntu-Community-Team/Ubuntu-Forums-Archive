---
title: "sed question"
date: 2007-03-10
forum: Programming Talk
---

### Post by jackrobinson on 2007-03-10
Hi I want to write a sed command which will add the string "jack" to the end of all lines in the file /etc/group which start with the string "vboxusers" AND end with a colon ":"  (all quotes are to be ignored).
can anyone help?
I have come up with the following till now but it adds "jack" to the end of all lines following the one with the correct match (and including that as well):
```
sed -e'/^vboxusers/,/\:^/s/$/jack/g' /etc/group
```
Thanks in advance.

---

### Post by Mr. C. on 2007-03-10
```
sed  's/^vboxusers\(.*\):$/vboxusers\1:jack/'
```

---

### Post by jackrobinson on 2007-03-11
> **Mr. C. said:**
> ```
sed  's/^vboxusers\(.*\):$/vboxusers\1:jack/'
```

Thanks a lot! That worked!

---

