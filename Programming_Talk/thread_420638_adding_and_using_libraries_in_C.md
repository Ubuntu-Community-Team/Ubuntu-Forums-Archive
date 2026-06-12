---
title: "adding and using libraries in C"
date: 2007-04-23
forum: Programming Talk
---

### Post by raequin on 2007-04-23
I downloaded gsl-1.9.tar.gz and extracted it to a folder in which I have a c project I'm working on.  In that project, I need to solve for the roots of quartic polynomials; hence gsl.  Now a bit of background: I know nearly nothing about headers, makefiles, libraries, etc.  I can write enough C to be able to do what I want when I'm using the standard libraries, but now I need help.

So, first of all I need to get my program to compile on my computer, but eventually I will need to be able to give it to my professor and be able to have it run on his computer.  I have to assume he does not have the gsl library.

Firstly, I have the following lines in my program:

     #include "./gsl-1.9/gsl/gsl_poly.h"

and in the file, "./gsl-1.9/gsl/gsl_poly.h" I changed the following line:

     #include <gsl/gsl_complex.h>

to:

     #include "./gsl_complex.h"

Now this seems pretty awkward.  Is there another way that I should be doing this?

When I write the following command in terminal:

     gcc -Wall -lm engine.c

I get this message:

     /tmp/ccQJAR3M.o: In function `main':engine.c:(.text+0x3b): undefined reference to
     `gsl_poly_complex_workspace_alloc'
     :engine.c:(.text+0x62): undefined reference to `gsl_poly_complex_solve'
     :engine.c:(.text+0x6d): undefined reference to `gsl_poly_complex_workspace_free'
     collect2: ld returned 1 exit status

The code, engine.c, is something I just copied off the gsl reference manual.  Here's engine.c:

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include "./gsl-1.9/gsl/gsl_poly.h"
#include "./engine.h"

int main() {
  int i;
  /* coefficients of P(x) =  -1 + x^5  */
  double a[6] = { -1, 0, 0, 0, 0, 1 };  
  double z[10];
     
  gsl_poly_complex_workspace * w = gsl_poly_complex_workspace_alloc (6);
  gsl_poly_complex_solve (a, 6, w, z);
  gsl_poly_complex_workspace_free (w);
     
  for (i = 0; i < 5; i++)
    {
      printf ("z%d = %+.18f %+.18f\n", i, z[2*i], z[2*i+1]);
    }
     
  return 0;
}

So can you tell me where I'm going wrong with this library work?  Also, but not so pressing right now: how will I be able to make this project portable?  Thanks.

---

### Post by wmcbrine on 2007-04-23
> **raequin said:**
> Firstly, I have the following lines in my program:

     #include "./gsl-1.9/gsl/gsl_poly.h"

and in the file, "./gsl-1.9/gsl/gsl_poly.h" I changed the following line:

     #include <gsl/gsl_complex.h>

to:

     #include "./gsl_complex.h"

Now this seems pretty awkward.  Is there another way that I should be doing this?Yes -- use the "-I" directive to specify additional paths to search:

     gcc -I ./gsl etc.

Then you don't need to edit the source.

> [i]When I write the following command in terminal:

     gcc -Wall -lm engine.c[/i]You're not linking to gsl anywhere there. It needs its own "-l" (ell, not to be confused with the "-I" (eye) above), or you can specify the full path to the library. If you use the "-l" form, you're going to have to specify the directory anyway, via "-L".

As an alternative to all this, you could add the libgsl0 and libgsl0-dev packages via synaptic or apt-get. Then you wouldn't have to muck with the paths. Of course, that doesn't help you get it running on your professor's system. Knowing nothing about the parameters of your assignment, I can't really address that. I guess you should ask the prof if it's OK to use gsl and, if so, how to handle it?

---

### Post by Wybiral on 2007-04-23
The library should have some type of binary that you need to link with when compiling.

Maybe it will have object files like ".o", in that case you need to compile with:

gcc someobject.o someotherobject.o -Wall -lm engine.c

Just add the object file to the compile command and C will link it to your program.

But more likely the library comes with an actual library file. This will probably be a "lib*.a" file. If so, then you use...

gcc -l(INSET LIBRARY NAME HERE) -Wall -lm engine.c

The library name is the lib*.a file without the "lib" or ".a". So if it's libBLAH.a, then use "-lBLAH" when you compile.

EDIT:

Looks like wmcbrine beat me to it, lol.

---

### Post by raequin on 2007-04-23
Well I reverted the source back to its original: #include <gsl/gsl_complex.h> but can't remember what command options I used with gcc when I tried to compile it.  Anyway, I couldn't get that to help, so I used synaptic package manager to add the libgsl0 and libgsl0-dev packages.  Then I changed a line in "engine.c" to read #include <gsl/gsl_poly.h> and used this command in the terminal:

     gcc -lgsl -Wall -lm engine.c

but then I got a bunch of lines like this:

/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libgsl.so: undefined reference to `cblas_dsdot'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libgsl.so: undefined reference to `cblas_dswap'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libgsl.so: undefined reference to `cblas_zaxpy'

So, what am I missing with the packages I added?  I really appreciate your help.  It's just that I don't understand what's going on here.  It's like now I know how my mom feels when I try to tell her over the phone how to download attachments or something.

EDIT:

I forgot to mention that I removed all gsl function calls from "engine.c."  Most recently, I even removed the line including "gsl_poly.h." and I can't compile it if I include the option "-lgsl" in the gcc command.  I get all those lines I just referenced above.  Seems to me like something is wrong with my libgsl installation.

EDIT(2):

At your prompting I contacted my prof and apparently his computer has the gsl library, so I guess portability is not an issue.

---

### Post by slavik on 2007-04-24
seems like gsl is dependent on some other library ... search synaptic for cblas for any clues.

---

### Post by WW on 2007-04-24
GSL requires the BLAS library; it provides its own version, but you still have to give it the library name when you link.  So, add the option **-lgslcblas** to your command.

That is, try this:
```

gcc -Wall engine.c  -lgsl -lgslcblas -lm -o engine

```
That command will call the executable file "engine" instead of the default "a.out".

If you have your copy of the GSL library installed in a nonstandard location, you can use the -I and -L options.  If, for example, you installed GSL in /opt/gsl-1.9, you could do this:
```

gcc -Wall -I/opt/gsl-1.9/include  engine.c  -L/opt/gsl-1.9/lib -lgsl -lgslcblas -lm -o engine

```
By the way, with this version of engine.c,
```

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <gsl/gsl_poly.h>

int main()
    {
    int i;
    /* coefficients of P(x) = -1 + x^5 */
    double a[6] = { -1, 0, 0, 0, 0, 1 };
    double z[10];

    gsl_poly_complex_workspace * w = gsl_poly_complex_workspace_alloc (6);
    gsl_poly_complex_solve (a, 6, w, z);
    gsl_poly_complex_workspace_free (w);

    for (i = 0; i < 5; i++)
        {
        printf ("z%d = %+.18f %+.18f\n", i, z[2*i], z[2*i+1]);
        }

    return 0;
    }

```
I can compile this with the first gcc command that I gave above (I have the Ubuntu GSL package installed):
```

$ gcc -Wall engine.c -lgsl -lgslcblas -lm -o engine
$ ./engine
z0 = -0.809016994374947451 +0.587785252292473137
z1 = -0.809016994374947451 -0.587785252292473137
z2 = +0.309016994374947451 +0.951056516295153642
z3 = +0.309016994374947451 -0.951056516295153642
z4 = +1.000000000000000222 +0.000000000000000000
$

```

---

### Post by raequin on 2007-04-24
It works now on my computer.  I can't thank you enough for all your help and your instruction.  So maybe I'll buy you some creamer for your Ubuntu.

---

### Post by raequin on 2007-05-07
As I said earlier, I know very little about libraries.  So do I need to uninstall the gsl library that I installed into my project folder?  I mean do I need to uninstall it or can I just delete it.  I don't need it since I installed the package using Synaptic.

---

### Post by thethawav on 2007-05-09
As long as you have the ubuntu provided package installed you can delete them

---

