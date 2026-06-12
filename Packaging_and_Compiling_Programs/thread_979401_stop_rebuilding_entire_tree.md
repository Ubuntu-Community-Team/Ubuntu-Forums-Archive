---
title: "stop rebuilding entire tree"
date: 2008-11-11
forum: Packaging and Compiling Programs
---

### Post by dmcbob on 2008-11-11
it seems like my changes don't get incorporated unless i run git-clean -xdf and rebuild the entire source tree. the command i'm running to build is: 
```
CONCURRENCY_LEVEL=4 NOEXTRAS=1 skipabi=true skipmodule=true fakeroot debian/rules binary-core2
```

the code i'm changing is under drivers/char if that makes a difference.

also, is it possible to remove the currently-installed OS by doing dpkg --remove linux-image-core2.deb? seems like that might be a reason i'm getting the same OS when i boot up. it doesn't explicitly error, but i don't know how else to explain the behavior unless a) the old os isn't being removed or b) the new os is being compiled without incorporating the new changes.

thanks,
ivan

---

### Post by dmcbob on 2008-11-20
bump! comeon, isn't git what everyeone's supposed to be using for packages and getting the latest build?

---

