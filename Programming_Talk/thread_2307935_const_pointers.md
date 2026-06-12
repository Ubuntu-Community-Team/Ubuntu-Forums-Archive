---
title: "const pointers"
date: 2015-12-29
forum: Programming Talk
---

### Post by jessCPP on 2015-12-29
Hi everyone!
 

 I have some doubts about const arrays and pointers in C.
 

 Given the following code
 

 ```

 #include <stdio.h>
 #include <stdlib.h>
 

 

 

 int main(int argc, char** argv)
 {
     const char array[] = "this is an array";
      
     //    array[0] = 'j';//error: assignment of read-only location ‘array[0]’
      
     char *p = (char*)array;//warning: initialization discards ‘const’ qualifier from pointer target type
 

     p[0] ='j';
     printf("array = %s\n",array);
     return (EXIT_SUCCESS);
 }
 
```
 

 If 'array' is declared as constant I can not change the array. But why can I use a pointer to the array 'p' and alter it the original array 'array'?
 

 Another question is that if I cast the assignation to the array
 

 ```

 char *p = (char*)array;
 
```
 

 The warning disappears. Why?
 

 Thank you all very much!

---

### Post by KemyLand on 2015-12-29
[B]This is undefined behaviour. The fact that it works is just an... eh... architectural detail. See below.

[/B]According ot the standards, this code...
```

const char array[] = "this is an array";

```
Declares a constant *array* of type *const char[17]*, that is an array of 17 constant characters. That means that you *can't* modify the array in standard code. However, your code is not 
standard compliant. It casts a *const char[]* to a *char* *in this line...
```

char *p = (char*)array;

```
The next line, the one that dereferences such a pointer, could perfectly crash the program, as well as explode the planet, just because it's _undefined_ behaviour.

Now, *why* this works? It happens that in both the x86 and x86-64 architectures, there's a area of memory known as the *stack*, where local variables are held. Because your array is a local variable, it's stored in the array. The stack is, well, a stack of variables. You can "push" variables in it, "pop" variables from it, and "peek" variables in it without poping. Because of this dynamic design, the operating system is unable to define which areas of the stack should *not* be written and which may be. So, the whole stack is both readable and writable. As a result, your program can run, and apparently succeed, thought it could perfectly have catched your RAM chip in fire, as far as the C standard is concerned ;).

BTW, could you please explain your second question? I couldn't understand it.

---

