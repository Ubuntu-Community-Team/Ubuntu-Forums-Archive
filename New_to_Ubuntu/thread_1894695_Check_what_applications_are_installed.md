---
title: "Check what applications are installed"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by fedtobunt on 2011-12-13
How do I check to see what applications/packages are installed?

I believe I selected vftpd to install during ubuntu server install.
but I don't think it is.

---

### Post by nothingspecial on 2011-12-13
```
dpkg --get-selections | grep vftpd
```

---

### Post by asifnaz on 2011-12-13
As **nothingspecial** said

---

