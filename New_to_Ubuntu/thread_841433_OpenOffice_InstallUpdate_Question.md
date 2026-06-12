---
title: "OpenOffice Install/Update Question"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-06-26
What's the difference between the parts of OO.o and the whole?  When I check in Add/Remove, for example, OO.o Writer is listed separately from OO.o (the whole package).  Is there an advantage/disadvantage to the default arrangement in Ubuntu?

Thanks,

Eric

---

### Post by Papenco on 2008-06-26
The advantage is you can uninstall for example the word processor without uninstalling any other of the Open Office applications.
If you use the terminal
```

sudo apt-get remove NameofPackage

```
it will remove the whole Open Office.

---

