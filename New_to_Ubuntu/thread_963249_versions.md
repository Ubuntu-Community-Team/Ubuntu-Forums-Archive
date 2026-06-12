---
title: "versions"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by jsshere on 2008-10-30
How to find out the kernel version and Ubuntu version using terminal?

---

### Post by igknighted on 2008-10-30
For kernel version:
```
uname -r
```

---

### Post by Marshal0505 on 2008-10-30
more options and info , try : 

```
man uname
```

---

### Post by hellion0 on 2008-10-30
To find out your Ubuntu version:
```
cat /etc/issue | grep Ubuntu | cut -c1-13
```

---

