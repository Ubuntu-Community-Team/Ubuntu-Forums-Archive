---
title: "[SOLVED] Cannot compile header files...  Simple mistake?"
date: 2008-10-16
forum: Programming Talk
---

### Post by lamikins on 2008-10-16
Hallo,
I've been trying to debug this for several hours and have made zero progress...  

**PROBLEM SUMMARY**
Trying unsuccessfully to compile a header file "numerical_resipes.h" (a chunk of Numerical Recipes in C) to feed prototypes to an int main() { ... } type file.  


**PROGRAMME STRUCTURE**
Structurally, my intention is to 

//  filename:  "energy.c"

#include "numerical_recipes.h"
#include "eigenfinder.c" //  this is an external void function that utilises the numerical recipes (to determine eigenvalues, obviously).

int main () {

//  calls functions w/in eigenfinder and uses numerical recipes

}


Oddly, the above energy.c file WILL compile and run (I haven't yet verified the accuracy of the output), and yet -

neither eigenfinder.c NOR numerical_recipes.h compile independently

**COMPILE ERRORS**

Trying to compile numrec.h with a (definately working) makefile:

~/Quantum_Spin_Chains$ make numrec

gcc -c numrec.c
gcc -W -Wall -o numrec numrec.o -L/usr/X11R6/lib -lX11 -lcpgplot -lpgplot -lpng -lz
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [numrec] Error 1

Trying to compile eigenfinder.c also gives errors, but I suspect these will be largely resolved if I can fix numrec.h!!!

I realise this compile error is usually associated with a missing main() function, but it seems to me that this prerequisite has been met...

I'm hoping the solution is simple and that I'm just not seeing it...  can anyone help? 

Cheers

---

### Post by nvteighen on 2008-10-16
A question: does eigenfinder.c also have a main()? That error can also mean that there's a duplicate reference that confuses the linker and therefore, it's undefined.

But also, you better never #include a source code file. You just need to include declarations without code from header files and the linker will do the rest.

Consider this stupid example:
```

[color=#408080]*/* hello.c */*[/color]
[color=#BC7A00]#include <stdio.h>
[/color]
[color=#B00040]void[/color] [color=#0000FF]hello[/color]([color=#B00040]void[/color])
{
    [color=#408080]*/* Defining hello() */*[/color]

    printf([color=#BA2121]"Hello from hello.c!"[/color]);
}

```

```

[color=#408080]*/* hello.h - Header file for hello.c */*[/color]

[color=#B00040]void[/color] hello([color=#B00040]void[/color]); [color=#408080]*/* Just declaring. No definition. */*[/color]

```

```

[color=#408080]*/* main.c */*[/color]
[color=#BC7A00]#include "hello.h" [/color][color=#408080]*/* Use quotes. < > is for system-wide headers. */*[/color][color=#BC7A00]
[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color]([color=#B00040]void[/color])
{
    hello();

    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

As you see, I never include the source file, but just the header. Then, I can compile using something like this:
```

gcc -c main.c hello.c -Wall

```

And I get main.o and hello.o. After that, to link them together into a program called "myapp":
```

gcc -o myapp main.o hello.o -Wall

```

So, in your case, you should 1) delete any main() outside your main module 2) create a header file for eigenfinder.c, call it eigenfinder.h, where only declarations can be found, not "code". 3) Include eigenfinder**.h** into energy.c.

---

### Post by lamikins on 2008-10-16
Thanks, that was a really good explanation of header file usage.

To answer your question, eigenfinder is a void function.

I wasn't sure that I wanted to render eigenfinder purely in declarations, so what I've done is this:

[INDENT]*  I have a header file #include "numerical_recipes.h" [/INDENT]
[INDENT]*  I have simply incorporated eigenfinder into energy.c as follows:[/INDENT]



/***  energy.c  ******/

#include.....  
#include.....  // just the various relevant includes



#include "numerical_recipes.h"  //  numrec is called 1st to 'feed' eigenfinder (requires it's prototypes)

/***  the following WAS eigenfinder.c  *********/




void eigenfinder(float **M, float *d, int N)
{   
	int i;
	float **zz = matrix(1,N,1,N);
	float *e = vector(1,N);
	
  	tred2(M,N,d,e);
  	tqli(d,e,N,zz);

	free_vector(e,1,N);
	free_matrix(zz,1,N,1,N);
}

/*******************************/

int main()
{   

//  eigenfinder is called
//  various numerical recipe prototypes are called

}


What I'm finding NOW is that energy.c compiles and runs, but still when i try to "compile" numerical_recipes.h, the same compile error throws up just as before...

Is it a nonsense to attempt to compile a .h file in this context?

Thanks again for your explanation of headers!

---

### Post by nvteighen on 2008-10-16
Erm... you never compile header files. They're just pasted to the source code where you're #include'ing them and compiled with it... They're not code, but just a help for the compiler (because of how C compilers work...).

Could you please show the contents of numrec.h and/or numerical_recipes.h?

---

### Post by lamikins on 2008-10-16
Ahh.  See, I thought this may have been the case.  Bakachan.  

numrec.h  (the actual filename...  I posted as numerical_recipes for clarity  - which has obviously backfired) is structured as follows:

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <stddef.h>

#define NR_END 1
#define FREE_ARG char*

/************************************************************************************/

void	tred2(float **a, int n, float d[], float e[]);
void	tqli(float d[], float e[], int n, float **z);
float	pythag(float a, float b);

void	nrerror(char error_text[]);
float	*vector(long nl, long nh);
int		*ivector(long nl, long nh);
unsigned char *cvector(long nl, long nh);
unsigned long *lvector(long nl, long nh);
double	*dvector(long nl, long nh);
float	**matrix(long nrl, long nrh, long ncl, long nch);
double	**dmatrix(long nrl, long nrh, long ncl, long nch);
int		**imatrix(long nrl, long nrh, long ncl, long nch);
float	**submatrix(float **a, long oldrl, long oldrh, long oldcl, long oldch, long newrl, long newcl);
float	**convert_matrix(float *a, long nrl, long nrh, long ncl, long nch);
float	***f3tensor(long nrl, long nrh, long ncl, long nch, long ndl, long ndh);
void	free_vector(float *v, long nl, long nh);
void 	free_ivector(int *v, long nl, long nh);
void 	free_cvector(unsigned char *v, long nl, long nh);
void 	free_lvector(unsigned long *v, long nl, long nh);
void 	free_dvector(double *v, long nl, long nh);
void 	free_matrix(float **m, long nrl, long nrh, long ncl, long nch);
void 	free_dmatrix(double **m, long nrl, long nrh, long ncl, long nch);
void 	free_imatrix(int **m, long nrl, long nrh, long ncl, long nch);
void 	free_submatrix(float **b, long nrl, long nrh, long ncl, long nch);
void 	free_convert_matrix(float **b, long nrl, long nrh, long ncl, long nch);
void 	free_f3tensor(float ***t, long nrl, long nrh, long ncl, long nch, long ndl, long ndh);

#define SWAP(a,b) tempr=(a);(a)=(b);(b)=tempr
#define SIGN(a,b) ((b) >= 0.0 ? fabs(a) : -fabs(a))
static double sqrarg;
#define SQR(a) ((sqrarg=(a)) == 0.0 ? 0.0 : sqrarg*sqrarg)
static double cubearg;
#define CUBE(a) ((cubearg=(a)) == 0.0 ? 0.0 : cubearg*cubearg*cubearg)

/************************************************************************************/
/*	Householder reduction of a real, symetric matrix a[1..n][1..n]. On output, a
	is replaced by the orthogonal matrix Q effecting the transformation. d[1..n]
	returns the diagonal elements of the tridiagonal matrix, and e[1..n] the off-
	diagnal elements, with e[1]=0. This is the corrected version.
*/
void tred2(float **a, int n, float d[], float e[])
{
  //  a whole stack of code

}

//  now there are several more functions....

..............


(it's about 600 lines of code).

Now, I can foresee you admonishing me for #include'ing a header file with code embedded...   the file was originally sent to me as a .c, and the syntax for the include was 

#include "numrec.c"

I am anticipating that I should return to this format (or perhaps scrap it entirely!)...

---

### Post by lamikins on 2008-10-16
PS I need all these functions so i can perform block diagonalisation on a Hamiltonian and solve for energy eigenstates, but I certainly don't want to have the numrec prototypes in the main body of my code.

---

### Post by nvteighen on 2008-10-16
It's a trivial fix. Separate the functions from the rest and put them into a file called numrec.c which includes numrec.h (this may sound silly, but as the header has some macros, not doing this can break everything as you need to expand them).

Then, where you need access to those functions, just do #include "numrec.h"... 

And check the Makefile to see numrec**.c**, energy.c, eigenfinder.c, (other .c) are compiled and linked together.

---

### Post by lamikins on 2008-10-16
Thank you so much!  

Trivial if you know what you're doing, and easy to fix.  
Trivial if you **don't** know what you're doing - pain in the **** to fix.  

I'll have to do a stack of work before I know if this runs smoothly, but i'm guessing it will.

Thanks again.

---

### Post by dwhitney67 on 2008-10-16
Generally, header files (.h) are used for declaring (defining) functions.  It is in the implementation files (.c) where these functions are actually... you guessed it... implemented.  The function definitions and the implementation of such must match; otherwise, if not, you are defining two different functions (apples vs. oranges come to mind).

When dealing with a multiple modules (.c) project, you need to compile each of the implementation files (that is the .c files) to form an executable.  If all has been written well, there will not be any compile errors, much less any "unresolved" errors.

The preceding two paragraphs will not mean much to the newbie or to the casual C (or C++!) programmer, but with experience you will understand the nuances of the GCC compiler better than the front/back of your underwear.

---

### Post by nvteighen on 2008-10-16
> **lamikins said:**
> Thank you so much!  

Trivial if you know what you're doing, and easy to fix.  
Trivial if you **don't** know what you're doing - pain in the **** to fix.  

I'll have to do a stack of work before I know if this runs smoothly, but i'm guessing it will.

Thanks again.
Glad to hear that.

And don't forget to mark the thread as solved! (Thread Tools -> Mark as solved).

---

