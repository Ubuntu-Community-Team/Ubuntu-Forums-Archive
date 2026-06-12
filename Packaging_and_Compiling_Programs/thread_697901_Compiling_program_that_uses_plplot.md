---
title: "Compiling program that uses plplot"
date: 2008-02-15
forum: Packaging and Compiling Programs
---

### Post by browny254 on 2008-02-15
Hi, Im trying to compile some c++ code that uses a couple of functions of plplot but not sure exactly how to do it. 

I have included plplot.h at the beginning of my code (which i found a mention to in the documentation somewhere) and use -lplplot when i go to compile, but i get  error: plplot.h: No such file or directory.

Im not sure how im ment to do it correctly or if i have even installed the plplot libraries correctly (im still really new to this so i just ticked everything that mentioned plplot in the synaptic package manager...)


thanks for any help you can give.

---

### Post by hod139 on 2008-02-16
Make sure you install the -dev packages, and include as
```

#include <plplot.h>

```

---

### Post by browny254 on 2008-02-16
thanks for the reply,

i hadnt had any replies here so i posted this in the beginners thread and someone mentioned you need

```
#include <plplot/plplot.h>
```

instead of what you have there. thought i would let you or anyone else who looks at this know.

now im stuck at trying to compile it, im using 

```
$ g++ histoplot.cpp -lgsl -lgslcblas -lplplot -o histoplot
/usr/bin/ld: cannot find -lplplot
collect2: ld returned 1 exit status
```

while i here i might as well ask why you need -lgslcblas as well as -lgsl? how is it i can tell what i need to link to when im trying to compile?

---

### Post by hod139 on 2008-02-22
You can get the correct header and linker options by typing:
```

pkg-config --cflags plplotd
pkg-config --libs plplotd

```

Same thing works for gsl
```

 pkg-config --libs gsl

```
returns "-lgsl -lgslcblas -lm"

---

