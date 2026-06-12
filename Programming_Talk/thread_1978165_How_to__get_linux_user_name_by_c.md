---
title: "How to  get linux user name by c ?"
date: 2012-05-11
forum: Programming Talk
---

### Post by prismctg on 2012-05-11
how to get username via C progam & how to strore it into a variable ?

---

### Post by r-senior on 2012-05-11
Have a look at the documentation for getlogin, getlogin_r and cuserid:

```
man 3 getlogin
```

---

