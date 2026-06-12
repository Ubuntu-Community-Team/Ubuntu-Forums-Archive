---
title: "Access Denied?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Torak on 2008-11-15
Whenever I try to extract a folder into usr/share/background it says I do not have permission to do this. How can i give my self permission?

---

### Post by shifty_powers on 2008-11-15
are you doing it on the command line?

if so then use 

```
sudo tar.....
```

otheriwse, open terminal,

```
gksudo nautilus
```

and do it through nautilus...

---

### Post by halitech on 2008-11-15
> **Torak said:**
> Whenever I try to extract a folder into usr/share/background it says I do not have permission to do this. How can i give my self permission?

the reason it says you do not have permission is because any directory outside your home folder is owned by root and it is not a good idea to mess with permissions. If you have something you need to put somewhere outside your home folder, use the commands shifty_powers suggested.

---

