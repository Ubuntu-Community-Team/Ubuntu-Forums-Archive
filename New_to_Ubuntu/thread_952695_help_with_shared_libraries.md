---
title: "help with shared libraries"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by rpcraig on 2008-10-19
i have a shared library called libt1.so.  I now want to combine object file AddNumbers.o with libt1.so into a new shared library called libnew.so.
Is this possible?  I tried g++ -shared -o libnew.so AddNumbers.o ./libt1.so
but I get an error when trying to link against libnew.so. Such as:
g++ -o temp temp.cpp ./libnew.so I get a few errors about undefined references.
Somebody please help.

---

