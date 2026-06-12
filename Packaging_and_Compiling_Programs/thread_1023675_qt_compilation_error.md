---
title: "qt compilation error"
date: 2008-12-28
forum: Packaging and Compiling Programs
---

### Post by garethrichardadams on 2008-12-28
Hi,

I'm trying to compile a program and am getting this error:

checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!

Can anyone tell me what to apt-get to solve this??

Thanks

Gareth

---

### Post by garethrichardadams on 2008-12-28
Solved it:

```
sudo apt-get install libqt3-headers
```

---

