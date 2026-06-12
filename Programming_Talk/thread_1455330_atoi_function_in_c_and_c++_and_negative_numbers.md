---
title: "atoi function in c and c++ and negative numbers"
date: 2010-04-15
forum: Programming Talk
---

### Post by Sidneyaks on 2010-04-15
Can the atoi function in c handle negatives? If it can should I just pass it a "-10" string to get -10 back, or is there some other format?

Thanks :)

---

### Post by Jekshadow on 2010-04-15
Atoi works with negatives for me.

---

### Post by MadCow108 on 2010-04-16
atoi works on negative numbers in the usual format

in c++ you should use streams instead of atoi
int number;
stream >> number;

---

### Post by Compyx on 2010-04-16
In C, you should use strtol(3), since atoi(3) doesn't detect errors and strtol does. But for small student-type programs, atoi is fine, I suppose.

---

