---
title: "Google Earth COM API under Linux?"
date: 2007-09-12
forum: Programming Talk
---

### Post by zoniq on 2007-09-12
Is there a way to access the [Google Earth COM API]("http://earth.google.com/comapi/") unter Linux? I thought about using WINE for GE and also my application. But I think there should be a better solution.

GE itself is Qt, but the API is COM, which I think is a Microsoft thing.

Thanks

---

### Post by aks44 on 2007-09-12
> **zoniq said:**
> the API is COM, which I think is a Microsoft thing.

COM (aka ActiveX, although there are some slight differences between the two, ActiveX being a "refinement" of COM) is indeed a Microsoft-specific technology.


I'm pretty positive that the Linux version of Google Earth doesn't use COM APIs, since this technology isn't supported under Linux...

---

