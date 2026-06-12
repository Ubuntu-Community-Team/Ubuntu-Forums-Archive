---
title: "change one line, get a compile error"
date: 2013-08-15
forum: Programming Talk
---

### Post by George Heine on 2013-08-15
The following program, "main_good.c",
```
#include <stdio.h>
#include <math.h>

int main ()
{
        double p = 3.14159265;
//        double s = sin(p/4.0);
        double s= sin(3.14159265/4.0);
        printf ("sin  is %f\n", s);
}
```
compiles under gcc without problems (and produces the correct answer).

But the following code, "main_bad.c",
```
#include <stdio.h>
#include <math.h>

int main ()
{
        double p = 3.14159265;
        double s = sin(p/4.0);
//        double s= sin(3.14159265/4.0);
        printf ("sin  is %f\n", s);
}
```Produces rhw error:
```
/tmp/cc819Wha.o: In function `main':
main_bad.c:(.text+0x23): undefined reference to `sin'
collect2: ld returned 1 exit status
```

Following a suggestion in this [thread ]("http://ubuntuforums.org/showthread.php?t=2144356"), tried compiling with the -lm switch.  Same error.

Can anyone explian what is happening ?
Hopefullly something simple; haven't programmed in plain old C for a long time.
thanks for any help -

---

### Post by QIII on 2013-08-15
Just for giggles and grins ...

What happens if you do something like this...

```
        .
double p = 3.14159265;
double q = 4.0;
double r = p/q;
double s = sin(r);
```

or 

```
        .
double p = 3.14159265;
double q = 4.0;
double s = sin(p/q);
```

(... and I'll not get into a discussion about the naming of your variables ... ;))

---

### Post by steeldriver on 2013-08-15
Where exactly are you adding the -lm? please post your exact compile command (the position of the library relative to the source file matters)

Probably what is happening is that when you do

```
double s= sin(3.14159265/4.0);
```

the compiler is optimizing it out (i.e. the compiler itself is evaluating the 'sin' function, and replacing the function call with a constant - so that no external linkage to libm is needed)

When you do

```
double s= sin(p/4.0);
```

then the compiler can't do that because the argument contains a variable (it would be interesting to see what happens if you declare p as const double).

---

### Post by dwhitney67 on 2013-08-15
> **George Heine said:**
> 
Following a suggestion in this [thread ]("http://ubuntuforums.org/showthread.php?t=2144356"), tried compiling with the -lm switch.  Same error.


Really??  Please show how you compiled the program, for I have my doubts.

---

### Post by trent.josephsen on 2013-08-15
I defer to steeldriver's explanation.

The reason people are asking about the command line you used to compile it is because compilers can be notoriously finicky about the order of arguments, especially when it comes to linking.

```
$ cc -lm foo.c  # may not work depending on what cc is
$ cc foo.c -lm  # the "correct" way
```
Me, I can never remember which order things are supposed to go in, especially when you throw a "-o foo" in the mix, so I like to rely on make to remember it for me:
```
$ LDLIBS="-lm" make foo
```

This has the added advantage of also recognizing the CFLAGS variable, which I define in my .zshrc as below (you'll also notice I use clang instead of gcc):
```
$ export CFLAGS="-std=c11 -Wall -Wextra -pedantic -Wwrite-strings"
$ export LDLIBS="-lm"
$ make foo
clang -std=c11 -Wall -Wextra -pedantic -Wwrite-strings    foo.c  -lm -o foo
```

Obviously when you go beyond simple programs it's time to write a real Makefile, but this saves me typing on a regular basis, because I never compile anything without lots of warnings enabled. It's a good habit to be in.

---

### Post by ofnuts on 2013-08-17
Incidentally, math.h defines:
```

# define M_PI        3.14159265358979323846    /* pi */
# define M_PI_2        1.57079632679489661923    /* pi/2 */
# define M_PI_4        0.78539816339744830962    /* pi/4 */

```

(and also the long forms)

---

### Post by George Heine on 2013-08-22
Thanks for all the informative responses.

Following suggestions from trent.josephsen and dwhitney67, tried recompiling with
```
gcc main_bad.c -lm
``` And it works, with no problems.  So apparently the order of the flags was the issue.
Will experiment with suggestions of  trent.josephsen's for using "make" rather than calling gcc directly.

Thanks also to Steeldriver for some insights on why the problem occurred in the first place.
I will try the suggestions of QIII on some different methods of declaration, and report back if 
anything interesting turns up.

Of course, the real goal is to understand what is going on.  Can anyone recommend
a good source of information (other than the voluminous man pages) that could help
with figuring out the gcc command-line syntax?

---

### Post by trent.josephsen on 2013-08-22
> **George Heine said:**
> Of course, the real goal is to understand what is going on.  Can anyone recommend
a good source of information (other than the voluminous man pages) that could help
with figuring out the gcc command-line syntax?

Nope. Sorry.

I believe the special case regarding placement of -lfoo predates gcc, and it has something to do with the order in which symbols are made available for linkage, but if it makes sense to anybody, that somebody is not me. AFAIK the man pages are your only real recourse. Yes, the man page for gcc is over 17,000 lines long, but you can search it, so it's usually not too hard to find something you're looking for. I don't know of any other reliable resource that goes beyond "gcc -o bar bar.c -lfoo" in complexity.

---

### Post by steeldriver on 2013-08-22
I've been meaning to follow up on why libm is not required (and therefore why the placement of the -lm doesn't matter) when you change the line to a constant expression that can be evaluated at compile time

You can kind of see how this happens if you use the -S option to stop compilation at the assembler stage, and then look for what function calls are present the assembly file. So for example if we have the original non-constant version:

```

$ cat sin1.c
#include <stdio.h>
#include <math.h>

int main()
{
  double p = 3.1415926;
  double v;

**  v = sin(p/4.0);**
  printf("%lf\n", v);

  return 0;
}

```

then

```
 
$ gcc -S sin1.c
$ 
$ grep 'call' sin1.s
    call    sin
    call    printf
$ 

```

but if we replace the sin argument by a constant expression: 

```

$ cat sin2.c
#include <stdio.h>
#include <math.h>

int main()
{
  double p = 3.1415926;
  double v;

**  v = sin(3.1415926/4.0);**
  printf("%lf\n", v);

  return 0;
}

```

then

```

$ gcc -S sin2.c
$ 
$ grep 'call' sin2.s
    call    printf
$ 

```

Hope this helps

---

### Post by Bachstelze on 2013-08-23
> **George Heine said:**
> 
Of course, the real goal is to understand what is going on.  Can anyone recommend
a good source of information (other than the voluminous man pages) that could help
with figuring out the gcc command-line syntax?

For this particular issue only. I am by no means an expert on compilers, but here is (my understanding of) what's happening. The first thing to remember is that the source files and libraries are processed in the order they appear onthe command like.

Good: [font=monospace]gcc -o foo foo.c -lm[/font]

What happens is that the compiler first processes the file [font=monospace]foo.c[/font]. It sees that there is a call to the [font=monospace]sin()[/font] function. Since the code of the function is not provided in the file, the compiler will make some kind of internal note that the code of the function [font=monospace]sin()[/font] is needed, and to get it from a subsequent file or library that provides it.

Bad: [font=monospace]gcc -o foo -lm foo.c[/font]

Based on the above it's easy to guess what happens. First the compiler processes the [font=monospace]libm[/font] library. Since there is no pending memo that the code of some function is needed, it will conclude that the library is not needed and carry on. The reason this syntax works on some (most?) systems is that when the compiler processes a library, it will keep track of all the functions that this library provides, in case a subsequent file needs it. Aside from the obvious drawback of having to keep all those memos around (especially if there is a lot of libraries in use), I do not know of any other reason to prefer the "new" behavior (but then again, I am not an expert).

---

### Post by George Heine on 2013-08-23
Thanks to steeldriver for a good explanation of why the compiler doesn't need to include a call to libm when evaluating the sine of a constant.
Thansk also to Bachstelze for some insights on why the order of command-line switches might be important.

Repeated steeldriver's experiment with Qlll's two examples:
 
```
$ cat sin3vars.c
#include <stdio.h>
#include <math.h>

int main ()
{
double p = 3.14159265;
double q = 4.0;
double s = sin(p/q);
printf ("sin  is %f\n", s);
}
$ gcc -S sin3vars.c
$ grep call sin3vars.s
    call    sin
    call    printf
```


And with other variants, including 
```
#def PI 3.14159625
...
double s = sin(PI/4.0);
printf ("sin  is %f\n", s);

```
with similar results:  if the compiler sees something it can resolve as a constant, no call to the sin function is included.

Marking this thread as "solved", but further discussion, especially on the command-line syntax, would not be unwelcome.

---

### Post by steeldriver on 2013-08-23
Once thing I forgot to mention is that declaring p as const doesn't seem to make any immediate difference i.e.

```

const double p = 3.14159265;
.
.
double s = sin(p/4.0);
printf ("sin  is %f\n", s);

```

still calls 'sin'. However adding any level of optimization to the command line (-O1 or -O2 or -O3) even without an explicit const declaration does:

```

gcc -S sin1.c
$ grep 'call' sin1.s
        call    sin
        call    printf
$
$ gcc -O1 -S sin1.c
$ grep 'call' sin1.s
        call    __printf_chk
$

```

---

### Post by Bachstelze on 2013-08-24
> **George Heine said:**
> 
Marking this thread as "solved", but further discussion, especially on the command-line syntax, would not be unwelcome.

Well, what else do you want to know?

---

