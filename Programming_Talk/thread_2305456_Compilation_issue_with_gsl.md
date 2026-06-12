---
title: "Compilation issue with gsl"
date: 2015-12-06
forum: Programming Talk
---

### Post by amd3 on 2015-12-06
Hello,

I have a compilation problem. I need to first solve an implicit non-linear equation and then to find the eigenvalues of a non symmetric matrix. The top of my code includes those libraries :
```

 #include <gsl/gsl_vector.h>
#include <gsl/gsl_multiroots.h>
#include <gsl/gsl_math.h>
#include <gsl/gsl_eigen.h

```

In a first place when I was only using the gsl_vector and the gsl_multiroots I used to compile with the line :
```

gcc my_program.c `pkg-config --cflags --libs gsl` -o my_program

```

But when I do that I now get from the terminal : 
```

/tmp/ccmeqXCQ.o: dans la fonction « main »:
stab_bis.c:(.text+0xcb3): référence indéfinie vers « gsl_eigen_non_symmv_free »
collect2: error: ld returned 1 exit status

```

If any one has an idea it would be great to let me know !

Merci ! Thanks ! Grazie ! Gracias !

---

### Post by steeldriver on 2015-12-06
Hello and welcome to the forums

Are you sure you are using the correct function name in your call? A quick search of the lib suggests it should be [SIZE=3][FONT=courier new]gsl_eigen_**nonsymmv**_free[/FONT] [/SIZE]instead of [SIZE=3][FONT=courier new]gsl_eigen_**non_symmv**_free[/FONT][/SIZE]

---

### Post by amd3 on 2015-12-06
I think you are right it seems to work ! Sorry I didn't see my mistake...

---

