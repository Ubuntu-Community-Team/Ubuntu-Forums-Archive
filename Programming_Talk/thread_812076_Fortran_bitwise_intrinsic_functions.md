---
title: "Fortran bitwise intrinsic functions"
date: 2008-05-29
forum: Programming Talk
---

### Post by jwbales on 2008-05-29
x

---

### Post by Bichromat on 2008-05-29
Hmmm, you should try... gfortran!

```
program logic

integer :: a=4, b=6

print *, iand(a,b), ior(a,b), ieor(a,b)

end program
```

works perfectly here :confused:

---

### Post by jwbales on 2008-05-29
> **Bichromat said:**
> Hmmm, you should try... gfortran!

```
program logic

integer :: a=4, b=6

print *, iand(a,b), ior(a,b), ieor(a,b)

end program
```

works perfectly here :confused:
Thanks, bichromat, for your quick response. 

I realized my error immediately after my post and returned to delete the post before I saw that it already had a response. Sorry about the deletion.

I was trying to use these as 'infix' functions, 'i.iand.j' and 'i.ieor.j'.

Duh!

I haven't used fortran in 25 years and am trying to catch up.

Thanks again.

---

