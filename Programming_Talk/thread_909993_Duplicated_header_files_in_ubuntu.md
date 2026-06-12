---
title: "Duplicated header files in ubuntu?"
date: 2008-09-04
forum: Programming Talk
---

### Post by StOoZ on 2008-09-04
I wonder , any reason why do I have duplication of dirent.h ?
> /usr/include/dirent.h
/usr/include/bits/dirent.h
/usr/include/linux/dirent.h
/usr/include/tcl8.4/tcl-private/compat/dirent.h
/usr/src/linux-headers-2.6.24-19/include/linux/dirent.h
/usr/src/linux-headers-2.6.24-19-generic/include/linux/dirent.h


---

### Post by slavik on 2008-09-04
some might be links, others might be including different dirent.h files.

keep in mind that /usr/include/tcl8.4 is for tcl headers, not C.

---

### Post by StOoZ on 2008-09-04
I see , so basically if I want to use it in a C++ program , I will use 
> /usr/include/dirent.h ?

---

### Post by slavik on 2008-09-04
yes ... #include <cdirent> (or w/e the C++ way for including C system headers is).

---

### Post by StOoZ on 2008-09-04
Right. I hate the design of these C library files... :(

---

### Post by slavik on 2008-09-04
what exactly do you dislike about them?

---

### Post by StOoZ on 2008-09-04
they are not C++ user friendly :)

---

