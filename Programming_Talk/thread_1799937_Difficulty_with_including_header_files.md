---
title: "Difficulty with including header files"
date: 2011-07-08
forum: Programming Talk
---

### Post by TheHimself on 2011-07-08
I'm trying to compile a C++ program on machine which has the library headers I need in /com/gsl/include/gsl/ . I've put the following line in my program
```
#include </com/gsl/include/gsl/gsl_matrix.h>
``` 

The compiler can find gsl_matrix.h but can't find the files gsl_matrix.h wants to include. I get errors:


/com/gsl/include/gsl/gsl_matrix.h:4:48: error: gsl/gsl_matrix_complex_long_double.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:5:43: error: gsl/gsl_matrix_complex_double.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:6:42: error: gsl/gsl_matrix_complex_float.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:8:40: error: gsl/gsl_matrix_long_double.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:9:35: error: gsl/gsl_matrix_double.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:10:34: error: gsl/gsl_matrix_float.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:12:34: error: gsl/gsl_matrix_ulong.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:13:33: error: gsl/gsl_matrix_long.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:15:33: error: gsl/gsl_matrix_uint.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:16:32: error: gsl/gsl_matrix_int.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:18:35: error: gsl/gsl_matrix_ushort.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:19:34: error: gsl/gsl_matrix_short.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:21:34: error: gsl/gsl_matrix_uchar.h: No such file or directory
/com/gsl/include/gsl/gsl_matrix.h:22:33: error: gsl/gsl_matrix_char.h: No such file or directory


The compiler is simply looking in the wrong place; albeit a little wrong. (I mean instead of gsl/gsl_matrix_complex_long_double.h it should look for gsl_matrix_complex_long_double.h) I've also tried "" instead of <> and got the same results.

---

### Post by Bachstelze on 2011-07-08
Do

#include <gsl/gsl_matrix.h>

and compile with -I/com/gsl/include/

---

### Post by TheHimself on 2011-07-08
Thank you very much! Could you now tell me how to do the linking? On my own machine I add ```
`pkg-config  --cflags  --libs  gsl`
``` to the g++ command but pkg-config on the new machine says that the library can't be found. The library is in  /com/gsl/lib/ .

---

### Post by Bachstelze on 2011-07-08
How ithe library file named? Assuming it's libgsl.a you would link with -L/com/gsl/lib/ and -lgsl.

---

