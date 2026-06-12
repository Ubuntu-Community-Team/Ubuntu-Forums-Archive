---
title: "intercepting another processes I/O"
date: 2018-09-20
forum: Programming Talk
---

### Post by Skaperen on 2018-09-20
i would like to put together a program that can run another program in another process and intercept all of its I/O and filesytem operations.  the other program will likely be tar.  tar will do many things when creating a tar archive and even more when extracting a tar archive.  i need to intercept all of that and handle them.  maybe ptrace()?  anyone know know of examples for this?

---

