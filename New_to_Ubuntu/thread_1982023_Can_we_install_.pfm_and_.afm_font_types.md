---
title: "Can we install .pfm and .afm font types?"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-17
Hi All

Is it possible to install .afm and .pfm font types in Linux? They are a native Windows font type and come with a .pfb metrics file.
I know .ttf and .otf fonts install, but what about these?

Glenn.

---

### Post by dniMretsaM on 2012-05-17
I think you just need to copy the .pfb file into the [FONT=courier new]~/.fonts/[/FONT] folder. Then you need to log out and log back in or run this in terminal:
```
fc-cache -fv
```

---

### Post by Senior_Buckethead on 2012-05-19
Thanks, that works great!

---

