---
title: "Advanced Desktop Effect Settings Promblems"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by waffleturd on 2008-11-13
The effects I enabled were working fine, until i was trying to change the resolution. When that happened everything that I enabled didn't seem work. For example the cube effect and others didn't work. I reinstalled Compiz and advanced destop effect settings and when I updated the settings it seems like nothing haved. I won't update.
How can I fix this?

---

### Post by Daveth on 2008-11-13
so, are you back to your original resolution now? Which settings did you try to update- those in Compix or the screen resolution?

---

### Post by cariboo on 2008-11-13
When  you reinstall a program in Linux 99%  of the time it doesn't make any difference, because the configuration file used with the previous installation is still there. All the desktop effects configurations are located in ~/.compiz/session. The files on my computer look like this:

```
ls -l
total 8
-rw-r--r-- 1 jimk jimk 592 2008-11-13 14:14 1021f0cd8227d774e2122660968870932600000059990023
-rw-r--r-- 1 jimk jimk 344 2008-11-13 12:53 106c29c2a6bf61d4ae122660907764813800000100190023
```

These are xml files, so they can be edited, or in your case you just may want to delete them and start all over again.

Jim

---

