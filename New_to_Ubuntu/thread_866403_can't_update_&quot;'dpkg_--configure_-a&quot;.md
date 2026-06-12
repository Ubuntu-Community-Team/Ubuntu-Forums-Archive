---
title: "can't update &quot;'dpkg --configure -a&quot; ????"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by takspiderman on 2008-07-21
I just installed Ubuntu and tried to update but during the rocess my laptop shut down.  Now when I try to update it states
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
can someone help me to update?

---

### Post by phidia on 2008-07-21
Try the dpkg command with "sudo". Hope that helps.

---

### Post by ibutho on 2008-07-21
Run Applications -> Accessories -> Terminal and enter the command
```
sudo dpkg --configure -a
```

---

### Post by cjv8888 on 2008-07-21
Just open a terminal and run
> sudo dpkg --configure -a

---

### Post by SunnyRabbiera on 2008-07-21
This is a common issue, nothing to worry about.

---

