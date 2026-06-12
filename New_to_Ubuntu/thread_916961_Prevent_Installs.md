---
title: "Prevent Installs?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by jcherepy on 2008-09-11
I have Ubuntu installed on an Asus Eee with limited storage space and the update manager wants to install Samba and I don't need or want it.  How do I keep the update manager from continually showing Samba as an update?

Thanks,
Bill

Please ignore.

---

### Post by LowSky on 2008-09-11
For update manager to tell you you need to update Samba means you have Samba installed

run this command from terminal to check if it is installed

```
dpkg -l "samba*"
```BTW "l" is a lower case L

---

### Post by Joeb454 on 2008-09-11
> **LowSky said:**
> For update manager to tell you you need to update Samba means you have Samba installed

run this command from terminal to check if it is installed

```
dpkg -l "samba*"
```BTW "l" is a lower case L

That's a good point. If it is installed I'm sure you could uninstall it, provided there was no dependency issues

---

### Post by LowSky on 2008-09-11
Yea I should have mentioned that too.

jherepy do you use network folders or printers. You need Samba to access those.

---

### Post by meindian523 on 2008-09-11
> **jcherepy said:**
> I have Ubuntu installed on an Asus Eee with limited storage space and the update manager wants to install Samba and I don't need or want it.  How do I keep the update manager from continually showing Samba as an update?

Thanks,
Bill

Please ignore.
Please also post the solution.And mark the thread solved.

---

