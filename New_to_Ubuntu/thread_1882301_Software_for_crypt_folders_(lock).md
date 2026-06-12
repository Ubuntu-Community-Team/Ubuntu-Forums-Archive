---
title: "Software for crypt folders (lock)"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by LukaHr on 2011-11-17
I got folder my pictures on pc, external hard disk and now I will transfer it on laptop. But id there any way to secure them so if i lose laptop no one can see my pictures? So kind of password or better security idea?

---

### Post by surfer on 2011-11-17
yes there is!

there are several tools:
[truecrypt]("http://www.truecrypt.org/") is a famous one.

if you have a whole partition you would like to encrypt, dm-crypt (cryptsetup package) is a good choice.

if you only want to have a directory where everything you put in is encrypted (including the file/directory names) encFS (package: encfs) and cryptkeeper as frontend may be the simplest solution.

---

### Post by LukaHr on 2011-11-17
Thanks man!

---

