---
title: "malloc() gives 4-bytes per float ?"
date: 2007-09-04
forum: Programming Talk
---

### Post by nss0000 on 2007-09-04
Gents:

Continuing my tutorial excursion thru K&R: I've encountered MALLOC() to my dismay... but at least I expected 8-bytes ( 16 on my x64 kit ??? ) per floating point value. I don't get it in the code below:

[code]
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

 /* ptr.c : 4.9.07 : pointer stuff */

main( int argc, char *argv[] )
{

long int i, j, n, m;
float *p, *q;
float temp;

  if ( argc != 3 )
   {
     printf("Enter two equal integers\n");
     exit(0);
    }

  n = atoi(argv[1]);
  m = atoi(argv[2]);
  printf("The commandline sez %d\t%d\n", n, m);

  p = malloc( n * sizeof(float) ); 
  q = malloc( m * sizeof(float) );
  printf("And the initial pointer values are %d\t%d\n\n", p, q);

  for( i=0; i<n; i++)
    {
     *(p+i) = (float)i + 0.1;
     *(q+i) = (float)i + 0.2;
    } 

  for (j=0; j<n; j++)
    {   
     temp = *(p+j) + *(q+j);
     printf("Calculating ..%ld\t%ld\t%f\t%f\t%f\n", p+j, q+j, *(p+j), *(q+j), temp);
    }

  free(p);
  free(q);

 return 0;
} 


My output looks like:

rayh@asusm2n:~/cprogs0$ ./ptr 3 3
The commandline sez 3   3
And the initial pointer values are 5246992      5247024

Calculating ..5246992   5247024 0.100000        0.200000        0.300000
Calculating ..5246996   5247028 1.100000        1.200000        2.300000
Calculating ..5247000   5247032 2.100000        2.200000        4.300000

Why am I getting only 4-bytes per float??

---

### Post by LaRoza on 2007-09-04
-EDIT Sorry, wrong answer...

(Use [ code ] tags, can't read your code! ([ php ] tags will give you syntax highlighting for C style langs.)

---

### Post by slavik on 2007-09-04
float is 4, double is 8. (on my system at least, 64bit pentium D with 32bit feisty.)

makes sense since double has double the precision of a float.

---

### Post by Compyx on 2007-09-04
> **nss0000 said:**
> Gents:

Continuing my tutorial excursion thru K&R: I've encountered MALLOC() to my dismay... but at least I expected 8-bytes ( 16 on my x64 kit ??? ) per floating point value. I don't get it in the code below:

```

#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

 /* ptr.c : 4.9.07 : pointer stuff */

main( int argc, char *argv[] )
{

```


Better be explicit:
```

int main(int argc, char *argv[])

```
Implicit int is bad style in C90 and a syntax error in C99. Your compiler should have warned you about this. Try invoking gcc with `-Wall -Wextra -ansi -pedantic -O2` and see what it tells you.

> 
```

long int i, j, n, m;
float *p, *q;
float temp;

  if ( argc != 3 )
   {
     printf("Enter two equal integers\n");
     exit(0);

```

0 is the portable code for 'no errors', better use `EXIT_FAILURE` if you want to signal an error and EXIT_SUCCESS if you want to signal success.
You can also use a `return` here since you're in main().

> 
```

    }

  n = atoi(argv[1]);
  m = atoi(argv[2]);
  printf("The commandline sez %d\t%d\n", n, m);

```

Why not use atol() (or better yet: strtol) since you declared `n` and `m` to be long.
Format specifier is wrong in the printf() call: use %ld for long.

> 
```

  p = malloc( n * sizeof(float) ); 
  q = malloc( m * sizeof(float) );

```

better:
```

  p = malloc(n * sizeof *p);

```
this way you can change the type pointed to by p without having to worry about rewriting this line. And remember to malloc()'s return value for NULL, it can fail.

> 
```

  printf("And the initial pointer values are %d\t%d\n\n", p, q);

```

Undefined behaviour: you pass a pointer-to-float to an int format specifier. Change `%d` to `%p` and cast p to void*:
```

  printf("And the initial pointer values are %p\t%p\n\n", (void *)p, (void *)q);

```

> 
```

  for( i=0; i<n; i++)
    {
     *(p+i) = (float)i + 0.1;
     *(q+i) = (float)i + 0.2;
    } 

  for (j=0; j<n; j++)
    {   
     temp = *(p+j) + *(q+j);
     printf("Calculating ..%ld\t%ld\t%f\t%f\t%f\n", p+j, q+j, *(p+j), *(q+j), temp);
    }

  free(p);
  free(q);

 return 0;
} 

```

My output looks like:

rayh@asusm2n:~/cprogs0$ ./ptr 3 3
The commandline sez 3   3
And the initial pointer values are 5246992      5247024

Calculating ..5246992   5247024 0.100000        0.200000        0.300000
Calculating ..5246996   5247028 1.100000        1.200000        2.300000
Calculating ..5247000   5247032 2.100000        2.200000        4.300000

Why am I getting only 4-bytes per float??

Because on your system a float is 4 bytes wide, if you need higher precision, use double or long double.

On my system (32-bits) float is 4 bytes, double is 8 and long double is 12. I haven't got an x64-system yet so I can't check what the sizes are on such a beast.

Oh, and why ask the user to enter the same number twice? Wouldn't it be easier just to ask for one number? ;)

---

### Post by nss0000 on 2007-09-04
BigC:

I appreciate your critique. One issue ... since a pointer is just a memory location ... hardware ...  then expressing such as a (long)integer seems quite natural.

Otherwise, It seems my assumption of 8-bytes per float was dead_wrong.

---

### Post by nss0000 on 2007-09-04
BigC:

Yep, the DOUBLE is 8-bytes :

rayh@asusm2n:~/cprogs0$ ./ptr 3 3
The commandline sez 3   3
And the initial pointer values are 5246992      5247024

Calculating ..5246992   5247024 0.100000        0.200000        0.300000
Calculating ..5247000   5247032 1.100000        1.200000        2.300000
Calculating ..5247008   5247040 2.100000        2.200000        4.300000

**BTW** I used two equal CLI inputs, because I was "fishing" for a reason to use the MALLOC() function at all. What I saw was that it can be used as "scratch-pad" space for bunches of "tweener' calculations that may be tossed after use. That's what the proggie does.

Thanks again for your comments.

---

### Post by Compyx on 2007-09-04
> **nss0000 said:**
> BigC:

Yep, the DOUBLE is 8-bytes :

rayh@asusm2n:~/cprogs0$ ./ptr 3 3
The commandline sez 3   3
And the initial pointer values are 5246992      5247024

Calculating ..5246992   5247024 0.100000        0.200000        0.300000
Calculating ..5247000   5247032 1.100000        1.200000        2.300000
Calculating ..5247008   5247040 2.100000        2.200000        4.300000

**BTW** I used two equal CLI inputs, because I was "fishing" for a reason to use the MALLOC() function at all. What I saw was that it can be used as "scratch-pad" space for bunches of "tweener' calculations that may be tossed after use. That's what the proggie does.

Thanks again for your comments.

You're welcome.
I already had an idea that the two numbers on the CLI where there for a reason.

C is a great programming language, my personal favorite. These days compilers are so good at optimization that they usually approach hand-coded assembly in terms of speed and sometimes even surpass hand-coded assembly.

Have fun coding!

---

### Post by nitro_n2o on 2007-09-04
data types sizes vary depends on cpu's thus you should always consult header files :) 
check out [http://www.opengroup.org/onlinepubs/009695399/basedefs/limits.h.html](http://www.opengroup.org/onlinepubs/009695399/basedefs/limits.h.html)
[http://www.opengroup.org/onlinepubs/009695399/basedefs/float.h.html](http://www.opengroup.org/onlinepubs/009695399/basedefs/float.h.html)
check the entries in wikipedia as well 
have fun :)

---

