---
title: "g++ compile using postgresql library"
date: 2009-01-29
forum: Programming Talk
---

### Post by bo01 on 2009-01-29
Hi guys,
just another question about postgres-c++.

Does anyone know the exact command (flags etc) for g++ in order to compile and link the libraries of Postgres (libpqxx)? I want to use the c++ library (libpqxx), not the c one (libq-fe.h).

Thanks in advance

---

### Post by bo01 on 2009-01-29
Ok, I think I found it.

For those who has the same question the option in g++ is -lpqxx.

So, the command looks like this:

```
g++ -o output_file.o source_file.o -lpq -lpqxx
```

---

