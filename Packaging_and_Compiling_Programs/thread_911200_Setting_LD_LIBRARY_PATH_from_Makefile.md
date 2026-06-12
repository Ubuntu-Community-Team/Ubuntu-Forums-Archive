---
title: "Setting LD_LIBRARY_PATH from Makefile?"
date: 2008-09-05
forum: Packaging and Compiling Programs
---

### Post by Cherish76 on 2008-09-05
Hi,

I wanna set the LD_LIBRARY_PATH from within Makefile and am running 8.04. Can anyone let me know how to do it?

Cheers,
-Ram

---

### Post by stpg on 2008-12-06
> **Cherish76 said:**
> Hi,

I wanna set the LD_LIBRARY_PATH from within Makefile and am running 8.04. Can anyone let me know how to do it?

Cheers,
-Ram

-Wl,-rpath -Wl,path_to_shared_libraries

---

