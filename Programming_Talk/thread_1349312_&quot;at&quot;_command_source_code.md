---
title: "&quot;at&quot; command source code"
date: 2009-12-08
forum: Programming Talk
---

### Post by mcnikolas on 2009-12-08
Hello , i am trying to find the "at" command source code.I thought that it was in Coreutils but unfortunately it is not :-( . Any ideas were i can find it ???

---

### Post by amauk on 2009-12-08
find which package a program is in
```
dpkg -S /usr/bin/at
```
output:```
at: /usr/bin/at
```
so it's in a package called "at"

get source for a package
```
apt-get source at
```

---

### Post by mcnikolas on 2009-12-08
Thanks a lot !!!!!!!! it worked !!!!!:D:D:D:D:D

---

### Post by Arndt on 2009-12-08
> **amauk said:**
> find which package a program is in
```
dpkg -S /usr/bin/at
```
output:```
at: /usr/bin/at
```
so it's in a package called "at"

get source for a package
```
apt-get source at
```

I'm a newbie when it comes to package handling. Maybe this observation is useful: if the "dpkg -S" command doesn't find anything, it may be because the file given is a symbolic link. Follow the link to its end and give the final actual file to dpkg. 'at' is not a link, but for example 'javaws' is (if you have it installed).

---

### Post by amauk on 2009-12-08
If the symlink is done by the package, then dpkg should pick it up
If the symlink is created after the fact, then dpkg will not be aware of it

---

### Post by mcnikolas on 2009-12-08
I've looked the code of the "at" command but it is kinda difficult to find how "at" makes the command scheduling.Does anybody know the basic concept behind "at"? Does it uses getitimer ,or something like that?
Is there any other way to do command scheduling?

---

