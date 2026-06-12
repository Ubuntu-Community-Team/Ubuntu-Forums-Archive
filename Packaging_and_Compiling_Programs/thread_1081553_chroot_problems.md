---
title: "chroot problems"
date: 2009-02-26
forum: Packaging and Compiling Programs
---

### Post by jnw222 on 2009-02-26
i am trying to create a set of programs (like a miniture linux OS) that i can chroot into using source-compiled programs

i have /bin/bash and a /bin/sh-to/bin/bash link 
but when i try to chroot into the folder containing / of the mini-system i get 
```
jubuntu@jubuntu-desktop:~$ sudo chroot /media/foo/
[sudo] password for jubuntu: 
chroot: cannot run command `/bin/bash': No such file or directory
jubuntu@jubuntu-desktop:~$ ls /media/foo/bin/bas*
/media/foo/bin/base64    /media/foo/bin/bash

```

help? i am using this to show off to my friends

---

### Post by caljohnsmith on 2009-02-26
How about posting the output of:
```
ls -l /media/foo/bin/bash
/media/foo/bin/bash
```

---

### Post by jnw222 on 2009-02-26
-rwx------ 1 jubuntu root 2332536 2009-02-22 12:52 /media/foo/bin/bash

typing in path to the bash shell opens up a new bash shell (even from dash or ash

---

### Post by caljohnsmith on 2009-02-26
> **jnw222 said:**
> [COLOR="Blue"]-rwx-----[/COLOR]- 1 [COLOR="Blue"]jubuntu[/COLOR] root 2332536 2009-02-22 12:52 /media/foo/bin/bash

typing in path to the bash shell opens up a new bash shell
I don't know what you did to install all your programs under /bin, but I think they should be owned by "root" and not you ("jubuntu"). Or at least you should give "root" permission rights on the programs. How about doing:
```
sudo chown root:root /media/foo/bin/bash
sudo chmod 755 /media/foo/bin/bash
```
Then try chrooting again, and let me know if that makes any difference.

---

### Post by jnw222 on 2009-02-28
still doesn't work
i'm able to ./bash, but not chroot
chroot's bash version is 4.0
coreutisl is 7.1 and 6.1 

fs type is ext3 (default settings)

---

### Post by Cracauer on 2009-03-02
Actually this is probably complaining about a missing ld-linux.so or some base library.

Post
1) ldd on that bash
2) then take the output and make sure all that junk is present in the chroot

---

### Post by jnw222 on 2009-03-04
problem solved
missing some lib's
chroot works

---

