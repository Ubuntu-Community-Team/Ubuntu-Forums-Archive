---
title: "Networks and windows"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by lift_test on 2008-09-06
I've done it before with dapper but now can't remember how/where you enter your win workgroup name, any help please.

---

### Post by wolfen69 on 2008-09-06
```
gksudo gedit /etc/samba/smb.conf
``` near the top you will see WORKGROUP=MSHOME

replace MSHOME (or whatever else it may have) with the workgroup you need.

---

