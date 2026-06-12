---
title: "C program execution error"
date: 2006-01-25
forum: Programming Talk
---

### Post by derm0 on 2006-01-25
Hi All,

I've recently written a c program which I'm almost positive is error free and which compiles with no errors using gcc.

However when I try to execute the a.out file of the program i get the error "cannot execute binary file". 

I was wondering if anyone would have any suggestions on why I'm getting this error and how I might fix it??

Thanks for your time,
Derm

---

### Post by ubuntumaneh on 2006-01-25
maybe, this a permission problem. See the permission with:

ll a.out

Try also:
chmod +x a.out

---

### Post by ubuntumaneh on 2006-01-25
maybe, this a permission problem. See the permission with:

ll a.out

Try also:
chmod +x a.out

---

### Post by derm0 on 2006-01-25
Hi,

It's not a permission problem - i used chmod to change the permission to make sure i had execution rights and it made no difference.

Anyone have any other suggestions??

Thanks,
Derm

---

### Post by otake-tux on 2006-01-25
are you typing ```
./a.out
``` ?

---

### Post by derm0 on 2006-01-25
That was spot on,

Thanks a mil,
Derm

---

