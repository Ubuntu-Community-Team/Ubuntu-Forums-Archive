---
title: "Package dependency/wine issue"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by revaew on 2012-11-26
I just recently installed 12.10 and I am trying to install wine. I followed the instructions from their website but when I click on install I get the error " Package dependencies cannot be resolved" with the following details:
```
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

``` 

I am not sure exactly what that means.

---

### Post by LuciferRex on 2012-11-26
Which WINE install did you use?
Edit: you should use the "Microsoft Windows Compatibility Layer (meta-package)"

---

### Post by Shuudoushi on 2012-11-26
> **revaew said:**
> I just recently installed 12.10 and I am trying to install wine. I followed the instructions from their website but when I click on install I get the error " Package dependencies cannot be resolved" with the following details:
```
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

```I am not sure exactly what that means.

[http://http://www.playonlinux.com/en/](http://http://www.playonlinux.com/en/)
Use this it wil make sure you have the right ver of Wine and will even download and install it for you.

---

### Post by revaew on 2012-11-26
I tried installing 1.4 and 1.5

---

