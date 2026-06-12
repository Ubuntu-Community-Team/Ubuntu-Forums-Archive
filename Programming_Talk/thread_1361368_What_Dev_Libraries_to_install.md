---
title: "What Dev Libraries to install"
date: 2009-12-21
forum: Programming Talk
---

### Post by dale8458 on 2009-12-21
As a rule what dev libraries and header packages should be installed on a new install.  I need to make sure I can build ruby, php and other service related shared libs or languages from source... Oh we are using 9.10 64bit.

Thanks

---

### Post by nvteighen on 2009-12-22
> **dale8458 said:**
> As a rule what dev libraries and header packages should be installed on a new install.  I need to make sure I can build ruby, php and other service related shared libs or languages from source... Oh we are using 9.10 64bit.

Thanks
Well... install the build-essentials package. And from there on, install those you need.

---

### Post by geirha on 2009-12-22
And for packages that exist in the repositories (like ruby and php), you can install the needed development packages with apt-get build-dep. E.g.: 
```
sudo apt-get build-dep php5
```
Though of course, package dependancies may change from one version to the next, though you'll likely get most of the needed packages that way.

---

### Post by dale8458 on 2009-12-30
Thanks I did not know about the build-dep.  SO if I use build-dep plus what ever it is I am installing it will resolve the build-dep for that product?  Cool

---

