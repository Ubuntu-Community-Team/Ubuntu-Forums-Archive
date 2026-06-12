---
title: "errors"
date: 2018-09-26
forum: New to Ubuntu
---

### Post by aaabbbooo on 2018-09-26
I have Ubuntu 18.04 and display problems.
So I wanted to install a different driver, i.e nvidia driver 390.
I ran ubuntu-drivers autoinstall, which tells me that I have unmet dependencies.

```

libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not going to be installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed.
```

I am told to run apt --fix-broken install
which I did, and that gave me an dpkg-divert: error:mismatch on package

```
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.87-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.87-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Where do I go from here?:KS

---

