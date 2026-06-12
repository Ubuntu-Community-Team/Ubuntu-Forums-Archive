---
title: "[SOLVED] wine program fonts unreadable"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by sagesparrow on 2008-05-20
When I open any program with Wine (notepad, 7zip, iexplorer) the fonts are not readable.  Maybe there's someting in the Configure window, but I can't read the tabs or options.  Thanks.

---

### Post by schtufbox on 2008-05-20
try this:

```
sudo apt-get install msttcorefonts
```

and then try it. Hopefully should fix the issue you're having.

---

### Post by sagesparrow on 2008-05-20
that did it.  thanks!

---

### Post by schtufbox on 2008-05-20
No problem, glad it helped :)

---

