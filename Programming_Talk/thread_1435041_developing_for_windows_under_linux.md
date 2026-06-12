---
title: "developing for windows under linux"
date: 2010-03-21
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-03-21
the best way to do that ? 
testing on virtual machines or Wine ? 
can i use the windows libraries on virtual machines ?

---

### Post by mdurham on 2010-03-21
I would say use a virtual machine. I've always used VirtualBox with Visual Studio and had no problems at all. You can use all Windows libraries.
Cheers, Mike

---

### Post by amauk on 2010-03-21
you can cross compile windows apps in Linux using MinGW
```
sudo apt-get install mingw32
```

then instead of```
gcc -o program program.c
```
use```
i586-mingw32msvc-gcc -o program program.c
```

google around for how to set up the various IDEs for using MinGW

I wouldn't use wine to test things
use a proper windows install (either native or in a VM)

---

