---
title: "Nvida Geforce 8400M, and extending desktop"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by skydiving85 on 2008-09-09
is there any way for me to extend my desktop so that my secondary display works as a separate but attached identity; so that programs can be maximized in it but still be accessible from the primary? also the seperate display option does not work as it the nvidia control panel refuses to let me save my configeration
any help would be much appreciated
thanks

---

### Post by silverglade00 on 2008-09-09
You need to run the nvidia-settings control panel as root. 

```
gksudo nvidia-settings
```

That will let you save the changes.

---

