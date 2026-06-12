---
title: "Foobered my synaptic package manager."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by newbnewb on 2008-07-11
Hey folks very new to Linux and I think I foobered my synaptic PM. I tried installing some new apps and got this error.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I opened a terminal and tried running 'dpkg --configure -a' but it always says

bash: dpkg --configure -a: command not found

any suggestions?
Regards to all

---

### Post by nothingspecial on 2008-07-11
You gota sudo it -
```

sudo dpkg --configure -a
```

---

### Post by aktiwers on 2008-07-11
Try do as suggested by the error message:
```
sudo dpkg --configure -a
```

Then do a 
```
sudo apt-get update
```

And it should be fixed :)

---

### Post by newbnewb on 2008-07-11
Less than 20mins to fixed...Take that Microsoft support!! You guys rock! Thanks

---

