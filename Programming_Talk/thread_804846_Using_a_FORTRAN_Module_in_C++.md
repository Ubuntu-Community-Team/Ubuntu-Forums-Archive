---
title: "Using a FORTRAN Module in C++"
date: 2008-05-23
forum: Programming Talk
---

### Post by Dambrosio on 2008-05-23
I Have a Standard Atmosphere Module with multiple subroutines. I understand how to call the subroutines from C++ using 
extern "C" { void example_(int*,int*) } etc. but the subroutines modify pre-defined variables such as pressure temperature etc. out side the subroutines. How can I load those variables into my c++ so that when I call the FORTRAN subroutines they change the variables in C++.

Thanks,
Dan

---

### Post by Bichromat on 2008-05-23
I understand your variables are declared in your Fortran module ? You may be able to access them by using the following declaration in your C++ code:
```

extern typeofyourvariable nameofyourmodule_MP_nameofyourvariable;

```

EDIT: with gfortran, names seem to be:
```

__nameofyourmodule__nameofyourvariable

```

Try to run objdump on the object file corresponding to your module :
```

$ objdump -x nameofyourmodule.o

```

You should see a list of your variables.

---

### Post by Dambrosio on 2008-05-23
Great, I will try this out when I'm back at work!
Thanks a ton.

---

### Post by Dambrosio on 2008-05-27
Bichromat,
Thank you so much for the information. It worked perfect.

Dan

---

