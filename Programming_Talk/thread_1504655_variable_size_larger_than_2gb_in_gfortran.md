---
title: "variable size larger than 2gb in gfortran"
date: 2010-06-08
forum: Programming Talk
---

### Post by Zyren on 2010-06-08
Hello,

I have a program at work that i wrote in fortran (gfortran compiler), but i am having huge problems with variable sizes. My issue is that gfortran wont allow any variables larger than 2gb. Also, when i try using openMP in my algorithm, it constantly crashes if my variables are larger than like a few MB. 

My issue is that i need to support large addresses. I had coded the same program in C and hit the same issue, but i was able to find an answer. I had to enable large addresses. I am assuming this is the same issue i have with gfortran. However, i am unable to find how to do this in the documentation. 

Does anyone know how to enable large addressed with gfortran?

edit: just for clarification i am using the 64 bit gfortran compiler on windows 7 64 bit. If windows is a problem i can install linux on this. 

thanks

---

### Post by Axos on 2010-06-08
The following page says that gfortran accepts all the gcc command line options. So if you found a command line option to enable large addresses in gcc, chances are it should also work for gfortran. Give it a shot.

[http://gcc.gnu.org/onlinedocs/gfortran/Invoking-GNU-Fortran.html#Invoking-GNU-Fortran](http://gcc.gnu.org/onlinedocs/gfortran/Invoking-GNU-Fortran.html#Invoking-GNU-Fortran)

Sorry I don't actually know anything about Fortran.

---

