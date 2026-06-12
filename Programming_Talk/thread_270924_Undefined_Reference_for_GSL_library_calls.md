---
title: "Undefined Reference for GSL library calls"
date: 2006-10-03
forum: Programming Talk
---

### Post by Juanito on 2006-10-03
Hey guys,

I'm in a bit of a time-bind, so I thought I'd ask here after spending 2 hours scouring the internet for an answer.

I am using the GNU Science Library

[http://www.gnu.org/software/gsl/manual/html_node/Compiling-and-Linking.html#Compiling-and-Linking](http://www.gnu.org/software/gsl/manual/html_node/Compiling-and-Linking.html#Compiling-and-Linking)

After including the proper header files
#include <gsl/gsl_rng.h>
#include <gsl/gsl_randist.h>


After pressing Build in KDevelop or Anjuta, I'm getting errors like...

undefined reference to `gsl_ran_multinomial'

From what I've read, it's something about linking? I'm used to good ol' java and visual studio, so I have no clue what to do.

Thanks for your patience!

---

### Post by hod139 on 2006-10-04
You are correct, it is a linking issue.  I'm not sure how to specify external libraries in Kdevelop or Anjunta, but on the command line you would do this:

```
gcc myfile.c -lgsl
```

the "-l" flag tells gcc to link against the gsl library.  You will need to tell an IDE to also link against gsl.

You most likely will also want -lm (the math lib).

---

### Post by jwilley44 on 2008-06-05
Hello, I had the same problem. I tried compiling with -lgsl and I got a bunch of errors. The errors were of the form:

/usr/lib/gcc/x86 64-linux-gnu/4.2.3/../../../../lib/libgsl.so undefined refernce to `cblas_csyrk' 

with the last part between the ` and the ' varying.

Thanks in advance

---

### Post by WW on 2008-06-05
The best way to get the correct arguments to link the GSL library is with the pkg-config command:
```

$ pkg-config --libs gsl

```
That will print the options required to link the GSL library.  You can also use the --cflags option to get the correct compiler options:
```

$ pkg-config --cflags gsl

```
(That may just print a blank line, meaning no special options are required, since the header files are in a standard directory.)

To compile and link a program that is contained in a single C file that uses GSL:
```

$ gcc myprogram.c `pkg-config --cflags --libs gsl` -o myprogram

```
Or, to compile and then link,
```

$ gcc -c myprogram.c `pkg-config --cflags gsl`
$ gcc myprogram.o `pkg-config --libs gsl` -o myprogram

```

I don't use KDevelop or Anjuta, but I am sure there is a standard way to tell them to use the required compiler options.

---

### Post by abhinandkr on 2009-06-17
Yes it works!
And, you can simply create a shell file to execute that compile and link statement. Give the o/p file as a.out if required.

---

### Post by unadulterated on 2012-07-10
I am facing linking issues when attempting to use GSL_MATRIX_ALLOC. I am working on 12.04 Ubuntu, it used to work fine on 11.10 but I started working with it couple of days back and now its not working. I am presenting a smaller problem. I tried all I could locate on the internet and this post.

```

#include <stdio.h>
#include <gsl/gsl_matrix.h>

int
main (void)
{
 int i, j;
 gsl_matrix * m = gsl_matrix_alloc (10, 3);
 return 0;
}

```

$ gsl-config --cflags --libs
-I/usr/include
-L/usr/lib -lgsl -lgslcblas -lm


$ g++ -I/usr/include -L/usr/local/lib -o -lm -lgsl -lgslcblas test_gsl.c
/tmp/ccRY8yhP.o: In function `main':
test_gsl.c:(.text+0x19): undefined reference to `gsl_matrix_alloc'
collect2: ld returned 1 exit status

$ gcc -o 'gsl-config --cflags --libs' test_gsl.c
/tmp/cccAiyFb.o: In function `main':
test_gsl.c:(.text+0x19): undefined reference to `gsl_matrix_alloc'
collect2: ld returned 1 exit status


$ gcc -o 'pkg-config --cflags --libs gsl' test_gsl.c
/tmp/ccfGM3QF.o: In function `main':
test_gsl.c:(.text+0x19): undefined reference to `gsl_matrix_alloc'
collect2: ld returned 1 exit status


The GSL library is not getting linked for some reason. Please help me and let me know what I am doing wrong as such?

Also, '-c' option works fine.

---

### Post by SevenMachines on 2012-07-11
Best to open a new thread rather than resurrect long dead ones but, as far as your problems go.. 
* -o specifies output filename, so you'd want something like 
```
-o test_gsl
```
*  'gsl-config --cflags --libs' needs backquotes, not quotes, 
```
`gsl-config --cflags --libs`
```
* Linking libraries need to be added after the object files these days, not before otherwise you'll get a whole lot of undefined things (see many many threads on 'as-needed' linking)

So, your compilation line should look something like
```
$ g++ -o test_gsl test_gsl.c `gsl-config --cflags --libs`
```

---

### Post by unadulterated on 2012-07-11
Thanks that helped.. the ordering of where the test_gsl.c was mentioned also mattered. Good to know that. Thanks.

---

