---
title: "Don't have man iostream , man std"
date: 2005-02-16
forum: Programming Talk
---

### Post by VaDor on 2005-02-16
Hi ,


I am trying to see some manpages of standart headers such as iostream but i haven't any manual entry!!  Can anyone tell me what package i am missing?

Thanks

e.g:
root@Corbin:/home/vador/c0de # man iostream
No manual entry for iostream

root@Corbin:/home/vador/c0de # man -k iostream
iostream: nothing appropriate.

 man std
No manual entry for std


 :-x

---

### Post by toojays on 2005-02-16
You need something along the lines of libstdc++*-doc, then you can do "man std::iostream".

---

### Post by VaDor on 2005-02-16
[QUOTE=toojays]You need something along the lines of libstdc++*-doc, then you can do "man std::iostream".[/QUOTE]


Thanks working  \\:D/

---

