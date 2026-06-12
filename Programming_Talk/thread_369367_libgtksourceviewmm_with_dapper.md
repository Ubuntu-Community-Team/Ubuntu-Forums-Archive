---
title: "libgtksourceviewmm with dapper?"
date: 2007-02-24
forum: Programming Talk
---

### Post by maddog39 on 2007-02-24
Hello all,

Well first off all, why isnt this availible in the dapper repos and second how do you (anyone who uses it) get around this problem in dapper. Whenever I install from source, my apps compile with the headers ok, but when I run the binaries I get an invalid .so.2 file or something. I dont have the option to upgrade to edgy on the computer I need to develop on either. What do/can you/I respectively, about this problem.

Thanks!
-maddog39

---

### Post by po0f on 2007-02-24
maddog39,

Just create a symlink from the library to the file your binary is looking for.

---

