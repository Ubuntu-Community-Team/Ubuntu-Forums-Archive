---
title: "arpack libarary example file won't compile"
date: 2010-03-24
forum: Programming Talk
---

### Post by abraxas334 on 2010-03-24
I am trying to compile an example file from arpack++, which is a set of linear algebra routines.
I installed it using synaptic, assuming dependencies will be taken care of. It requires lapack and blas which i believe i have both installed. 
But if i try and run the rest probgram with test makefile i get a long list of errors:
I am compling using their preshipped makefile
 ```
g++ -g -fhandle-exceptions -DSUN4 -I/home/antonia/arpack++/include  -c symsimp.cc

```
The errors go on for ever and i can't make them be piped to a file so here a selection of them:
```

/usr/include/arpackf.h:32: error: ‘debug’ was not declared in this scope
/usr/include/arpackf.h:32: error: ‘_’ was not declared in this scope
/usr/include/arpackf.h:37: error: variable or field ‘name2’ declared void
/usr/include/arpackf.h:37: error: ‘dsaupd’ was not declared in this scope
/usr/include/arpackf.h:37: error: ‘_’ was not declared in this scope
/usr/include/arpackf.h:43: error: variable or field ‘name2’ declared void
/usr/include/arpackf.h:43: error: ‘dseupd’ was not declared in this scope
/usr/include/arpackf.h:43: error: ‘_’ was not declared in this scope

```
and
```

/usr/include/blas1c.h:185: error: ‘name2’ cannot be used as a function
/usr/include/blas1c.h: In function ‘void scal(const integer&, float&, float*, const integer&)’:
/usr/include/blas1c.h:191: error: ‘sscal’ was not declared in this scope
/usr/include/blas1c.h:191: error: ‘_’ was not declared in this scope

```

and 

```

/usr/include/arpackf.h:43: error: ‘_’ was not declared in this scope
/usr/include/arpackf.h:54: error: variable or field ‘name2’ declared void
/usr/include/arpackf.h:54: error: ‘dnaupd’ was not declared in this scope
/usr/include/arpackf.h:54: error: ‘_’ was not declared in this scope
/usr/include/arpackf.h:60: error: variable or field ‘name2’ declared void
/usr/include/arpackf.h:60: error: ‘dneupd’ was not declared in this scope
/usr/include/arpackf.h:60: error: ‘_’ was not declared in this scope
/usr/include/arpackf.h:73: error: variable or field ‘name2’ declared void
/usr/include/arpackf.h:73: error: ‘ssaupd’ was not declared in this scope
/usr/include/arpackf.h:73: error: ‘_’ was not declared in this scope

```

any idea what they could mean. Basically they go on for ever and to my knowledge everything should be installed. So I am guessing I am linking wrong

---

### Post by johnl on 2010-03-24
Hi, 

> 
The errors go on for ever and i can't make them be piped to a file so here a selection of them:


Try compiling with &> compile.log, e.g.:

```

g++ -g -fhandle-exceptions -DSUN4 -I/home/antonia/arpack++/include  -c symsimp.cc &> compile.log

```

Errors are printed to stderr, not stdout, so just doing "> compile.log" will not catch errors.

It's possible that the very first error is a missing header or similar which is causing the rest of the errors. 

> 
any idea what they could mean. Basically they go on for ever and to my knowledge everything should be installed. So I am guessing I am linking wrong


This is definitely a problem when compiling, not linking.  

Hope this helps.

---

### Post by abraxas334 on 2010-03-25
Hi this worked like magic!
> Try compiling with &> compile.log, e.g.:
But I am still having errors, but I think i managed to get down to it.

For the example program to run, it is required to include blas1c.h, which includes fine, but blas1c.h includes arch.h and arch.h requires a file called generic.h, which does not seem to exist on my system. What does this file do? Does anyone know? Can I work around it somehow without having to poke around these library files too much? I don't really understand them and I thought the idea behind oo is that you don't have to poke around in the intestines of what I am trying to run! I just wanted work out Eigenvalues of a large matrix. How hard can this be!
Any thoughts on this would be greatly appreciated!

---

### Post by abraxas334 on 2010-03-25
Well it is all solved. Apparenlty the version i am using is very old (2000) and it doesn't like the 4.+ gnu compiler.
But there is a patch and even a ubuntu site which i missed:
[https://help.ubuntu.com/community/Arpack%2B%2B]("https://help.ubuntu.com/community/Arpack%2B%2B")

---

