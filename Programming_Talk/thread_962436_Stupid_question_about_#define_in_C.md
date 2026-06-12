---
title: "Stupid question about #define in C"
date: 2008-10-29
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-29
What is the point of #define in C?
```

#define VARIABLE 100

```
Couldn't it just be
```

int VARIABLE = 100;

```
That command is called after #include statements at the beginning
of the program, so the variable is global anyway. Why there is #define?

---

### Post by slavik on 2008-10-29
because #define is interpreted by the cpp (C Pre-Processor) and ends up being a text replacement before the compiler gets to the code, while the second code snippet is interpreted by the compiler and ends up being a compiled piece of code which reserves sizeof(int) space and an assignment operation.

not only that, but if you use VARIABLE as a constant in multiple locations, the resulting code will not have to do a symbol lookup to get the value.

#define is also the reason, why Bjarne put in the 'const' keyword (among other uses for it). const is available in C99.

EDIT: What you suggest can be done and will work but the underlying meaning is different.

EDIT2: #define can be used for conditional compilation ...
```

in some other header file for Windows stuff
#define WIN32

in your code
#ifdef WIN32
printf("This is windows\n");
#else
printf("This is NOT windows\n");
#endif

```

---

### Post by crazyfuturamanoob on 2008-10-29
> **slavik said:**
> because #define is interpreted by the cpp (C Pre-Processor) and ends up being a text replacement before the compiler gets to the code, while the second code snippet is interpreted by the compiler and ends up being a compiled piece of code which reserves sizeof(int) space and an assignment operation.

not only that, but if you use VARIABLE as a constant in multiple locations, the resulting code will not have to do a symbol lookup to get the value.

#define is also the reason, why Bjarne put in the 'const' keyword (among other uses for it). const is available in C99.

EDIT: What you suggest can be done and will work but the underlying meaning is different.

EDIT2: #define can be used for conditional compilation ...
```

in some other header file for Windows stuff
#define WIN32

in your code
#ifdef WIN32
printf("This is windows\n");
#else
printf("This is NOT windows\n");
#endif

```

Ok thanks.

---

### Post by cmay on 2008-10-29
you can also use #defines like this.

[PHP]
#include <stdio.h>
int i;
#define begin {
#define end }
#define writeln printf
#define program int main(){
#define loop for(i=0;i<=10;i++)	
	
  program 
   begin     
	    loop
          begin
      	    writeln("hello world\n");
	     end
	   end
	  return 0; 
  end[/PHP]

---

### Post by snova on 2008-10-29
Yes, but I think he's just interested in the usage of the C prepreprocessor, not trying to write an entry for the IOCCC. :)

The preprocessor has uses in conditional compilation, especially where otherwise the code would be invalid. Take platform-specific code as an example. There's no other way (besides messing with the build system) to prevent code for one OS from being compiled for another. Even if the compiler accepted it (big if), you'd get link errors...

---

### Post by orphean on 2008-10-29
> **cmay said:**
> you can also use #defines like this.

[PHP]
#include <stdio.h>
int i;
#define begin {
#define end }
#define writeln printf
#define program int main(){
#define loop for(i=0;i<=10;i++)	
	
  program 
   begin     
	    loop
          begin
      	    writeln("hello world\n");
	     end
	   end
	  return 0; 
  end[/PHP]

Keep your pascal out of my C!

---

### Post by dribeas on 2008-10-30
> **slavik said:**
> because #define is interpreted by the cpp (C Pre-Processor) and ends up being a text replacement before the compiler gets to the code, while the second code snippet is interpreted by the compiler and ends up being a compiled piece of code which reserves sizeof(int) space and an assignment operation.


+1

Also note that previous to C99 array sizes must be known at compile time:

```

// pre C99 code
#define SIZE 100
int size = 100;
void f()
{
   int array0[100]; /* Fine. */
   int array1[SIZE]; /* compiles perfectly, compiler sees: int array1[100]; */
   int array2[size]; /* fails to compile, array size must be known at compile time. */
}

```

Note that a variable and a #define are not interchangeable. Variables occupy an space, and you can get pointers into them, while #defines are just text substitutions that the precompiler performs. You cannot request the address of a define just as you cannot get the address of a number.

There are other uses of #define. Conditional compilation, as others posted, or macro definition:

```

#define MAX( x, y ) ((x) > (y) ? (x) : (y) )
void f()
{
   int x = MAX( 5, 8 );
/*   
Compiler sees:
   int x = ((5) > (8) ? (5) : (8));
*/
}

```

With all that means (macros can be a source of code errors).

---

### Post by crazyfuturamanoob on 2008-10-30
So sometimes it is a better idea to use a macro for a value than a variable, because a macro doesn't use any space from my RAM?

---

### Post by slavik on 2008-10-30
correct. please note "sometimes" ... it is really a case by case basis, depending on what you need this 'variable' for.

---

