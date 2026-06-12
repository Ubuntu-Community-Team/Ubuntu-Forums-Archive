---
title: "compiling ogre...."
date: 2007-01-25
forum: Packaging and Compiling Programs
---

### Post by Choad on 2007-01-25
```
/usr/bin/ld: cannot find -lXaw
collect2: ld returned 1 exit status
make[3]: *** [libOgrePlatform.la] Error 1
make[3]: Leaving directory `/home/richard/Desktop/ogrenew/PlatformManagers/GLX/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/richard/Desktop/ogrenew/PlatformManagers/GLX'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/richard/Desktop/ogrenew/PlatformManagers'
make: *** [all-recursive] Error 1
richard@richard-laptop:~/Desktop/ogrenew$ 
```

i fixed various dependencies when doing ./configure, but now i am trying to make it i get this error. the weird bit is that i remember installing libxaw-dev, but yet its still giving me this error...

---

### Post by 23meg on 2007-01-25
There are two Athena dev packages in the repos, libxaw7-dev and libxaw6-dev; maybe you installed the wrong one?

---

