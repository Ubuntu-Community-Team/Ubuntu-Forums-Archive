---
title: "Help with ubuntu software center after gimp install"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by Red Razor on 2011-11-10
Tried to install gimp in 11.10 and now software center is frozen. Cannot seem to remove gimp or install other software from the software center or terminal. Keep getting the following from the terminal:
```
The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (<= 2.6.11-z) but 2.7.4-2011102201~oo is to be installed
        Depends: gimp-data (<= 2.6.11-z) but 2.7.4-2011102201~oo is to be installed
```

Any help would be greatly appreciated to get my system back up and running correctly. Thanks ahead of time from a linux newbie!

---

### Post by sadaruwan12 on 2011-11-10
Did you tried this

```
sudo apt-get purge --remove gimp
```

use the terminal to do this.

---

