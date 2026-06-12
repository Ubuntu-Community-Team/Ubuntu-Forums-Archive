---
title: "Type casting a void function pointer in C"
date: 2012-08-14
forum: Programming Talk
---

### Post by Datweakfreak on 2012-08-14
I'm writing a program that has:

A function that returns char*
A function that returns int
An array of two void function pointers

I made the function pointer void because I want to be able to assign the char* and int functions to it by typecasting the void pointer to int and char* respectively. Here's the code:

```
#include <stdio.h>
#include <malloc.h>

typedef union {
    int intData;
    char *charData;
} dataUnion;

void (*funcArray[2])(dataUnion param);

int func1(dataUnion param) {
    return param.intData;
}

char *func2(dataUnion param) {
    return param.charData;
}

int main(void)
{
    int a;
    char *b;
    
    dataUnion c;

    c.intData = 0;
    c.charData = "foobar";

    funcArray[0] = malloc(sizeof(int));
    funcArray[0] = (int (*)(dataUnion)) funcArray[0];
    funcArray[0] = &func1;

    funcArray[1] = malloc(sizeof(char*));
    funcArray[1] = (char* (*)(dataUnion)) funcArray[1];
    funcArray[1] = &func2;

    a = (*funcArray[0])(c);
    b = (*funcArray[1])(c);

    printf("%d\n", a);
    printf("%s\n", c);

    return 0;
}
```I have these errors:
```

executors.c: In function ‘main’:
executors.c:30:15: warning: assignment from incompatible pointer type [enabled by default]
executors.c:33:15: warning: assignment from incompatible pointer type [enabled by default]
executors.c:35:4: error: void value not ignored as it ought to be
executors.c:36:5: error: void value not ignored as it ought to be
make: *** [executors] Error 1
```I'm still learning the ropes of C, so excuse me if I've done something foolish in the code, or if I'm missing something obvious.

Thanks!

---

### Post by Bachstelze on 2012-08-14
> **Datweakfreak said:**
> 
I made the function pointer void because I want to be able to assign the char* and int functions to it by typecasting the void pointer to int and char* respectively.

You can do that all right, but you do need to cast at every step. Both when storing and accessing the pointers. This is not exactly the kind of thing that I would do to "learn the ropes of C", but whatever. Here goes:

```
#include <stdio.h>
#include <malloc.h>

typedef union {
    int intData;
    char *charData;
} dataUnion;

void (*funcArray[2])(dataUnion param);

int func1(dataUnion param) {
    return param.intData;
}

char *func2(dataUnion param) {
    return param.charData;
}

int main(void)
{
    int a;
    char *b;
    
    dataUnion c;

    c.intData = 0;
    c.charData = "foobar";

    funcArray[0] = (void (*)(dataUnion))func1;
    funcArray[1] = (void (*)(dataUnion))func2;

    a = ((int (*)(dataUnion))(funcArray[0]))(c);
    b = ((char *(*)(dataUnion))(funcArray[1]))(c);

    printf("%d\n", a);
    printf("%s\n", b);

    return 0;
}

```

P.S.: If you expected the first printf() to print 0, it doesn't...

---

### Post by Datweakfreak on 2012-08-14
That works, thanks!

But the output shows:

4195972
foobar

instead of:

0
foobar

I tried assigning a directly to c.intData, but that still returns the same thing.

By learning the ropes, I meant I haven't done anything substantial beyond a few hundred lines of code, and I still haven't gone beyond the basics. I guess I misunderstood the phrase :)

---

### Post by Datweakfreak on 2012-08-14
Alright, I changed it to a struct. Thanks a lot!

---

### Post by Bachstelze on 2012-08-14
Learn about what a union is, and how it is different from a struct. For that matter, also learn about what an array is, because your code says that you are not very clear on that, either.

---

### Post by trent.josephsen on 2012-08-14
"function-returning-pointer-to-char" isn't compatible with "function-returning-int" or "function-returning-void". You can't cast them and pass them about interchangeably or treat one as if it were another, because knowing the return value of a function is essential to calling it.

If you were dealing with non-function types, then you could store a pointer-to-A and a pointer-to-B both as void * and cast it to (A *) or (B *) respectively when you dereference it. But that's not guaranteed to be possible with function types (C doesn't assume a von Neumann architecture, so pointers to code aren't necessarily interchangeable with pointers to data).

What you might do is write your interchangeable functions to return a pointer-to-void; that way they all have the same return type and you can represent the function pointers interchangeably as `void (*)(dataUnion)`.

```
/* returns 1, then 2, then 3, etc. up until 100 */
void *f1(void) { static int i = 0; if (i < 100) i++; return &i; }
/* returns 'A', then 'B', etc. up until 'Z' */
void *f2(void) { static char c = 'A'; if (c < 'Z') c++; return &c; }

void (*a[2])(void) = { f1, f2 };
```

However, you'll also need to keep track of what type each pointer *actually* returns a pointer to, so that you can cast it correctly when you call it:

```
void *p = a[0](); /* p contains a pointer to int */
void *q = a[1](); /* q contains a pointer to char */

char ch1 = *( (char *) p); /* WRONG -- converts p to pointer-to-char */
char ch2 = *( (char *) q); /* ok */

int  i1  = *( (int  *) q); /* WRONG -- converts q to pointer-to-int */
int  i1  = *( (int  *) p); /* ok */
```

This means you need a way to determine, *at runtime*, which pointers point to functions returning which types. You might do this by maintaining another parallel array that simply tracks the appropriate type.

I'm sure most of this isn't making much sense. I'll conclude with one other observation: this

```
    funcArray[0] = malloc(sizeof(int));
    funcArray[0] = (int (*)(dataUnion)) funcArray[0];
    funcArray[0] = &func1;
```

is two no-ops followed by a mistake. I've already addressed why the last is a mistake, but the first two are no-ops because they're all assignment statements that assign to the same object. In other words, the first one is overwritten by the second, which is overwritten by the third. If you want conversions to happen when assigning func1 to funcArray[0], you have to do it all in one step.

Also I don't approve of your use of typedef.

---

### Post by trent.josephsen on 2012-08-14
Thought I'd just add, Bachstelze's version does work, but it depends on... I *think* undefined behavior when casting a function pointer to a pointer to a function returning a different type. Function pointers of different types may have different alignment requirements and conversions between them are not described by the Standard. I think.

---

### Post by Bachstelze on 2012-08-14
> **trent.josephsen said:**
> "function-returning-pointer-to-char" isn't compatible with "function-returning-int" or "function-returning-void". You can't cast them and pass them about interchangeably or treat one as if it were another, because knowing the return value of a function is essential to calling it.

You can, however, cast a function-returning-int to a function-returning-void and then back, and it *will* be equal to the original pointer. This is what OP does here (or at least what I do in my solution).

*EDIT:* 6.3.2.3, §8 (in C99).

---

### Post by Bachstelze on 2012-08-14
I should add that this is not a panacea, and you should be very careful if you do this. In particular, you need to carefully keep track of which type each pointer was originally in order to convert it back to the correct type. If you don't, you enter undefined behavior, and the compiler *will not* warn you!

For example if I swap the indices on lines 32 and 33:

```
firas@aoba ~ % cat test.c                                            
#include <stdio.h>
#include <malloc.h>

struct data {
    int intData;
    char *charData;
};

void (*funcArray[2])(struct data);

int func1(struct data param) {
    return param.intData;
}

char *func2(struct data param) {
    return param.charData;
}

int main(void)
{
    int a;
    char *b;
    
    struct data c;

    c.intData = 0;
    c.charData = "foobar";

    funcArray[0] = (void (*)(struct data))func1;
    funcArray[1] = (void (*)(struct data))func2;

    /* Indices swapped below! */
    a = ((int (*)(struct data))(funcArray[1]))(c);
    b = ((char *(*)(struct data))(funcArray[0]))(c);

    printf("%d\n", a);
    printf("%s\n", b);

    return 0;
}
firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Wextra -g -o test test.c
firas@aoba ~ % ./test 
4196076
zsh: segmentation fault (core dumped)  ./test

```

---

### Post by Datweakfreak on 2012-08-15
I got the general idea of how to deal with function pointers, from the above posts. Thanks guys!

One more question, though, I want to create a dynamic array containing function pointers, so that depending on the number of functions, I can realloc the array. Is this possible, as creating an array of pointers to data?

I did something like this:

```

#include <stdio.h>
#include <malloc.h>

struct dataStruct {
    int intData;
    char *charData;
};

void *(*funcArray)(struct dataStruct param);

int func1(struct dataStruct param) {
    return param.intData;
}

char *func2(struct dataStruct param) {
    return param.charData;
}

int main(void)
{
    int a;
    char *b;
 
    struct dataStruct c;
        
    c.intData = 0;
    c.charData = "foobar";

    printf("%d\n", sizeof(void *(*)(struct dataStruct)));

    funcArray = malloc(2 * sizeof(void *(*)(struct dataStruct)));

    funcArray[0] = (void (*)(struct dataStruct))func1;
    funcArray[1] = (void (*)(struct dataStruct))func2;

    a = ((int (*)(struct dataStruct))(*(*funcArray)))(c);
    b = ((char *(*)(struct dataStruct))(*(*funcArray + 1)))(c);

    printf("%d\n", a);
    printf("%s\n", b);

    return 0;
}
```But that returns an error:

./e    executors.c: In function ‘main’:
executors.c:33:14: error: subscripted value is pointer to function
executors.c:34:14: error: subscripted value is pointer to function

Does this have something to do with C not assuming a Von Neumann architecture?

---

### Post by ofnuts on 2012-08-15
I o agree with Trent that maintaining an array of pointer to functions is pointless if you don' t know how to call them. However I don't think the best solution, is to use several arrays maintained in parallel. but to keep call type and pointer in the sale struct. And if there are no more than a couple of dozen call types the complexity of the function pointer casting can be hidden in an union:
```

typedef union { 
    void* generic; // might not be useful
    int (*intFromIntInt)(int,int); 
    int (*intFromStringString)(char *,char *);
} Pointers; 

typedef struct {
    int callType;
    Pointers pointers;
} TypedPointer;

```So you would create an array of TypedPointers, and to call the function inside the TypedPointer:

```

    switch (tp.callType) {
        case INT_FROM_INT_INT:
            r=tp.pointers.intFromIntInt(xi,yi);
            break;
        case INT_FROM_STRING_STRING:
            r=tp.pointers.intFromStringString(xs,ys);
            break;
        default:
            printf("Unknown call type=%d\n",tp.callType);
            break;
    }

```

---

### Post by trent.josephsen on 2012-08-15
> **Bachstelze said:**
> You can, however, cast a function-returning-int to a function-returning-void and then back, and it *will* be equal to the original pointer. This is what OP does here (or at least what I do in my solution).

*EDIT:* 6.3.2.3, §8 (in C99).
Really? Well I was misinformed. Actually, maybe I'm thinking of ANSI (C89)... don't have a copy of that standard on hand. Thanks for providing a reference; I'll mend my ways. :)

The cast in the following statement makes me flinch:

```
    funcArray[0] = (void (*)(struct dataStruct))func1;
```

Since funcArray[0] is of type void (*)(struct dataStruct), the conversion is automatic, and the cast serves no purpose but to suppress a compiler warning.[1] **This is okay**, and probably preferable to turning off that warning altogether, but you (OP) should know that whenever you cast a pointer that is *not* a pointer to void, you are almost certainly suppressing a compiler warning that could have been useful. It's okay to use them once in a while, but better to **avoid designing code that requires such casts**. Casts, like typedefs, should be used sparingly.

Another thing:
```
    funcArray = malloc(2 * sizeof(void *(*)(struct dataStruct)));
```
Don't type that whole thing out; it's prone to mistake and if you ever change the type of funcArray you'll need to fix it.

```
    funcArray = malloc(2 * sizeof *funcArray);
```

Also, it's not exactly bad practice, but naming things their types (funcArray is an array of functions, dataStruct is a struct type) is generally not useful. Name variables (and struct tags) something that describes their conceptual role in your program. E.g., if you have a struct that represents a widget, and an array of function pointers that represent actions associated with widgets, call them "struct widget" and "widget_actions", not "a_struct" and "function_array". Not a big deal for a small test program like this one, but keep it in mind.

One more thing and I'll stop picking on you. ;) ofnuts' solution is probably preferable to storing types and pointers-to-data separately. However, this is beginning to look more and more like an attempt to do OOP in C. Which is okay, and technically possible, but seriously, if you want to use OOP, your first inclination should not be to take a language without OO features and try to graft them on. If you want C, use C; if you want C with kludgy OOP, use C++. :D

---

### Post by spjackson on 2012-08-15
> **Datweakfreak said:**
> 
./e    executors.c: In function ‘main’:
executors.c:33:14: error: subscripted value is pointer to function
executors.c:34:14: error: subscripted value is pointer to function

Does this have something to do with C not assuming a Von Neumann architecture?
No. You've got errors with your types. To be honest, a surfeit of complex types like I see in your code always sends shudders down my spine, so I won't attempt to repair it. In my opinion, I find it much clearer to simplify as much as possible with a typedef. Something like this:
```

#include <stdio.h>
#include <malloc.h>

struct dataStruct {
    int intData;
    char *charData;
};

typedef void * (*our_function_ptr)(struct dataStruct);

our_function_ptr * funcArray;

int func1(struct dataStruct param) {
    return param.intData;
}

char *func2(struct dataStruct param) {
    return param.charData;
}

int main(void)
{
    int a;
    char *b;
 
    struct dataStruct c;
        
    c.intData = 0;
    c.charData = "foobar";

    printf("%d\n", sizeof(funcArray[0]));

    funcArray = malloc(2 * sizeof(funcArray[0]));

    funcArray[0] = (our_function_ptr) func1;
    funcArray[1] = (our_function_ptr) func2;

    a = (int)((funcArray[0])(c));
    b = (char *)((funcArray[1])(c));

    printf("%d\n", a);
    printf("%s\n", b);

    return 0;
}

```OK, still a little ugly I admit, but at a lot more readable to a mere mortal like me.

---

### Post by ofnuts on 2012-08-15
> **trent.josephsen said:**
> ofnuts' solution is probably preferable to storing types and pointers-to-data separately. However, this is beginning to look more and more like an attempt to do OOP in C. Which is okay, and technically possible, but seriously, if you want to use OOP, your first inclination should not be to take a language without OO features and try to graft them on. If you want C, use C; if you want C with kludgy OOP, use C++. :DStructs have been around since well before OOP...

---

### Post by trent.josephsen on 2012-08-15
> **ofnuts said:**
> Structs have been around since well before OOP...
It's not the structs I'm complaining about, but the crude pseudo-message-passing implied by determining at runtime what function to call based on a type. That's not an idiomatic way to use C.

---

### Post by Datweakfreak on 2012-08-15
Though certain stuff flew above my head, this thread's turned out to be very enlightening. Thanks for all the free knowledge, people!

My case is this: A bunch of functions(let's say helpers) and pointers to them, each pointer with a macro that maps the pointer back to a plain string(would be easier to pass the macros as parameters in external modules, I thought). One more function that takes these pointers to helpers (their macros, that is) as parameters and runs the helpers sequentially. So basically, a function that executes a bunch of other functions sequentially. 

Reading this thread just taught me how plain out ugly some of my implementation plans were.

---

### Post by ofnuts on 2012-08-16
> **trent.josephsen said:**
> It's not the structs I'm complaining about, but the crude pseudo-message-passing implied by determining at runtime what function to call based on a type. That's not an idiomatic way to use C.
Wait a minute, you said, before me:
> 
This means you need a way to determine, *at runtime*, which  pointers point to functions returning which types. You might do this by  maintaining another parallel array that simply tracks the appropriate  type.

My only change to this is just keeping related data together. In other words, is it better to use:
```

switch(types[i]){
  case 1:
      functions[i].pointers.intFromIntInt(x,y); // assuming "union" trick
      break;
  case 2:
      ((unreadable_cast_from_hell) functions[i])(x,y); // without "union" trick
      break;
...

```
or
```

switch (typedPointers[i].type) {
   case 1:
      typedPointers[i].pointers.intFromIntInt(x,y);
      break;

``` 

Finding at runtime what function to call and how to call it isn't that much OOP-related, I did this in C+assembler a long time ago, in an interface between two programming languages...

Here this is mandated by the specs, and there is no C language construct to support this directly... but C is flexible enough to allow it.

---

### Post by trent.josephsen on 2012-08-16
> **ofnuts said:**
> My only change to this is just keeping related data together. In other words, is it better to use:
I merely suggested one possible solution, one that's a bit more trivial than yours. Your solution is better than what I suggested, no doubt about that -- I'm not arguing that point. What I'm saying is that the design itself is complex, probably too complex. I've seen complexity like this before. I've *written* complexity like this before, when I was an ex-Java programmer new to C and felt compelled to make an object out of everything. (Maybe I'm just projecting?)

> Finding at runtime what function to call and how to call it isn't that much OOP-related, I did this in C+assembler a long time ago, in an interface between two programming languages...
However, the notion that *data itself* "knows" what its type is and what operations can be associated with it is not a C-like notion. It's not all the way in OOP-land but it seems to me like the kind of thing that a programmer might cook up if he were not well versed in C but had some exposure to OOP. That's all I was trying to say.

> Here this is mandated by the specs, and there is no C language construct to support this directly... but C is flexible enough to allow it.
Perl is flexible enough to write a file system in. :P

---

### Post by ofnuts on 2012-08-16
> **trent.josephsen said:**
> I merely suggested one possible solution, one that's a bit more trivial than yours. Your solution is better than what I suggested, no doubt about that -- I'm not arguing that point. What I'm saying is that the design itself is complex, probably too complex. I've seen complexity like this before. I've *written* complexity like this before, when I was an ex-Java programmer new to C and felt compelled to make an object out of everything. (Maybe I'm just projecting?)


However, the notion that *data itself* "knows" what its type is and what operations can be associated with it is not a C-like notion. It's not all the way in OOP-land but it seems to me like the kind of thing that a programmer might cook up if he were not well versed in C but had some exposure to OOP. That's all I was trying to say.
I don't see my design as any more complex than maintaining two arrays in parallel. In fact I find it simpler: one single array to manage, one single item to pass as a parameter if needed... that is what structs are meant for, and they have been part of the C language since the beginning (in my '78 edition(*) of the K&R, there is a whole chapter on them (Chapter 6, pp 119-140), about 10% of the whole book.... Of course in C++ class and structs are closely related, but that doesn't make structs an OOP-ism (or K&R OOP crypto-minions).

(*) showing my age here... got the book in '82 or '83..

---

### Post by trent.josephsen on 2012-08-16
I was referring to your design and parallel arrays as two implementations of the same underlying design. I'm not criticizing the solution, but the formulation of the problem.

---

