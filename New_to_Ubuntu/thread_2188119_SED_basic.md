---
title: "SED basic"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by manuj on 2013-11-15
Followin expression:
  echo abcd123 | sed 's/\([a-z]*\).*/\1/'

is supposed to give the result "abcd". But I am getting "abcd123".
WHY??

---

### Post by MG&amp;TL on 2013-11-15
Which version of *sed* are you running?

```
michael@michael-laptop:/tmp$ echo abcd123 | sed 's/\([a-z]*\).*/\1/'
abcd

```

---

### Post by drmrgd on 2013-11-15
Also seems to work OK with the extended regex option to sed:

```

$ echo abcd123 | sed -r 's/([a-z]*).*/\1/'
abcd

```

---

