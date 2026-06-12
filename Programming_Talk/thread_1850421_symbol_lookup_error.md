---
title: "symbol lookup error"
date: 2011-09-26
forum: Programming Talk
---

### Post by madjid.80 on 2011-09-26
HI all 
When i want to run my program this error occur : 
```
symbol lookup error: /usr/lib/libQtOpenGL.so.4: undefined symbol: _ZN14QWidgetPrivate15checkWindowRoleEv
```I used ldconfig --format=compat /usr/lib and it didn't worked

Thanks

---

### Post by Bachstelze on 2011-09-26
Paste your code and the command you run to compile it.

---

### Post by karlson on 2011-09-26
> **madjid.80 said:**
> HI all 
When i want to run my program this error occur : 
```
symbol lookup error: /usr/lib/libQtOpenGL.so.4: undefined symbol: _ZN14QWidgetPrivate15checkWindowRoleEv
```I used ldconfig --format=compat /usr/lib and it didn't worked

Thanks

Check output of:
```

$ ldd <binary>

```

Make sure that the libraries you are loading are actually the right ones.

---

