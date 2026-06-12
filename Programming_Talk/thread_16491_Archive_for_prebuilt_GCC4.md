---
title: "Archive for prebuilt GCC4?"
date: 2005-02-21
forum: Programming Talk
---

### Post by wtd on 2005-02-21
So, to gain access to some Ada2005 features I've been attempting to build GCC 4.0, but I've run into problems.

```
make[1]: *** No rule to make target `../include/ansidecl.h', needed by `regex.o'.  Stop.
```

Does anyone know if there's an archive for it that'll work with Warty and includes the GNAT front-end?

---

### Post by goedson on 2005-02-22
[QUOTE=wtd]So, to gain access to some Ada2005 features I've been attempting to build GCC 4.0, but I've run into problems.

```
make[1]: *** No rule to make target `../include/ansidecl.h', needed by `regex.o'.  Stop.
```

Does anyone know if there's an archive for it that'll work with Warty and includes the GNAT front-end?[/QUOTE]

 You may want to try Debian experimental packages:

```

deb http://ftp.us.debian.org/debian/ ../project/experimental main

```

But it may require some sid packages. Maybe getting the source packages and trying to build on Warty will give better results than those you've got.

---

### Post by wtd on 2005-02-23
Eventually I did manage to get it to work, and the Ada.Directories packages are fantastic stuff.

---

