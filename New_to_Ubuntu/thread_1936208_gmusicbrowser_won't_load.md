---
title: "gmusicbrowser won't load"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by 118118 on 2012-03-05
as follows:```

luke@luke-AOD260:~$ gmusicbrowser
print() on closed filehandle $fifofh at /usr/bin/gmusicbrowser line 286.
Bus error
```:)

---

### Post by Toz on 2012-03-05
Are you running the precise beta? See: [http://ubuntuforums.org/showthread.php?t=1878702]("http://ubuntuforums.org/showthread.php?t=1878702").

Short answer:
```
gmusicbrowser -nodbus
```
...then
```
gmusicbrowser -plugin MPRIS2
```

---

### Post by 118118 on 2012-03-18
hi, pretty sure this is woking fine now. i don't remember doing anything....... ha. cheers for the reply :)

---

