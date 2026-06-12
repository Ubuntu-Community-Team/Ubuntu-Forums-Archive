---
title: "rpm installing trouble as normal user.."
date: 2011-05-26
forum: Programming Talk
---

### Post by Blackbug on 2011-05-26
I am trying to install a RPM in SUSE ( i know its ubuntu forum, but linux related and since i use ubuntu at home so i have right...D)
 
well, i don't have admin rights, and till now i was installing packages by compiling it and using --prefix option to install everythin in my home dir. But, gtk has lot of dependencies and i have spent whole 8 hours installing packages one by one and its irritating me.
 
rpm -ivh <rpmname>  is givin following error:
 
```
rpm -i --prefix=/nethome/tmt507/k/karnatak/bin/ gtk3-3.0.9-35.11.src.rpm
warning: gtk3-3.0.9-35.11.src.rpm: Header V3 DSA signature: NOKEY, key ID 629ff0c2
error: cannot write to %sourcedir /usr/src/packages/SOURCES

```
 
any help will be appreciated..

---

### Post by Blackbug on 2011-05-26
can i just bypass the root directory structure installation(default one) with user defined path?? similar to the way we provide user defined path while compling code
```

./configure --prefix="user-defiend-path"
```

---

