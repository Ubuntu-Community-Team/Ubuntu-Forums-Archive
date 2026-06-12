---
title: "Compiler argument order - why?"
date: 2008-05-11
forum: Programming Talk
---

### Post by squaregoldfish on 2008-05-11
Having just spent an entire day of frustration using gfortran (GCC) for the first time, and getting the arguments in the wrong order, I'm interested to see if there's a reason why the order of arguments is so sensitive. For example,

```
gfortran -Wall -I/usr/local/include -L/usr/local/lib -lnetcdf -o ZonalAverage ZonalAverage.f90 
```

won't link properly, but

```
gfortran -Wall -I/usr/local/include -o ZonalAverage ZonalAverage.f90 -L/usr/local/lib -lnetcdf
```

will.

Before I have a complete rant over why we haven't moved on from the order of command line arguments being important, could someone let me know if there's any justification for this? I would guess it's more relevant in larger compile commands, but I don't know enough yet to understand this stuff.

Any insights appreciated,
Steve.

---

### Post by slavik on 2008-05-11
my guess is that compiling takes place before linking?

-L and -l flags are for the linker, -I and -i is for the compiler.

the compiler shifts the arguments out. and the parameters are not named. The only language that I know that does named arguments are scripts for AVIsynth. Perl6 is the only language that will have them (even though Perl5, Python and Ruby can already do this with hashes/dictionaries but this is more of a workaround).

---

