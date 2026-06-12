---
title: "[SOLVED] Cannot compile archaic C++ code with gcc"
date: 2008-11-18
forum: Packaging and Compiling Programs
---

### Post by Trafferth on 2008-11-18
Hello all!

I have been given the task of resurrecting some old (written ca. 1991) general-purpose transition probability calculation code written in C++ in order to apply it to the study of energy level transitions in positronium, which we are currently undertaking in the physics department here in Swansea University.

Unfortunately, as the title of the thread suggests, the program will not compile with gcc (under Ubuntu 8.04), which is puzzling since it *will* compile under Windows (using an obsolescent version of Visual Studio).  

The code was written by a theorist, and so is a little ...difficult... to follow in the main body (the actual calculations).  The problem, however, seems to be in the first few simple lines of code, where the type declarations are made:

```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
/***************** NOTE ********************
* This source code is valid for IBM and VAX
* To compile it for either of them you must
* define ibm or vax, according to the system
* you suppose to use.
********************************************/
#define ibm /* vax */
double pi,csv,ln10;
double bpp,bss,dtp,dfrp,dfrs,frp,frs,dp,ds,dopp,hk;
double xsh,ysh,xstep,ystep;
double **y;
double ip,is;
int ie,iet;
double tp,ts;
int ns,np,nt,J1,J2,J3;
double w11,w22,w33,w12,w13,w23;
int m_prop,m_time;
int main(int,char **);
double **dalloc(int,int);
int shape_load(void);
double bpp_funk(double);
double y9(double,double,double);
double y9_evr(double,double,double,double,double);
double phy(int,int,int);
int data_load(void);
int erge(void);
int fre_field(void);
FILE *f12,*f8,*f10;
int main(argc,argv)
int argc;
char *argv[];
{
```

A compiler-type interrogation and lots of physics-related code then follow...

The error from the compiler is shown below:

```
ALEX.C:33: error: ‘int main’ redeclared as different kind of symbol
ALEX.C:21: error: previous declaration of ‘int main(int, char**)’
ALEX.C:33: error: ‘argc’ was not declared in this scope
ALEX.C:33: error: ‘argv’ was not declared in this scope
ALEX.C:35: error: storage size of ‘argv’ isn't known
ALEX.C:36: error: expected unqualified-id before ‘{’ token
```

The lines of code that seem to be giving the problem are therefore:

```
int main(int,char **);
int main(argc,argv)
int argc;
char *argv[];
{
```

etc...

Just in case it is important, I am running Ubuntu 8.04, using Geany as an editor, gcc as the compiler, and have installed the build-essentials package.  The code also fails to compile using MinGW under Windows XP SP3 - but I suppose since that MinGW wraps gcc that isn't so surprising.

Since I work almost exclusively with Linux and can compile most of my C++ programs just fine, I am a bit stumped.  I should point out, however, that I mostly program in Python and LabVIEW (I'm an experimentalist if you hadn't guessed :)), and I have only a basic working knowledge of C++, so I may well have missed something really obvious.  If anyone can spot what I'm doing wrong / what's missing / wrong in the code, I'd really appreciate it.

Cheers!

Trafferth :)

---

### Post by WW on 2008-11-18
Are you sure it is C++, and not just old C?

---

### Post by zwaardmeester on 2008-11-18
I would replace
```
int main(argc,argv)
int argc;
char *argv[];
{
```
by 
```
int main(int argc, const char * argv[]) {
```
and also tidy up the program a bit, make things indented etc. Then it's easier to see where things are missing. Good luck!

---

### Post by Trafferth on 2008-11-18
Thanks, everyone for the quick responses.  You are right, it is plain old C (the file has a .C extension) - there are some (later) files I have been given to handle ALEX.C (the simulation itself), and these are written in C++.

@zwaardmeester: I have tried your suggested substitution.  It all goes a bit weird when I do that - the compilation fails with the error message shown below:

```
ALEX.C: In function &#8216;int main(int, const char**)&#8217;:
ALEX.C:33: error: declaration of C function &#8216;int main(int, const char**)&#8217; conflicts with
ALEX.C:21: error: previous declaration &#8216;int main(int, char**)&#8217; here
ALEX.C: At global scope:
ALEX.C:91: error: &#8216;double** dalloc&#8217; redeclared as different kind of symbol
ALEX.C:22: error: previous declaration of &#8216;double** dalloc(int, int)&#8217;
ALEX.C:91: error: &#8216;N&#8217; was not declared in this scope
ALEX.C:91: error: &#8216;M&#8217; was not declared in this scope
ALEX.C:93: error: expected unqualified-id before &#8216;{&#8217; token
ALEX.C:130: error: &#8216;double bpp_funk&#8217; redeclared as different kind of symbol
ALEX.C:24: error: previous declaration of &#8216;double bpp_funk(double)&#8217;
ALEX.C:130: error: &#8216;x&#8217; was not declared in this scope
ALEX.C:137: error: expected unqualified-id before &#8216;{&#8217; token
```

So, it's all a bit puzzling - when I make the change, the problem appears to 'shift' to later in the program.  For reference (if it helps), the lines mentioned are:

```
int main(int,char **);
double **dalloc(int,int);

int main(int argc, const char * argv[]) {

double **dalloc(N,M)
int N,M;
{
}

{
extern double **y,tp;
}

double bpp_funk(x)
double bpp_funk(x)
double x;
{
}

}

```

Here I have omitted code that isn't complained about and have retained braces to show which scope each line appears in.

Bizarrely, if I write a new C source file with the original complained-about lines in it, it compiles without complaint.  The following code compiles just fine:

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main(int,char **);

int main(argc,argv)
int argc;
char *argv[];
{	
	return 0;
}
```

I'm getting more confused by the minute! :) Thanks for the suggestions - any ideas what's going on?

Thanks!

Trafferth :)

---

### Post by Trafferth on 2008-11-18
Hello again!

I have now got the code to compile - I renamed the file from 'ALEX.C' to 'alex.c' and then tried to compile it.  It had a whole bunch of 'unused variable' errors, which I corrected with judicious use of comments.  I.e. if 'double a,b,c' was present and only a and b referenced, I'd comment the line out and replace it with 'double a,b'.

So... the file will now compile, but the linker has a fit when I try to build the binary.  It spits out the following errors:

```
/tmp/ccAK0p6S.o: In function `main':
alex.c:(.text+0x108): undefined reference to `log'
/tmp/ccAK0p6S.o: In function `y9_evr':
alex.c:(.text+0x74e): undefined reference to `exp'
alex.c:(.text+0x7ee): undefined reference to `exp'
alex.c:(.text+0x86c): undefined reference to `exp'
alex.c:(.text+0x93a): undefined reference to `sqrt'
/tmp/ccAK0p6S.o: In function `phy':
alex.c:(.text+0x9aa): undefined reference to `sqrt'
alex.c:(.text+0xa4a): undefined reference to `sqrt'
/tmp/ccAK0p6S.o: In function `data_load':
alex.c:(.text+0x10b0): undefined reference to `exp'
alex.c:(.text+0x10cc): undefined reference to `exp'
alex.c:(.text+0x1114): undefined reference to `sqrt'
alex.c:(.text+0x1125): undefined reference to `sqrt'
alex.c:(.text+0x1136): undefined reference to `sqrt'
alex.c:(.text+0x115d): undefined reference to `sqrt'
collect2: ld returned 1 exit status
```

Would I be right in thinking that gcc cannot find the math.h header file?

The command I used to try to build alex.c is the following:

```
gcc -Wall "alex.c" -o "alex" 
```

If I rename alex.c to alex.cpp, then the compiler throws out the original compile errors on attempting to compile (it doesn't even get to the linking stage).

Very confusing.  I am hoping this linking problem is more easily solvable than the original set of errors...  Again, I am open to suggestions! :lolflag:

Thanks for looking into this, everyone - it's much appreciated!

Trafferth :)

---

### Post by WW on 2008-11-18
Add the option **-lm** to link the math library:
```

gcc -Wall alex.c -lm -o alex

```

---

### Post by Trafferth on 2008-11-18
WW,

You sir, are a gent.  It now compiles.  Thank you.  If I may ask, I tried looking with gcc --help for possible parameters I might have missed, but didn't see -lm anywhere.  What does the -lm parameter stand for (if it's 'link math' I might have to cry...)?

Again, thanks to everyone who helped me out here.  Appreciated.

Trafferth :)

---

### Post by WW on 2008-11-18
> **Trafferth said:**
>   If I may ask, I tried looking with gcc --help for possible parameters I might have missed, but didn't see -lm anywhere.  What does the -lm parameter stand for (if it's 'link math' I might have to cry...)?

Bascially, yeah, that's it.  Here's a tissue. :)

Libraries are generally linked with the option **-l***name*, where *name* identifies the library.  The math library happens to be called **m**.  Actually, the math library is singular; it is a standard library, but you still have to give the option.  Note that you don't have to give a -l option to use the standard IO library (printf, etc).  I don't know enough C history to explain why.

---

