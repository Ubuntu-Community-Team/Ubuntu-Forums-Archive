---
title: "E:couldn't find package compiz settings manager"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by flyshy on 2008-08-04
Hello, 
i am trying to install compiz on my ubuntu 8.0.4 and i continue for get an error message saying E:couldnt find package compiz-setting-manager.  I am trying to find out why its not install.  Secondly when i go to hardware drivers it says no propriety drive are in use on this system.  Any help would be great.

---

### Post by pi.boy.travis on 2008-08-04
Make sure you have the proper repositories installed.  Go to System-Administration-Software Sources to adjust this.

No proprietary drivers is a good thing!  Unless you have hardware that needs proprietary drivers, you shouldn't worry about it.

---

### Post by sisco311 on 2008-08-04
it's compizconfig-settings-manager.

open a terminal and post the output from:
```
lshw -C display
```

---

