---
title: "question in extern"
date: 2012-11-01
forum: Programming Talk
---

### Post by IAMTubby on 2012-11-01
Hey,
I have been trying hard to understand the extern keyword. I have read up about the difference between declaration and definition. But somehow, I keep getting stuck.

Please have a look at the following 3 files (Please don't mind the file names, I have files of the same name, but I have put only code which would help me understand the concept in these files.
```

/* File1 : main.c */
#include <stdio.h>
int main(void)
{
 TestFunction();

}

/*  File2 : objtable.c */
#include <stdio.h>
int a = 109;
int fun()
{
 printf("\nThis is a random function");
}


/* File3 : testfunction.c */
#include <stdio.h>
int a;

int TestFunction()
{
 printf("\nInside testfunction.c, value of a == %d",a);

}

```

I'm compiling the application as : *$gcc main.c objtable.c testfunction.c* 
**I have a few questions**
**1.**Yes, I am getting the output. But how ? 
I am **_defining_** the int a; variable twice in the application, and that's not allowed right ? From what I have read, you can declare as many times as you please, but definitions should be done only once.

**2.**
Assume, my file3, ie testfunction.c was to look as below
```

/* File3 : testfunction.c */
#include <stdio.h>
extern int a;

int TestFunction()
{
 printf("\nInside testfunction.c, value of a == %d",a);

}

```
How does it work again ? Because main.c calls testfunction.c and nowhere so far have you told that the definition for a variable called a exists in another file called objtable.c. I understand that extern int a; in testfunction.c is to extend the scope, but it gives me a feeling like we are printing without defining it, but with only it's declaration.(Code hasn't seen the definition yet).  

3)Why do you need the extern keyword when the same output was got in 1 without adding any extern ?

4)One last question

Assume, I give the int a; in the file objtable.c inside the function.
```

/*  File2 : objtable.c */
#include <stdio.h>
int fun()
{
 int a = 109;
 printf("\nThis is a random function");
}

/*  File3 : testfunction.c */
#include <stdio.h>
extern int a;
int TestFunction()
{
 printf("\nInside testfunction.c, value of a == %d",a);
}

```
Now, I'm not able to access the variable within testfunction.c and it gives an error.
Please explain how making 'a' local/global makes a difference.


Thanks.

---

### Post by IAMTubby on 2012-11-01
Was doing some further reading, Is it true that only global variables from another part of the code can be accessed using extern?

I'll add to the previous questions
5)But I was able to access even without the extern keyword in 1.
6)How then, would you access a local variable within the function, as I asked in 4.

Thanks.

---

### Post by Tony Flury on 2012-11-01
> **IAMTubby said:**
> Hey,
I have been trying hard to understand the extern keyword. I have read up about the difference between declaration and definition. But somehow, I keep getting stuck.

Please have a look at the following 3 files (Please don't mind the file names, I have files of the same name, but I have put only code which would help me understand the concept in these files
.... code snipped...

I'm compiling the application as : *$gcc main.c objtable.c testfunction.c* 
**I have a few questions**
**1.**Yes, I am getting the output. But how ? 
I am **_defining_** the int a; variable twice in the application, and that's not allowed right ? From what I have read, you can declare as many times as you please, but definitions should be done only once.

You are not allowed to declare a identifier twice in the same block or compilation unit - your files are different complication units - so it is fine that you define a in more than one place. How you are getting that output i don't know - I might guess the linker is being nice - I will do some testing and get back to you.

> 
**2.**
Assume, my file3, ie testfunction.c was to look as below
```

/* File3 : testfunction.c */
#include <stdio.h>
extern int a;

int TestFunction()
{
 printf("\nInside testfunction.c, value of a == %d",a);

}

```
How does it work again ? Because main.c calls testfunction.c and nowhere so far have you told that the definition for a variable called a exists in another file called objtable.c. I understand that extern int a; in testfunction.c is to extend the scope, but it gives me a feeling like we are printing without defining it, but with only it's declaration.(Code hasn't seen the definition yet).  

This is exactly what extern is meant to do - it signals to the compiler that the definition of a is i another file, and the liker (which is the last part of the compilation process) links the two (declaration and definition) together.  two functions don't have to be in the same file so long as they see the same declarations, and the variable is defined once somewhere.

> 
3)Why do you need the extern keyword when the same output was got in 1 without adding any extern ?

The fact that the first example worked a bit of a mystery to me at the moment - it might be coincidence - i will do some testing and get back to you.

> 
4)One last question

Assume, I give the int a; in the file objtable.c inside the function.
```

/*  File2 : objtable.c */
#include <stdio.h>
int fun()
{
 int a = 109;
 printf("\nThis is a random function");
}

/*  File3 : testfunction.c */
#include <stdio.h>
extern int a;
int TestFunction()
{
 printf("\nInside testfunction.c, value of a == %d",a);
}

```
Now, I'm not able to access the variable within testfunction.c and it gives an error.
Please explain how making 'a' local/global makes a difference.

The whole point of a local variable is just that - it is local to the code block - in this case your fun function. It is not accessible by name to anything else.

---

### Post by Tony Flury on 2012-11-01
> **IAMTubby said:**
> Was doing some further reading, Is it true that only global variables from another part of the code can be accessed using extern?

I'll add to the previous questions
5)But I was able to access even without the extern keyword in 1.

No idea - all the tests i have done confirm that it does work as you mention, but to be honest, i thought it shouldn't - but I am no expert. I wouldn't rely on it always working without extern - the fact it works for both of us with the testing doesn't mean it always will.

> 
6)How then, would you access a local variable within the function, as I asked in 4.
Thanks.
Simple answer - you can't by name - that is the point of the scoping rules.If you need to access the value - either return it from a function, or set it in a global variable.


A final point - if you can avoid using global varibales, it is a good idea. Use of globals can lead to major design issues as your application becomes more complex.

---

### Post by spjackson on 2012-11-01
Case 1 works because both declarations are at file scope without a storage specifier (i.e. extern or static) and therefore both have external linkage, and consequently refer to the same object.

So why use extern? The point is to make it clear to both the compiler and the human reader that this is only a declaration, not a definition.

At file scope
```

int a;

```
Is a declaration. It may also be a definition, if a more explicit definition isn't found.
```

extern int a;

```
is not a definition.

So, as you have written case 1, if you forget to include file 2 in the link, the program will link OK and when run the output will be 0. If instead, you explicitly state extern in file 3, and forget to include file 2 in the link, the link will fail. This is generally to be preferred.

As an aside, things are less messy with C++, IMHO. case 1 is an error and will fail to link.

---

### Post by Bachstelze on 2012-11-01
C99 6.2.2 §5 states in part:

> If the declaration of an identifier for an object has file scope and no storage-class specifier, its linkage is external.

which is consistent with what you observe. If you want [font=monospace]a[/font] to be limited to objtable.c, declare it static (in that case the printed value will be 0).

*EDIT:* Yes, zero, not undefined. 6.2.4 §3 states in part:

> An object whose identifier is declared with external or internal linkage, or with the storage-class specifier static has static storage duration.

and 6.7.8 §10:

> If an object that has static storage duration is not initialized explicitly, then:
&#8212; if it has arithmetic type, it is initialized to (positive or unsigned) zero;


---

### Post by IAMTubby on 2012-11-03
> **Tony Flury said:**
> 
This is exactly what extern is meant to do - it signals to the compiler that the definition of a is i another file, and the liker (which is the last part of the compilation process) links the two (declaration and definition) together.
Thanks Tony Flury. That was a short and useful summary.
Can we say that to use a variable which is defined not-in-the-same-file, you have the following 2 options.
1)Declare it in another **C file**(say alien.c) and (ideally)use extern in the file where you are working(say native.c). I say ideally because, it will work even if the word "extern" is not used.
2)Define the variable in a **.h file** and then do #include "header.h" inside native.c(the file where you are working) 

Is that correct ?

> **spjackson said:**
> 
So, as you have written case 1, if you forget to include file 2 in the link, the program will link OK and when run the output will be 0. If instead, you explicitly state extern in file 3, and forget to include file 2 in the link, the link will fail. This is generally to be preferred.

Thanks spjackson. Yes, I get it now.
> 
At file scope
```

int a;

```
Is a declaration. It may also be a definition, if a more explicit definition isn't found.
```

extern int a;

```
is not a definition.

As you said, don't you think this is a bit messy ? At the moment, this is how it works.

**compiler.c** :p
```

CompilerCode()
{
 _On Seeing an integer variable(ie, int i; not extern int i;)-------> **4 cases here**_
 {
  If(int is defined globally)
  {
   If int of the same name/label is declared in another file
    **use the value from that file**

   else if there is no other file
    **value = 0**
  } 
  
  else if int is defined locally
  {
   **value = garbage_value** (irrespective of variable of the same name exists in another file in the application or no.
  }
 } 





 _On Seeing an extern integer variable(ie, extern int a) --------------> **8 cases here**_
 {
  if it is declared as extern int i 
  {
   if it is declared globally, ie, outside main
   {
    if there is only 1 file in the application
     **would give error saying variable not defined earlier**
 
    if variable of the same name is already declared as say int i = 10 in another file
     **works fine,value = 10** 
   }

   if it is declared locally, ie, inside main
   {
    if there is only 1 file in the application
     **would give error saying variable not defined earlier**
 
    if variable of the same name is already declared as say int i = 10 in another file
     **works fine, value = 10** 
   }
  }
 
  if it is defined as extern int i = 10 
  {
   if it is defined globally, ie, outside main
   {
    if there is only 1 file in the application
     **works fine, value = 10**
 
    if variable of the same name is already declared as say int i = 10 in another file
     **error : says multiple declaration** 
   }

   if it is defined locally, ie, inside main
   {
    if there is only 1 file in the application
     **error: i has both extern and initializer**
 
    if variable of the same name is already declared as say int i = 10 in another file
     **error: i has both extern and initializer**
   }
  }
 }

}

```

Please have a look at the code below, to get the same in code format
```

Case1 : When the variable i is declared only in this file, and just 1 file in the application.

#include <stdio.h>

//extern int i; //Will give the error : externdefault.c.text+0x12): undefined reference to `i' collect2: ld returned 1 exit status
extern int i = 10; //Works fine!, but with the warning : externdefault.c:4: warning: â initialized and declared âternâ

int main(void)
{
//extern int i;//Will give the error : externdefault.c.text+0x12): undefined reference to `i' collect2: ld returned 1 exit status
//extern int i = 10;//Will give the error : externdefault.c:9: error: â has both âternând initializer

printf("\nValue of i == %d",i);

return 0;
}


Case2 : The variable i is declared to be int i = 10; in the other file in the application.

#include <stdio.h>

//extern int i; //Works fine! : No warnings either
//extern int i = 10; //Error: main.c:4: warning: â initialized and declared âternâtmp/cctKu5ap.o.data+0x0): multiple definition of `i'/tmp/ccUO9uzj.o.data+0x0): st defined herecollect2: ld returned 1 exit status

int main(void)
{
//extern int i;//Works fine
extern int i = 10;//Will give the error : main.c:9: error: â has both âternând initializer

printf("\nValue of i == %d",i);

return 0;
}

```


> **Bachstelze said:**
> C99 6.2.2 §5 states in part:
which is consistent with what you observe.
Thanks Bachstelze for providing the right resources, but I need some more time to go and read it for myself.
But for now, can I say that, by default
_int a; is equivalent to saying extern int a; in terms of viewing the variable in another file( which is more of a, property-you-associate-with-extern)_. The same way all functions are extern by default, and a function declared in any one file can be used in any other file in the same application.
That is, 
```

int a: Declaration + Definition(allocating memory) + Giving it the property to be accessible in other files
extern int a; Declaration + Giving it the property to be accessible in other files

```
But I'm not clear here as to why this happens . Assume this is the **only** file in the applcation.
```

#include <stdio.h>
extern int i = 10; //Works fine!, but with the warning  : externdefault.c:4: warning: Ã¢ initialized and declared Ã¢ternÃ¢

int main(void)
{
 //extern int i = 10;//Will give the error : externdefault.c:9: error: Ã¢ has both Ã¢ternÃ¢nd initializer

 printf("\nValue of i == %d",i);

 return 0;
}

```

I shall read in detail and get back in case of queries. Thanks.

---

### Post by Bachstelze on 2012-11-03
You get an error for a reason. You are not allowed to initialize an extern variable inside a block (what you call "locally"). C99 6.7.8 §5:

> If the declaration of an identifier has block scope, and the identifier has external or internal linkage, the declaration shall have no initializer for the identifier.

---

