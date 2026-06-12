---
title: "Failure repacking RPM-package"
date: 2020-12-09
forum: Packaging and Compiling Programs
---

### Post by spielmops on 2020-12-09
I need a package that's only available in RPM-package converted to deb. I started alien on that package and:

```
root@HartmutsPi:/home/hartmut/Downloads# alien --target aarch64 pix-1.6.2-lp152.3.3.aarch64.rpm 
....
pix-1.6.2-lp152.3.3.aarch64.rpm is for architecture aarch64 ; the package cannot be built on this system

root@HartmutsPi:/home/hartmut/Downloads# uname -a
Linux HartmutsPi 5.8.0-1006-raspi #9-Ubuntu SMP PREEMPT Fri Oct 16 12:55:30 UTC 2020 aarch64 
```

Is alien not able to convert packages with aarch64-architektur?

Spielmops

---

