---
title: "File permissions"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by ZenMasterInTraining on 2013-04-10
I've created a specific directory with multiple files and I need to set read / write / execute permissions for all files in this folder read / write / execute for group only and not allow for 'others', what is the best way to go about this using CLI?

---

### Post by Frogs Hair on 2013-04-10
Here is a place to start until further responses come. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ZenMasterInTraining on 2013-04-10
> **Frogs Hair said:**
> Here is a place to start until further respoces come. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thanks for the reply I looked there already, I found it more confusing. somebody already explained it to me and it seems I want to do the following:

chmod 070 file, file, file, file

---

### Post by steeldriver on 2013-04-10
Why do you want no permissions for the owner?

Why do you want all files to have execute permission? unless they are actually executable (scripts or binaries) then what you probably want is something like

```
chmod ug=rwX,o= *yourdir*
```

Tell us your purpose and we can give better advice

---

### Post by ZenMasterInTraining on 2013-04-10
Solved, used chmod 770 file* which did the trick

---

