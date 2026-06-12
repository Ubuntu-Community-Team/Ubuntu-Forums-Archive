---
title: "[SOLVED] trying to install i get a dpkg error"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by brucegriffin on 2008-08-29
I was trying to install windows drivers ndiswrapper from the add-remove and when I do I get this error message. Hope someone can tell me what to do.



```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by SunnyRabbiera on 2008-08-29
just do as the error message says and in a terminal input this:
sudo dpkg --configure -a
just copy and paste it into a terminal

---

### Post by nothingspecial on 2008-08-29
> **brucegriffin said:**
> I was trying to install windows drivers ndiswrapper from the add-remove and when I do I get this error message. Hope someone can tell me what to do.



```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Do what it says. Open a terminal (applications > Terminal) and type
```

sudo dpkg --configure -a
```

---

### Post by brucegriffin on 2008-08-29
Thank you both for the replies that worked.

---

