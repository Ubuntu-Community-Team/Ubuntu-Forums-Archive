---
title: "char pointer not returning as expected."
date: 2010-12-11
forum: Programming Talk
---

### Post by c2tarun on 2010-12-11
try this program
```
#include<stdio.h>

char *foo()
{
char result[100];
strcpy(result,"anything is good");
//printf("%s \n",result);  /*comment*/
return (result);
}

void main()
{
char *j;
j=foo();
printf("%s \n",j);
}
```output:
anything

remove comment double slashes and make the comment line active, new code will be

```
#include<stdio.h>

char *foo()
{
char result[100];
strcpy(result,"anything is good");
printf("%s \n",result);  /*comment*/
return (result);
}

void main()
{
char *j;
j=foo();
printf("%s \n",j);
}
```output:
anything is good
anything is good


can anyone explain me this strange behaviour please  :(

---

### Post by GeneralZod on 2010-12-11
You are returning a pointer to a local array, which is undefined behaviour.

---

### Post by c2tarun on 2010-12-11
> **GeneralZod said:**
> You are returning a pointer to a local array, which is undefined behaviour.

ya i accept this is an error.
but then y just by adding a printf in the foo function is changing the output?? and local variable is supposed to be destroyed as soon as function ends, then y am i getting any output??

---

### Post by GeneralZod on 2010-12-11
> **c2tarun said:**
> ya i accept this is an error.
but then y just by adding a printf in the foo function is changing the output?? and local variable is supposed to be destroyed as soon as function ends, then y am i getting any output??

"undefined behaviour" means it can do whatever it wants :)

Also, main with no argument should be declared as:

```

int main(void)

``` 

in C.

Please get into the habit of compiling with at least -Wall!

---

### Post by c2tarun on 2010-12-11
> **GeneralZod said:**
> "undefined behaviour" means it can do whatever it wants :)

Also, main with no argument should be declared as:

```

int main(void)

```in C.

Please get into the habit of compiling with at least -Wall!


thanks :D

one more help please.

look at the following code

```

[COLOR=#000000]void main()
{
  char *s[]={ "dharma","hewlett-packard","siemens","ibm"};
  char **p;
  p=s;
  printf("%s ",++*p);
  printf("%s ",*p++);
  printf("%s ",++*p);
}
```[/COLOR]

output:
harma harma ewlett-packard


can you please explain me why first characters are omitted??

---

### Post by GeneralZod on 2010-12-11
Fix the "main" declaration, please :)

```

  const char *s[]={ "dharma","hewlett-packard","siemens","ibm"};
  const char **p;
  p=s;
  printf("%s ",++*p);

```

So: s is an array of char pointers.  p is initially set to s.

s[0] points to the string literal, "dharma", s[1] to "hewlett-packared", etc.  s[0] + 0 is a pointer to the "d" in dharma; s[0] + 1 is a pointer to the "h" in dharma; etc.

*p is the same as p[0] which is s[0] (as p == s), which is a pointer to the string literal "dharma", as mentioned. ++*p increments this pointer, so that it is s[0] + 1 (as mentioned, a pointer to the "harma" part of the string literal) and returns the result, which is then printed: hence, "harma" is printed out.

---

### Post by c2tarun on 2010-12-11
> **GeneralZod said:**
> Fix the "main" declaration, please :)

```

  const char *s[]={ "dharma","hewlett-packard","siemens","ibm"};
  const char **p;
  p=s;
  printf("%s ",++*p);

```So: s is an array of char pointers.  p is initially set to s.

s[0] points to the string literal, "dharma", s[1] to "hewlett-packared", etc.  s[0] + 0 is a pointer to the "d" in dharma; s[0] + 1 is a pointer to the "h" in dharma; etc.

*p is the same as p[0] which is s[0] (as p == s), which is a pointer to the string literal "dharma", as mentioned. ++*p increments this pointer, so that it is s[0] + 1 (as mentioned, a pointer to the "harma" part of the string literal) and returns the result, which is then printed: hence, "harma" is printed out.


thanx a lot :)
and from next time i'll surely fix my main.

---

### Post by worksofcraft on 2010-12-11
IDK if it helps to understand what is actually happening with a function call, but I'll explain anyway:

Here is roughly how the function call stack works.
Note that depending on the implementation and hardware, some parameters and return results may be put in processor registers to make it more efficient.

```

... ^ Vacant space: nested function calls get pushed here
---> Stack pointer points here while running foo() 
	- local variables in function foo()
	- function return address
	- function's parameter values
... ^ The function foo()'s stack frame

	- space to store function result: is managed by the caller code main()
	- Local variables of main()
	- return address to leave main()
	- argv
	- argc
... ^ Function main()'s stack frame
	- space to receive the result of main
---> The bottom of your program's stack (possibly)

```

When you return from the foo() function, the Stack pointer is simply moved down to just above where the result is stored. That result is a pointer that you made point to the local variable on the foo() stack frame.

The data is probably still all there, but that memory will be reused by the very next function that you call and on some systems that can even be by an asynchronous interrupt service routine that you have no control over in your program.

---

### Post by c2tarun on 2010-12-11
> **worksofcraft said:**
> IDK if it helps to understand what is actually happening with a function call, but I'll explain anyway:

Here is roughly how the function call stack works.
Note that depending on the implementation and hardware, some parameters and return results may be put in processor registers to make it more efficient.

```

... ^ Vacant space: nested function calls get pushed here
---> Stack pointer points here while running foo() 
    - local variables in function foo()
    - function return address
    - function's parameter values
... ^ The function foo()'s stack frame

    - space to store function result: is managed by the caller code main()
    - Local variables of main()
    - return address to leave main()
    - argv
    - argc
... ^ Function main()'s stack frame
    - space to receive the result of main
---> The bottom of your program's stack (possibly)

```When you return from the foo() function, the Stack pointer is simply moved down to just above where the result is stored. That result is a pointer that you made point to the local variable on the foo() stack frame.

The data is probably still all there, but that memory will be reused by the very next function that you call and on some systems that can even be by an asynchronous interrupt service routine that you have no control over in your program.


wow... great
i never thought of processor register. and you are right, this may be the reason for getting one word. thanx :)

---

