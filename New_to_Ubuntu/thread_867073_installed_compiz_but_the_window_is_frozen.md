---
title: "installed compiz but the window is frozen"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-22
i installed compiz fusion and compiz icon through synaptic,but its frozen
at dconfig deferred processing taking place.how do i un freez it?
rick

---

### Post by Rocket2DMn on 2008-07-23
Is this problem resolved yet?  That is typically the last line it shows before you can close the window.  If you ended up killing Synaptic, you will need to run this command before you can use the package manager(s) again:
```
sudo dpkg --configure -a
```

---

