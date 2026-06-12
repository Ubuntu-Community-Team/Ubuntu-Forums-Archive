---
title: "What is a static variable-function?"
date: 2011-07-20
forum: Programming Talk
---

### Post by stamatiou on 2011-07-20
What does that static mean before variables and functions in C?

---

### Post by Bachstelze on 2011-07-20
It means that the object or function in question will behave like a global variable, but only in the translation unit (source file, function or block) in which it was declared. In particular, its lifetime will be the lifetime of the program. Take for example this program:

```
#include <stdio.h>

static int n = 2;

void f(void)
{
        static int m = 0;
        printf("%d\n", m);
        m++;
        n++;
}

int main(void)
{
        f();
        f();
        printf("%d\n", n);
        return 0;
}

```

m and n are both declared static, meaning that they will both exist from the moment they are declared to the moment the program terminates. The difference is that n is declared outside any function or block, meaning that it will be accessible from anywhere in the source file, which is why we can access is both from f and main. m however is declared inside f, so it can only be accessed from inside f (if I tried to access it from inside main, I woudl get an error). The program's output is

```
0
1
4
```

Notice how m kept its value between the two calls to f, that's what we mean when we say that its lifetime is the lifetime of the program.

For functions it's the same thing, but since a function doesn't really have a value, it doesn't make a lot of sense to view them as "global". The main purpose of the static keyword fonr functions is to make them visible only to other functions in the same source file (so the static keywords restricts the visibility of function, whereas it may expand it for variables).

---

### Post by stamatiou on 2011-07-20
> **Bachstelze said:**
> It means that the object or function in question will behave like a global variable, but only in the translation unit (source file, function or block) in which it was declared. In particular, its lifetime will be the lifetime of the program. Take for example this program:

```
#include <stdio.h>

static int n = 2;

void f(void)
{
        static int m = 0;
        printf("%d\n", m);
        m++;
        n++;
}

int main(void)
{
        f();
        f();
        printf("%d\n", n);
        return 0;
}

```m and n are both declared static, meaning that they will both exist from the moment they are declared to the moment the program terminates. The difference is that n is declared outside any function or block, meaning that it will be accessible from anywhere in the source file, which is why we can access is both from f and main. m however is declared inside f, so it can only be accessed from inside f (if I tried to access it from inside main, I woudl get an error). The program's output is

```
0
1
4
```Notice how m kept its value between the two calls to f, that's what we mean when we say that its lifetime is the lifetime of the program.

For functions it's the same thing, but since a function doesn't really have a value, it doesn't make a lot of sense to view them as "global". The main purpose of the static keyword fonr functions is to make them visible only to other functions in the same source file (so the static keywords restricts the visibility of function, whereas it may expand it for variables).
So the static variable is a global variable but it is accesible only in the specific .c file?

---

### Post by 1clue on 2011-07-20
Are you talking about c or some other language?

---

### Post by Bachstelze on 2011-07-20
> **stamatiou said:**
> So the static variable is a global variable but it is accesible only in the specific .c file?

It is accessible only *in the translation unit in which it was declared*. If it is declared outside any function or block, it means the .c file, but if it is declared inside a function or block, it means that function or block.

---

### Post by Bachstelze on 2011-07-20
> **1clue said:**
> Are you talking about c or some other language?

> **stamatiou said:**
> What does that static mean before variables and functions **in C**?

:o

---

### Post by stamatiou on 2011-07-20
> **Bachstelze said:**
> It is accessible only *in the translation unit in which it was declared*. If it is declared outside any function or block, it means the .c file, but if it is declared inside a function or block, it means that function or block.
1.And what does it mean for functions, all of the functions are declared out of other functions
2.What is the difference between declaring a normal variable in a function, in both cases it is editable only in the function and in global I can edit it everywhere

---

### Post by Bachstelze on 2011-07-20
> **stamatiou said:**
> 1.And what does it mean for functions, all of the functions are declared out of other functions
2.What is the difference between declaring a normal variable in a function, in both cases it is editable only in the function and in global I can edit it everywhere

Did you actually read what I wrote?

1. The main purpose of static functions is to make them accessible only from the same source file.
2. The difference is that a static variable will continue to live after the function in which it is declared has returned, and will keep its value between function calls.

```
firas@aoba ~ % cat test.c                                        
#include <stdio.h>

void f(void)
{
        static int n = 0;
        int m = 0; /* not static */
        printf("%d\n", n);
        printf("%d\n", m);
        n++;
        m++;
}

int main(void)
{
        for (int i=0; i<5; i++) {
                printf("%dth passage in the loop:\n", i);
                f();
        }
        return 0;
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@aoba ~ % ./test                                            
0th passage in the loop:
0
0
1th passage in the loop:
1
0
2th passage in the loop:
2
0
3th passage in the loop:
3
0
4th passage in the loop:
4
0

```

---

### Post by stamatiou on 2011-07-20
> **Bachstelze said:**
> Did you actually read what I wrote?

1. The main purpose of static functions is to make them accessible only from the same source file.
2. The difference is that a static variable will continue to live after the function in which it is declared has returned, and will keep its value between function calls.

```
firas@aoba ~ % cat test.c                                        
#include <stdio.h>

void f(void)
{
        static int n = 0;
        int m = 0; /* not static */
        printf("%d\n", n);
        printf("%d\n", m);
        n++;
        m++;
}

int main(void)
{
        for (int i=0; i<5; i++) {
                printf("%dth passage in the loop:\n", i);
                f();
        }
        return 0;
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@aoba ~ % ./test                                            
0th passage in the loop:
0
0
1th passage in the loop:
1
0
2th passage in the loop:
2
0
3th passage in the loop:
3
0
4th passage in the loop:
4
0

```
1.And the global functions can be accesed from other .c files in the same folder?
2.So it is something like creating a variable inside a function and I can print it from other functions?

---

### Post by Bachstelze on 2011-07-20
> **stamatiou said:**
> 1.And the global functions can be accesed from other .c files in the same folder?

There is no such thing as "global functions", or if you prefer, functions are global by default, it means they can be accessed from any program that links the object file or library in which the function is located.

> 2.So it is something like creating a variable inside a function and I can print it from other functions?

No. Declaring a variable static does not change its visibility. If you declare a static variable in a function, you can still not access it from other functions. The variable will continue to live after the functionhas retured, but that doesn't mean you can always access it, it means that the variable will still be there when you enter that function again, and will have kept its value.

---

### Post by johnl on 2011-07-20
You need to de-couple the idea of "static lifetime" and "static linkage."  

Confusingly, in C, you use the same keyword (static) for both of them.

As previously mentioned,

```

int f(void) {
    static int n = 0;
    return n++;
}

```

means that **n** persists across the lifetime of the program, instead of being automatically created and destroyed as it goes into/out of scope.   This is **static lifetime**.

However, when you apply **static** to a variable or function at global scope:

```

static int n = 32768;

static int foo(void) {
    return 12;
}

```

You are specifying **static linkage**, which means that the variable or function is visible only within the current translation unit (i.e. source file).


If you try to access that function or variable from a different source file, you will run into an error at link-time.

---

### Post by JupiterV2 on 2011-07-20
This is one of the more difficult topics in C to wrap your head around. I, for the longest time, struggled to understand why and when static variables and functions should be used.

First, I'll discuss static variables because that's what you asked about. Good examples have already been provided but I'll give you a comparison of three techniques and, hopefully, explain their uses and drawbacks:

1. Global Variable
```
#include <stdio.h>

int num = 0;

void 
add_one_to_num(void)
{
  num++; /* synonymous with num += 1 and num = num + 1 */
}

int
main (void)
{
  printf ("num = %d\n", num);
  add_one_to_num();
  printf ("num = %d\n", num);

  return 0;
}
```

Declaring a variable as global allows it to be accessed anywhere within the file its defined. It can, by use of extern, also be accessed anywhere in the program the file is build into. This can lead, as you might imagine, into some dangerous territory. It can be changed anywhere, at any time. The beauty of it, though, is that it retains its value the entire time the program is run. Global variables are typically frowned upon and should be avoided but there are some situations where the only real solution is to use one.

2. Passing Local variable by Reference
```
#include <stdio.h>

void 
add_one_to_num(int *num)
{
  (*num)++;
}

int
main (void)
{
  int num = 0;

  printf ("num = %d\n", num);
  add_one_to_num(&num);
  printf ("num = %d\n", num);

  return 0;
}
```

Same result but now you have pointers flying everywhere. What if you could combine the best of both worlds?

3. Static Variable
```
#include <stdio.h>

int 
add_one_to_num(void)
{
  static int num = 0;
  return ++num;
}

int
main (void)
{
  printf ("num = %d\n", add_one_to_num());
  printf ("num = %d\n", add_one_to_num());

  return 0;
}
```

Much simpler! The value of num is retained for the entire duration of the program and no pointers are required.

The same somewhat applies to functions. A function is global by default. If you declare a function prototype at the top of your source file, any other function within that source can access it. If you place that prototype into a header file, the function can be accessed by any function which #include's it. A function declared as static is no different than a function whose prototype is only at the top of a source (.c) file and not in a header. It is only accessible within that source file. However, it signals to you, other coders, and the compiler that it will only be accessible within the scope of that file and not anywhere else. It's a useful distinction even if it has limited utility.

---

### Post by Bachstelze on 2011-07-21
> **JupiterV2 said:**
> 
The same somewhat applies to functions. A function is global by default. If you declare a function prototype at the top of your source file, any other function within that source can access it. If you place that prototype into a header file, the function can be accessed by any function which #include's it. A function declared as static is no different than a function whose prototype is only at the top of a source (.c) file and not in a header. It is only accessible within that source file. However, it signals to you, other coders, and the compiler that it will only be accessible within the scope of that file and not anywhere else. It's a useful distinction even if it has limited utility.

You misunderstood. static for functions refers to static *linking*, it means the function cannot be linked to functions in other object files to form an executable. If I have a file fact.c like this:

```
int fact(int n)
{
        int res = 1;
        for (int i=2; i<=n; i++) {
                res *= i;
        }
        return res;
}

```

and a file main.c like this:

```
#include <stdio.h>

int main(void)
{
        int n;
        n = fact(5);
        printf("%d\n", n);
        return 0;
}

```

I can do

```
firas@aoba ~ % cc -std=c99 -c fact.c   
firas@aoba ~ % cc -std=c99 -c main.c 
main.c: In function &#8216;main&#8217;:
main.c:6: warning: implicit declaration of function &#8216;fact&#8217;
firas@aoba ~ % cc -o fact fact.o main.o
firas@aoba ~ % ./fact 
120

```

And I will get a warning but it will work. However, if I make the function static in fact.c, it will not work:

```
firas@aoba ~ % cat fact.c 
static int fact(int n)
{
        int res = 1;
        for (int i=2; i<=n; i++) {
                res *= i;
        }
        return res;
}

firas@aoba ~ % cc -std=c99 -Wall -c fact.c
fact.c:2: warning: &#8216;fact&#8217; defined but not used
firas@aoba ~ % cc -o fact fact.o main.o   
Undefined symbols:
  "_fact", referenced from:
      _main in main.o
ld: symbol(s) not found
collect2: ld returned 1 exit status

```

Notice the warning at compilation. Since I declared the function static, the compiler expected me to use it in the same .c file (since it can't be used anywhere else).

---

### Post by JupiterV2 on 2011-07-21
> **Bachstelze said:**
> You misunderstood. static for functions refers to static *linking*, it means the function cannot be linked to functions in other object files to form an executable. If I have a file fact.c like this:

```
int fact(int n)
{
        int res = 1;
        for (int i=2; i<=n; i++) {
                res *= i;
        }
        return res;
}

```

and a file main.c like this:

```
#include <stdio.h>

int main(void)
{
        int n;
        n = fact(5);
        printf("%d\n", n);
        return 0;
}

```

I can do

```
firas@aoba ~ % cc -std=c99 -c fact.c   
firas@aoba ~ % cc -std=c99 -c main.c 
main.c: In function &#8216;main&#8217;:
main.c:6: warning: implicit declaration of function &#8216;fact&#8217;
firas@aoba ~ % cc -o fact fact.o main.o
firas@aoba ~ % ./fact 
120

```

And I will get a warning but it will work. However, if I make the function static in fact.c, it will not work:

...

Without looking up the C standard, I would hazard a guess that this is a result of undefined behavior. GCC may allow it to work but I'm not sure that all compilers would, nor if it should. Hense, why there's a warning. The static keyword doesn't give the compiler a choice, it has to enforce the rules whereas it's up to the compiler implementation to decide how to handle the other case.

---

### Post by Bachstelze on 2011-07-21
> **JupiterV2 said:**
> Without looking up the C standard, I would hazard a guess that this is a result of undefined behavior. 

Looking up the C standard, I would hazard a guess that you are wrong, but whatever. You totally missed the point. Add a prototype if you want, and it will be the same.

```
firas@aoba ~ % cat fact.c
int fact(int n)
{
        int res = 1;
        for (int i=2; i<=n; i++) {
                res *= i;
        }
        return res;
}
firas@aoba ~ % cat main.c                                   
#include <stdio.h>

int fact(int);

int main(void)
{
        int n;
        n = fact(5);
        printf("%d\n", n);
        return 0;
}
firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -c fact.c
firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -c main.c 
firas@aoba ~ % cc -o fact fact.o main.o 
firas@aoba ~ % ./fact 
120

```

But

```
firas@aoba ~ % cat fact.c                                   
static int fact(int n)
{
        int res = 1;
        for (int i=2; i<=n; i++) {
                res *= i;
        }
        return res;
}
firas@aoba ~ % cc -std=c99 -pedantic -Wall -c fact.c 
fact.c:2: warning: &#8216;fact&#8217; defined but not used
firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -c main.c
firas@aoba ~ % cc -o fact fact.o main.o                     
Undefined symbols:
  "_fact", referenced from:
      _main in main.o
ld: symbol(s) not found
collect2: ld returned 1 exit status

```

---

### Post by mokrates on 2011-07-21
C-Standard or no, static declared functions and variables at file-level ('global') will already be linked by the compiler, meaning the symbols aren't there in the object file (.o). So the linker later just cannot link to it, because there is no link destination.
static linkage is, by the way, the wrong word also: static linking is exactly what you do with non-static declared functions, taking two .o's and resolving the symbols, so that the pointers in the executable are static and fast.
Opposed to that is *dynamic linking* which incurs later when the executable is actually executed. Dynamic linking is what happens, when the .so's or under windows the .dll's are linked to the program
Static linking is what happens when you link the program (with the linker, 'ld', which *cannot* see 'static' declared funktions)
static-declared functions are already linked by the compiler, and you don't actually call that linking at all

---

### Post by Bachstelze on 2011-07-21
> **mokrates said:**
> 
static linkage is, by the way, the wrong word also: static linking is exactly what you do with non-static declared functions, taking two .o's and resolving the symbols, so that the pointers in the executable are static and fast.

Yes, my bad. The C standard says "internal linkage", which is a more accurate description of what happens.

> 6.2.2 Linkages of identifiers

3. If the declaration of a file scope identifier for an object or a function contains the storage class specifier [font=monospace]static[/font], the identifier has *internal linkage*.

But the fact remains that functions declared static differ from those that are not in a fundamental way.

---

### Post by mokrates on 2011-07-21
> **Bachstelze said:**
> 
But the fact remains that functions declared static differ from those that are not in a fundamental way.
Yessir, indeed they do! :biggrin:

---

### Post by JupiterV2 on 2011-07-21
> **Bachstelze said:**
> Looking up the C standard, I would hazard a guess that you are wrong, but whatever. You totally missed the point. Add a prototype if you want, and it will be the same.

I'm curious then, that if I missed the point why would the compiler issue a warning on the behaviour:
```
main.c:6: warning: implicit declaration of function ‘fact’
``` It is telling you that what you are doing could prove problematic. From the GCC manual:

-Wimplicit-function-declaration (C and Objective-C only)
Give a warning whenever a function is used before being declared. In C99 mode (-std=c99 or -std=gnu99), this warning is enabled by default and it is made into an error by -pedantic-errors. This warning is also enabled by -Wall.

The C99 standard does define that, if a function has no storage class specifier (like static, or extern) it is assumed to be extern. 

From C99 ISO/IEC 9899:TC2 Section 6.2.2:
>  If the declaration of an identi&#64257;er for a function has no storage-class speci&#64257;er, its linkage
is determined exactly as if it were declared with the storage-class speci&#64257;er extern. If
the declaration of an identi&#64257;er for an object has &#64257;le scope and no storage-class speci&#64257;er,
its linkage is external

I'm agreeing with that. At no point did I argue that it wasn't true. More than likely we are arguing the same point but not understanding each other. The end result, which I think we are all on agreement with is:

1) A function which is not declared static has external scope when linked.
2) A function which has been declared static has only file scope and can only be accessed from within that file.
3) While a function which has been declared non-static has global/extern scope, it's declaration should be within a header which ought to be #include'd into other files which would use it. Otherwise, the compiler will warn you that the behavior may not be what you want (though likely will be).

I guess what I'm trying to say is, I think it's generally accepted that if you want to use a function outside of the file its been defined/implemented in, you should place its declaration within a header file.

---

### Post by Bachstelze on 2011-07-21
> **JupiterV2 said:**
> I'm curious then, that if I missed the point why would the compiler issue a warning on the behaviour:
```
main.c:6: warning: implicit declaration of function &#8216;fact&#8217;
``` It is telling you that what you are doing could prove problematic.

You once again missed the point. My point was that functions declared static and extern (the default) are fundamentally different, not "almost the same", as you made it sound for example in:

> **JupiterV2 said:**
> A function declared as static is no different than a function whose prototype is only at the top of a source (.c) file and not in a header.

I omitted the prototype in main.c to make the point even clearer but I guess I shouldn't have. The fact that a non-static function can be linked from another file at all *even if it's terrible practice* (which we all agree it is) to me makes a lot of difference from one that cannot be linked.

> **JupiterV2 said:**
> I'm curious then, that if I missed the point why would the compiler issue a warning on the behaviour:
```
main.c:6: warning: implicit declaration of function &#8216;fact&#8217;
``` It is telling you that what you are doing could prove problematic. From the GCC manual:

-Wimplicit-function-declaration (C and Objective-C only)
Give a warning whenever a function is used before being declared. In C99 mode (-std=c99 or -std=gnu99), this warning is enabled by default and it is made into an error by -pedantic-errors. This warning is also enabled by -Wall.

Yes, yes, I agree with all that. Still, I find nothing in the standard that states that if a function with no prototype is calles *and* the parameter with which it is called match what is expected in its definition, the resulting behavior is undefined. There is no technical reason why it should be: the caller will pass the parameters, and the callee will get the parameters it expects and happily do its job. The warning to me just says "Hey dude y u no put a prototype? It's not like it would kill you, and then I could tell you if your parameters don't match, but whatever..."

---

### Post by JupiterV2 on 2011-07-21
I get what you're saying now. What I was trying to say in my comment about them being "almost the same" was that by placing a function prototype at the top of a source file the function may be called without compiler warnings anywhere within the scope of the file, just as it would be if declared static. I wasn't picking up on your point about how the function would be, by default, considered extern and accessible within other files too whereas the static version wouldn't. Glad we're finally on the same page! =)

Now, the question is, does the OP get it now?

---

### Post by Bachstelze on 2011-07-21
> **JupiterV2 said:**
> What I was trying to say in my comment about them being "almost the same" was that by placing a function prototype at the top of a source file the function may be called without compiler warnings anywhere within the scope of the file, just as it would be if declared static.

Oh but if the function is static you don't get a compiler warning, you get a linker error. But of course since you should always compile with -Werror, the result is the same: no binary. ;)

Yes, kids, I'm serious here, always compile -pedantic -Wall -Werror (unless you're arguing on a forum). That way, no "who cares about the warnings, it still works!" Warnings are here for a reason, and they're bad. You don't deserve your binary until you have eliminated them.

---

### Post by mokrates on 2011-07-21
calling a function without a prototype may be undefined, as argument coercion cannot take place correctly (as to the unknown destination types). Gets even more interesting with c++, where the prototype is needed to decide, if a parameter is a call by reference or call by value.

---

### Post by nvteighen on 2011-07-22
> **Bachstelze said:**
> 
Yes, kids, I'm serious here, always compile -pedantic -Wall -Werror (unless you're arguing on a forum). That way, no "who cares about the warnings, it still works!" Warnings are here for a reason, and they're bad. You don't deserve your binary until you have eliminated them.

I can think of many FOSS projects, some major ones, that leave warnings unsolved...

---

### Post by mokrates on 2011-07-22
For kids, that is correct, for adults, and c expects you to be one, you just should know, what the warning means.
There are old C-idioms, which provoke warnings with current compilers... so. ...
(like: if (!(f=fopen())) { ... )
Just know what you do.
And bear in mind, that C is by no means a language which is defined absolutely down to the bottom of execution. far from it.

---

### Post by Arndt on 2011-07-23
> **mokrates said:**
> For kids, that is correct, for adults, and c expects you to be one, you just should know, what the warning means.
There are old C-idioms, which provoke warnings with current compilers... so. ...
(like: if (!(f=fopen())) { ... )


fopen ought to have arguments, but omitting them is hardly an idiom. What warning do you have in mind?

---

### Post by mokrates on 2011-07-23
'scuse me. I did it all wrong but nevermind the arguments, that's nothing to do with what i was getting at.
i meant an indiom like
```

if (f=fopen(...)) {
  ... d sth with the open file f
}

```
You will get a warning, that you probably mean '==' in the if-condition and not '=' which you actually meant.
And yes, there are people, who argue, that the above idiom is bad practise. others say, it's an idiom, get over it.

---

### Post by Arndt on 2011-07-23
> **mokrates said:**
> 'scuse me. I did it all wrong but nevermind the arguments, that's nothing to do with what i was getting at.
i meant an indiom like
```

if (f=fopen(...)) {
  ... d sth with the open file f
}

```
You will get a warning, that you probably mean '==' in the if-condition and not '=' which you actually meant.
And yes, there are people, who argue, that the above idiom is bad practise. others say, it's an idiom, get over it.

I see what you mean now. If you want to write that way, but dislike the warning, you can turn off the warning, or evade it by using an extra set of parentheses. At least for gcc.

---

### Post by mokrates on 2011-07-23
> **Arndt said:**
> I see what you mean now. If you want to write that way, but dislike the warning, you can turn off the warning, or evade it by using an extra set of parentheses. At least for gcc.
Exactly my point.

---

