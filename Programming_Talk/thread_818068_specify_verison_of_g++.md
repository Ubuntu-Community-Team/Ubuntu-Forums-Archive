---
title: "specify verison of g++"
date: 2008-06-04
forum: Programming Talk
---

### Post by abraxas334 on 2008-06-04
Heya,
I was wondering if there is a way to specify which version of g++ i use for compiling. I have the latest one installed but would like to use an older version. Is that somehow possible?
Antonia

---

### Post by lixx on 2008-06-04
> **abraxas334 said:**
> Heya,
I was wondering if there is a way to specify which version of g++ i use for compiling. I have the latest one installed but would like to use an older version. Is that somehow possible?
Antonia

a 'hackish' solution would be is to change symlinks.
in my system, /usr/bin/g++ is a symlink which points to 
/usr/bin/g++-4.2. 
so if i were to change that to an older version,
i would simply issue this command:
```
sudo ln -sf /usr/bin/g++-3.4 /usr/bin/g++
```
--> assuming i have version 3.4.

---

### Post by abraxas334 on 2008-06-04
Thanks lixx that worked well for me :)

---

### Post by geirha on 2008-06-04
The better way is to set the environment variable CXX to the desired g++ version. Any sane makefile will read this variable. I.e.

```

export CXX=g++-3.4
./configure
make

```

---

