---
title: "Root access"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Kranzio on 2008-07-22
I need to change one line in the splunk.postinst file, but am unable to gain root access to it and root is the current owner. Any help would be most appreciated.

---

### Post by dje on 2008-07-22
try in a terminal (Applications >> Accessories >> Terminal):
```
gksu gedit /path/to/splunk.postinst
```

dje

---

### Post by Kranzio on 2008-07-22
Thanks!! That worked.  Is there a place I can get the list of commands and what they are for?

---

### Post by dje on 2008-07-22
no problem :)
[http://linuxcommand.org]("http://linuxcommand.org/") is a good place to start

dje

---

