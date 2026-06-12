---
title: "NULL and HEAP in C"
date: 2011-08-03
forum: Programming Talk
---

### Post by shashanksingh on 2011-08-03
Hi.

Iv'e done most of my programming in Java, and  I'm new to C.

I was wondering...

1.What is a NULL value in C? in Java, we often have variables that do not point to something as NULL (string s; s is null here, so I can check that in Java. How do I do so in C??). The closest analogy I could make is that of an uninitialized pointer in C, but that has some garbage and not NULL.

2.Is there a HEAP in C as well? Which objects are stored in it? I think most of OOP objects are stored in a HEAP and not the program Stack.

thanks

---

### Post by Bachstelze on 2011-08-03
1. NULL is a macro that expands to a *null pointer constant*. A null pointer constant can be either an integer constant with value 0, or such a constant cast to a void*.

2. Memory is allocated on the heap when you allocate it with malloc, calloc or realloc. I wouldn't swear on it but I think it's the only case where it is allocated on the heap. If you just declare a variable, the memory for it is allocated on the stack.

---

### Post by slavik on 2011-08-03
1. NULL == 0 == '\0'
2. malloc() family of functions allocate memory on the heap and return a pointer to it

---

### Post by karlson on 2011-08-03
> **shashanksingh said:**
> Hi.

Iv'e done most of my programming in Java, and  I'm new to C.

I was wondering...

1.What is a NULL value in C?


NULL == 0

> in Java, we often have variables that do not point to something as NULL (string s; s is null here, so I can check that in Java. How do I do so in C??). The closest analogy I could make is that of an uninitialized pointer in C, but that has some garbage and not NULL.


A lot of languages denote the concept of NOTHING as NULL, unfortunately C does not really have that given what it was designed to do.  The uninitialized pointer in C is not NULL it is initialized to the value currently in memory used for pointer.  So the closest analogy to the concept you are describing in Java or Perl is:
```

char *s = NULL;

```

> 

2.Is there a HEAP in C as well? Which objects are stored in it? I think most of OOP objects are stored in a HEAP and not the program Stack.

thanks

There is HEAP in C as well.  Every time you allocate memory directly using "malloc", "calloc" that memory allocation is on the heap.  As far as most of OOP objects being stored on the HEAP you are wrong.  The objects are equaly likely to be stored on HEAP as they are in STACK...  And actually more objects are on the STACK then there are on the HEAP.

---

### Post by Bachstelze on 2011-08-03
> **karlson said:**
> NULL == 0


The question was not what it compares equal to, but what it is. (Then again, "a NULL value" is nonsensical, so hard to tell what the question was exactly...)

---

### Post by Bachstelze on 2011-08-03
Also "heap" and "stack" lowercase please, they are not acronyms or macros.

---

### Post by Arndt on 2011-08-03
> **Bachstelze said:**
> If you just declare a variable, the memory for it is allocated on the stack.

Only within functions (and then when 'static' is not used), not outside them.

---

### Post by ve4cib on 2011-08-03
> **karlson said:**
> NULL == 0

Not always.  That's *normally* the case, but in terms of the actual value, the C standard does not specify that NULL must be zero.  It only states that the integer value 0, when cast to a pointer, will be NULL.  It does not state however that when NULL is cast back to an integer that the result must be 0.

The actual memory address pointed to by NULL could be any unavailable address.  In practice this is usually 0, but you shouldn't rely on that.

In C there's also a second null, the '\0' character, used to terminate strings.  However, the string null, and the NULL pointer are not the same thing, despite using the same name.

---

### Post by Bachstelze on 2011-08-03
> **ve4cib said:**
> Not always.  That's *normally* the case, but in terms of the actual value, the C standard does not specify that NULL must be zero.  It only states that the integer value 0, when cast to a pointer, will be NULL.  It does not state however that when NULL is cast back to an integer that the result must be 0.

Your last statement is true, but the catch is that there is no conversion involved when doing this comparison, and the internal representation of a null pointer is completely irrelevant.

[http://c-faq.com/null/ptrtest.html](http://c-faq.com/null/ptrtest.html)

A null pointer is guaranteed to compare equal to 0, regardless of its internal representation.

---

### Post by ve4cib on 2011-08-03
> **Bachstelze said:**
> Your last statement is true, but the catch is that there is no conversion involved when doing this comparison, and the internal representation of a null pointer is completely irrelevant.

[http://c-faq.com/null/ptrtest.html](http://c-faq.com/null/ptrtest.html)

A null pointer is guaranteed to compare equal to 0, regardless of its internal representation.

EDIT: I was speaking more about the internal representation than the comparison anyway.

---

### Post by Bachstelze on 2011-08-03
It is the case when you are comparing to a non-zero integer, but 0 is special. As I said above, an integer constant with value 0 (0, but also '\0', 0L, 0u, etc.) is a *null pointer constant*. A comparison between a pointer and a null pointer constant will be true if an only if the pointer is a null pointer, regardless of the internal representation of a null pointer.

---

### Post by karlson on 2011-08-03
> **ve4cib said:**
> Not always.  That's *normally* the case, but in terms of the actual value, the C standard does not specify that NULL must be zero.  It only states that the integer value 0, when cast to a pointer, will be NULL.  It does not state however that when NULL is cast back to an integer that the result must be 0.


I don't rely on this but most common implementations have NULL defined as 0x0 and it actually makes sense since casting in C is simply reinterpreting the data type in the same memory location as a different type.

> 
The actual memory address pointed to by NULL could be any unavailable address.  In practice this is usually 0, but you shouldn't rely on that.


Agreed...

> 
In C there's also a second null, the '\0' character, used to terminate strings.  However, the string null, and the NULL pointer are not the same thing, despite using the same name.

I can't say I agree with this statement the null string or undefined string is not the same as empty string.  I'm thinking that "Null terminated string" has actually stemmed from NULL = '\0' = 0, but I cannot know this for sure.

Most language interpreters use a secondary indicator that something is undefined.  It is very difficult to explain the concept of 'nothing' to something that is deterministic like a computer.

---

### Post by Bachstelze on 2011-08-03
> **karlson said:**
> I don't rely on this but most common implementations have NULL defined as 0x0 and it actually makes sense since casting in C is simply reinterpreting the data type in the same memory location as a different type.

As much as I hate to repeat myself, the internal representation of a null pointer is absolutely irrelevant in the fact that it is represented by the value 0. Don't say that "it actually makes sense", because it doesn't. The choice of 0 is purely arbitrary, it could have been anything else, another integer or a keyword like in Java or Pascal.

Also gcc defines NULL as (void*)0.

*EDIT:* Actually it makes so little sense that people felt the need to introduce NULL in the first place, probably because writing [font=monospace]int *p = 0;[/font] made a lot of people cringe, quite rightly I might add. NULL is really just syntactic sugar.

---

### Post by Bachstelze on 2011-08-03
@shashanksingh: A null pointer (lowercase!) in C is a pointer that points to nothing. It is guaranteed to compare unequal to any pointer to a valid object. As you correctly noted, this is not the same as an uninitialised pointer, which could point anywhere, including to a valid object.

To obtain a null pointer, you convert a *null pointer constant* to the appropriate pointer type. A null pointer constant is either an integer constant with the value 0, or such an integer constant cast to a pointer of type void, so for example

```
int *p1 = 0;
char *p2 = (void*)0;
float *p3 = 0u;
long *p4 = (void*)'\0';

```

will all produce null pointers. The C equivalent to the Java keyword null is a null pointer constant.

So as you can see, you *do not* need NULL (uppercase) to create null pointers. What is NULL then? It is a macro that expands to an implementation-defined null pointer constant. What this means is that the preprocessor will replace NULL with a null pointer constant of its choice (it can be 0, 0l, (void*)'\0', or any other null pointer constant) before the compiler compiles the code. Therefore, to repeat myself, you do not need NULL to create null pointers, you can use a null pointer constant directly instead of having the preprocessor replace NULL with one for you.

Moreover, a null pointer is guaranteed to compare equal to a null pointer constant, so assuming p is a pointer, all these comparisons are equivalent and will be true if and only if p is a null pointer:

```

if (p == NULL) /* Expands to  if (p == SOME_NULL_POINTER_CONSTANT) */
if (p == 0)
if (p == (void*)'\0')
if (!p) /* Really means   if (p == 0) */
```

One catch: 0 cast to any pointer type other than void* *is not* a null pointer constant (it is a null pointer of that particular pointer type only), so for example

```
int *p = (char*)0;
```

might not yield a null pointer. Also, never use NULL for anything other than pointers:

```
int n = NULL;
```

will work on implementations that expand NULL to 0, but not on those that expand it to (void*)0.

Notice than in all this, *the internal representation of a null pointer is totally irrelevant*! C programmers often care more about the internal representation of things than they need, which leads them to making false assumptions.

---

### Post by shashanksingh on 2011-08-07
> **Bachstelze said:**
> 
```
int *p1 = 0;
char *p2 = (void*)0;
float *p3 = 0u;
long *p4 = (void*)'\0';

```

will all produce null pointers. The C equivalent to the Java keyword null is a null pointer constant.



```

if (p == NULL) /* Expands to  if (p == SOME_NULL_POINTER_CONSTANT) */
if (p == 0)
if (p == (void*)'\0')
if (!p) /* Really means   if (p == 0) */
```

One catch: 0 cast to any pointer type other than void* *is not* a null pointer constant (it is a null pointer of that particular pointer type only), so for example

```
int *p = (char*)0;
```

might not yield a null pointer. Also, never use NULL for anything other than pointers:

```
int n = NULL;
```

will work on implementations that expand NULL to 0, but not on those that expand it to (void*)0.

Notice than in all this, *the internal representation of a null pointer is totally irrelevant*! C programmers often care more about the internal representation of things than they need, which leads them to making false assumptions.


Ok, so I think a null pointer, in C, is basically pointing to a 0 (int) and other constant types '\0'.


int *p= (int *)0;
So *p is the null pointer.

The crux of my doubt was how do people know if a pointer is FREE or NOT pointing to anything. Does that mean I compare that with the *p as above?
Doesn't that basically mean C has DEFINED what NOT POINTING to something is in this syntax, and say if I do free(*pointer), then the *pointer=(int *)0, can be one such statement at the end of the free() function?

---

### Post by slavik on 2011-08-07
C does not stop you from shooting yourself in the foot.

---

### Post by karlson on 2011-08-07
> **shashanksingh said:**
> Ok, so I think a null pointer, in C, is basically pointing to a 0 (int) and other constant types '\0'.

int *p= (int *)0;
So *p is the null pointer.


You misunderstand.  In a lot of compilers including GCC the NULL pointer is implemented as (void *)0, there may be operating systems and compilers that this is not the case.  It may be implemented as 0xffffffffffffffff, so don't confuse them.  If you want to make sure that something is NULL do
```

int *p = NULL;

```

This removes ambiguity and reliance on implementation.

> 
The crux of my doubt was how do people know if a pointer is FREE or NOT pointing to anything. Does that mean I compare that with the *p as above?


In C you don't know if a pointer is free or not pointing to anything real a pointer is simply an address of a memory location, what is or isn't in it is based on your program.

> 
Doesn't that basically mean C has DEFINED what NOT POINTING to something is in this syntax, and say if I do free(*pointer), then the *pointer=(int *)0, can be one such statement at the end of the free() function?

First of all this is the wrong syntax for free() and the assignment.  I am not sure what you mean in your question, but if you need to reset the pointer you should follow the free with:
```

ptr = NULL;

```

implementation of free does not reset the pointer.

---

### Post by Bachstelze on 2011-08-08
> **shashanksingh said:**
> Ok, so I think a null pointer, in C, is basically pointing to a 0 (int) and other constant types '\0'.

No. A null pointer does not point to anything meaningful. 0 is how you create a null pointer because that's how it is, not because a null pointer has anything to do with the integer 0.

> 
int *p= (int *)0;
So *p is the null pointer.

No. p is a null pointer of type int*. *p is nothing.

> The crux of my doubt was how do people know if a pointer is FREE or NOT pointing to anything. Does that mean I compare that with the *p as above?

A pointer that's not pointing to anything is a null pointer. What do you mean by "a pointer is free"? That doesn't make sense.

> Doesn't that basically mean C has DEFINED what NOT POINTING to something is in this syntax, and say if I do free(*pointer), then the *pointer=(int *)0, can be one such statement at the end of the free() function?

I don't understant what you mean here.

> **karlson said:**
> You misunderstand.  In a lot of compilers including GCC the NULL pointer is implemented as (void *)0, there may be operating systems and compilers that this is not the case.  It may be implemented as 0xffffffffffffffff, so don't confuse them.  If you want to make sure that something is NULL do
```

int *p = NULL;

```

This removes ambiguity and reliance on implementation.

I think a facepalm is in order here. I've told you repeatedly, in this thread and in PM, that the way you create a null pointer is standard-defined, and therefore not implementation-dependent. Apparently you don't want to understand, I wonder why.

---

### Post by ve4cib on 2011-08-08
> **Bachstelze said:**
> I think a facepalm is in order here. I've told you repeatedly, in this thread and in PM, that the way you create a null pointer is standard-defined, and therefore not implementation-dependent. Apparently you don't want to understand, I wonder why.

I will agree with shashanksingh that explicitly using "NULL" instead of "0" is a nice practice.  Yes, 0 will happily be treated as NULL, and do the same thing, but when I'm reading code I usually expect 0 to be assigned to int/double/float/other numerical types, and NULL to be assigned to pointers.  I just makes code that's easier for me to read.

But that's just stylistic quibbling, and somewhat tangential to the issue you're discussing.

---

### Post by Bachstelze on 2011-08-08
> **ve4cib said:**
> I will agree with shashanksingh that explicitly using "NULL" instead of "0" is a nice practice.  Yes, 0 will happily be treated as NULL, and do the same thing, but when I'm reading code I usually expect 0 to be assigned to int/double/float/other numerical types, and NULL to be assigned to pointers.  I just makes code that's easier for me to read.

But that's just stylistic quibbling, and somewhat tangential to the issue you're discussing.

I totally agree, but it is still important to understand that NULL is always 0, on all platforms. Even though [font=monospace]int *p = 0[/font] is not common, [font=monospace]if (p)[/font] is, and if you don't undestand that NULL is always 0, you won't understand why it always works.

*EDIT:* Though personally, I reject both on the exact same grounds.

---

### Post by ve4cib on 2011-08-08
> **Bachstelze said:**
> I totally agree, but it is still important to understand that NULL is always 0, on all platforms. Even though [font=monospace]int *p = 0[/font] is not common, [font=monospace]if (p)[/font] is, and if you don't undestand that NULL is always 0, you won't understand why it always works.

Definitely.  But as you said earlier, C programmers tend to focus far too heavily on the super-low-level stuff and the internal representations of everything, instead of having faith in the compiler to do its job.

---

### Post by karlson on 2011-08-08
> **Bachstelze said:**
> 
I think a facepalm is in order here. I've told you repeatedly, in this thread and in PM, that the way you create a null pointer is standard-defined, and therefore not implementation-dependent. Apparently you don't want to understand, I wonder why.

I have to apologize and re-read the standard.

---

### Post by karlson on 2011-08-08
> **ve4cib said:**
> Definitely.  But as you said earlier, C programmers tend to focus far too heavily on the super-low-level stuff and the internal representations of everything, instead of having faith in the compiler to do its job.

Having faith in compilers while important may not be the best way of implementing certain things case in point:

```

char str[8];
char str1[8];

...

if(!strcmp(str, str1))
{
    do something
}

```

The most efficient way of implementing a comparison in this case isn't a call to strcmp, but this is a different discussion altogether.

---

### Post by shashanksingh on 2011-08-09
Ok I think I understood now, and hopefully wont be more confused about it.

Thank you.

I was checking out the values of pointers with gdb..

char *p;

I use p at some point of time in my code.

When I saw its default value using gdb, I got this

```
p	char *	0x7fffffffe6f0 "\001"	0x7fffffffe600	

```

the above values respectively are:
Name, Type, Value, Address

so *p is 0x7fffffffe6f0 "\001" 

What does "\001" mean? And how do we comprehend that value? I thought it must be just a normal hex value like that of an int.

---

### Post by Bachstelze on 2011-08-09
What gdb command did you use?

But anyway, since you did not initialize the pointer, you can't expect its value to be anything, so it doesn't matter at all what it actually is.

---

### Post by shashanksingh on 2011-08-09
have attatched the two screenshots. I was using gdb at the backend with eclipse debugging tool.

I think that eclipse shows the literal value of the address stored at the pointer and the value at that address in Quotes. Thats what I can make of it now.

So the default for pointers without definition, the value must be something that turns out to be "\001"

---

### Post by dwhitney67 on 2011-08-09
> **shashanksingh said:**
> 
So the default for pointers without definition, the value must be something that turns out to be "\001"

Picture the thoughts that are running through your head after you wake up from a nap on a hot sunny day.  Undoubtedly you have waken up from many naps.  Now ask yourself... are your thoughts as you awaken from these naps always the same?

From the look of your responses on this thread, it would seem so.  Nevertheless, from the perspective of a C program, an _uninitialized_ pointer will point to some area in virtual memory that may or may not contain the same data from one run of the program to another.

```

<some address>           <some other address>
+----------+               +-----------+
|    p     |-------------->|    data   |
+----------+               +-----------+

```
So, when p is pointing to some random address (ie some other address as shown above), the data value could be ANYTHING!  If you want to initialize the pointer p to NULL, then that "some other address" will be zero.  If you point it to the address of another variable (as in your example), then the "some other address" will be the address of that variable.

Please tell me you understand this!  If not, you may need to give up on programming... or consider developing in Python.

---

### Post by karlson on 2011-08-09
> **shashanksingh said:**
> So the default for pointers without definition, the value must be something that turns out to be "\001"

This is wrong since you misunderstand the difference between uninitialized and NULL.

By default the value of a variable without initialization is whatever is stored in memory at the time.

So in the case of *p, which has some 8 bytes of memory allocated to store an address had some residual data which turned out to be 0x7fffffffe600.

So when this address was dereferenced by the debugger the value stored in the byte pointed to by the address above it turned out that byte had '\001' stored in it.

---

### Post by JupiterV2 on 2011-08-09
> **slavik said:**
> C does not stop you from shooting yourself in the foot.

Indeed, C will even hand you the gun.

---

### Post by jwbrase on 2011-08-10
> **shashanksingh said:**
> Ok, so I think a null pointer, in C, is basically pointing to a 0 (int) and other constant types '\0'.

It's not pointing to *a* zero, it's pointing to address 0 (or some other address that's guaranteed to be invalid).

Imagine a street with a bunch of mailboxes, labeled with addresses from 1 to 1000. Imagine that each mailbox contains a postcard with a number on it. A pointer is when we go to a mailbox, read the number on the postcard, and then go to the mailbox whose address is that number and read the number on its postcard. For example, we might go to mailbox 5 and find that its postcard has the number 37 on it. We'd then go to mailbox 37 and read its postcard, which might have the number 200 on it. We'd then use the number 200 for whatever calculation we were doing.

A null pointer is what we use when we want to point at *nothing*. We use a number that no mailbox has for its address (usually 0), and put it in the mailbox we're using as a pointer. So we might go to mailbox 5 and find that the number on its postcard is 0. There is no mailbox 0, so we can't get a number from it, and thus we don't use *anything* for the calculation we were doing.

---

### Post by jwbrase on 2011-08-10
> **Bachstelze said:**
> I totally agree, but it is still important to understand that NULL is always 0, on all platforms.

I get what you're saying, but I wouldn't word it that way.

0, when used as a pointer rather than as an integer, is always NULL, but NULL, when used as an integer rather than as a pointer, is not always 0.

---

### Post by shashanksingh on 2011-08-10
> **dwhitney67 said:**
> 
So, when p is pointing to some random address (ie some other address as shown above), the data value could be ANYTHING!  If you want to initialize the pointer p to NULL, then that "some other address" will be zero.  If you point it to the address of another variable (as in your example), then the "some other address" will be the address of that variable.

Please tell me you understand this!  If not, you may need to give up on programming... or consider developing in Python.

Yes I do.

> **karlson said:**
> This is wrong since you misunderstand the difference between uninitialized and NULL.

So when this address was dereferenced by the debugger the value stored in the byte pointed to by the address above it turned out that byte had '\001' stored in it.

Understood.

> **jwbrase said:**
> It's not pointing to *a* zero, it's pointing to address 0 (or some other address that's guaranteed to be invalid).

Imagine a street with a bunch of mailboxes, labeled with addresses from 1 to 1000. Imagine that each mailbox contains a postcard with a number on it. A pointer is when we go to a mailbox, read the number on the postcard, and then go to the mailbox whose address is that number and read the number on its postcard. For example, we might go to mailbox 5 and find that its postcard has the number 37 on it. We'd then go to mailbox 37 and read its postcard, which might have the number 200 on it. We'd then use the number 200 for whatever calculation we were doing.

A null pointer is what we use when we want to point at *nothing*. We use a number that no mailbox has for its address (usually 0), and put it in the mailbox we're using as a pointer. So we might go to mailbox 5 and find that the number on its postcard is 0. There is no mailbox 0, so we can't get a number from it, and thus we don't use *anything* for the calculation we were doing.

Very well explained. 
Thank you all.

Thread solved.

---

