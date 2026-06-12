---
title: "Unable to configure samba"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by WoodGuitar on 2013-01-06
I installed samba in an attempt to share my printer with other PCs (not running Ubuntu) on my home network.  I wan to edit /etc/samba/smb.conf but I can not as it is read only.  

I tried 'chmod +w /etc/samba/smb/conf' but received "Operation not permitted".  How do I gain access to edit files not in my home directory tree?

---

### Post by Cheesemill on 2013-01-06
You can edit that file by launching gedit with root permissions. Open a terminal (or hit F2) and run the command:
```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by WoodGuitar on 2013-01-06
Thank you, that worked.

---

