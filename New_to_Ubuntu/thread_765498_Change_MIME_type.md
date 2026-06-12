---
title: "Change MIME type"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by LittleKoy on 2008-04-24
Hello,
my ubuntu recognises .cpp and .in files as application/x-*-extension. This wont't give correct highliting in gedit when cpp programming, file preview not viewable, ecc.
How can I change it back? I tried assogiate, but
- If I run as user, I can't change a thing
- If I run as root, .cpp and .in extensions disappear

---

### Post by protorox on 2008-04-30
Try 

```
sudo gedit /usr/share/applications/mimeinfo.cache
```

---

