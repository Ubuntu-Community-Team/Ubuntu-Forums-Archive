---
title: "Deleting item in recyle bin"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-07-12
I have 2 folders in my deleted items, but i cant delete them, due to lack of permission..... I have try changing the permission but haven't had any luck so far, error you don't have enough permission to do this operation
Any ideas?

---

### Post by sisco311 on 2008-07-12
open nautilus as root (in the Trash folder):
Press Alt+F2 and type:
```
gksu nautilus ~/.local/share/Trash/files/
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ibizatunes on 2008-07-12
Thanks it work perfectly

---

