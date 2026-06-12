---
title: "I can't Install anhthing. Why?"
date: 2007-05-20
forum: Programming Talk
---

### Post by Ameliorate on 2007-05-20
whenever I install anything i get an error saying that  an
"An apt based error occured and installation was unsuccessful."

Any help here?

---

### Post by samjh on 2007-05-20
Perhaps try:```
sudo dpkg --configure -a
```It tries to repair failed package installations from previous runs.

---

