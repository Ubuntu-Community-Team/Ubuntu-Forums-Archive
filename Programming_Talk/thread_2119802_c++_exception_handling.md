---
title: "c++ exception handling"
date: 2013-02-24
forum: Programming Talk
---

### Post by Dirich on 2013-02-24
Hello, I am experimenting with try...catch.
I usually read the value of what I throw, since I code info about the details of the problem in there.

I used:

```
standard types (i.e. unsigned short int) -> no problem
typdef of standard types (i.e. typdef int Mine) -> no problem
array[2] of standard type (i.e. int variable[2]-> no problem

```But then I tried something else and it's not working:
```

typedef short unsigned int MyType;

MyType variable[3];

```What I mean by "not working" is that when I write
```

try
{
         MyType var[3];
         var[0] = 0;
         throw var;
}
catch (MyType var[3])
{
         cout << var[0] << endl;
}
```I do not get the same result as when I do
```

try
{
         MyType var[3];
         var[0] = 0;
         throw var[0];
}
catch (MyType var)
{
         cout << var[0] << endl;
}
```The first one gives me some random value, the second one gives me the correct value of 0 in output.

In my program, I am not throwing directly from the "try" scope. I am inside a couple of function call and an if statement, but that should change nothing due to how the exceptions work (it doesn't with all the other cases I tried).

---

### Post by muteXe on 2013-02-25
What do you think this is actually doing?

```

catch (MyType var[3])

```

---

### Post by Dirich on 2013-02-25
> **muteXe said:**
> What do you think this is actually doing?

```

catch (MyType var[3])

```
Catching an array of 3 elements of type MyType. It's what it does when I do

```

catch (int var[2])

```and this one works 100% of the time.

Is it not so?

---

### Post by muteXe on 2013-02-25
well it almost sounds like if you're getting nonsense are you in fact asking for the 4th element of the array, rather than an array of 3 elements?
I'm not sure without testing it but it kinda feels like that.
I'll have a look at lunchtime.

Also:  you would normally throw exception objects rather than 'normal' datatypes.

---

### Post by spjackson on 2013-02-25
The automatic object var has a duration that ends on exit from the try block. What is thrown and caught is a pointer. The caught pointer points to memory that is no longer valid. Accessing that memory is undefined behaviour.

It is similar to this:
```

MyType * foo()
{
   MyType var[3];
   var[0] = 0;
   
   return var;
}

```


What you catch is a copy of what was thrown. This works for basic types and (copyable) class objects. However, in the case of arrays, it is the pointer that is copied, not the thing pointed to.

If you wrap your array in a struct and throw and catch the struct, that will remove the undefined behaviour.

---

### Post by GeneralZod on 2013-02-25
I'm guessing C++ handles the "MyType var[3]" in the catch clause in the same way that it handles it in a parameter list - by treating it as MyType*.  Coupled with this, from the spec:

> 
A throw-expression initializes a temporary object, called the exception object, the type of which is determined by removing any top-level cv-qualifiers from the static type of the operand of throw and **adjusting the type from &#8220;array of T&#8221;** or &#8220;function returning T&#8221; **to &#8220;pointer to T&#8221;** or &#8220;pointer to function returning T&#8221;,
respectively.


So basically, you're throwing and catching a pointer to a local stack object, and attempting to dereference this is undefined behaviour.

Edit:

Goddamnit

---

### Post by Dirich on 2013-02-25
> **muteXe said:**
> well it almost sounds like if you're getting nonsense are you in fact asking for the 4th element of the array, rather than an array of 3 elements?
I'm not sure without testing it but it kinda feels like that.
I'll have a look at lunchtime.

Also:  you would normally throw exception objects rather than 'normal' datatypes.

I really *just* started using try...catch, and I saw all the exception types, but all the teaching examples are with standard ones (which are just a typedef away from the others anyway), so at the beginning I did not even used typedefs (now I do).

But to the point, to my understanding, in the catch "argument" what is relevant is the type, since the catching is type-based. Also, the variable used to catch is the one declared in that part, so I really thought of

catch (int a)

as

catch (type)

plus a name to refer to the value being thrown ('a' in the example).

Am I wrong?

---

### Post by muteXe on 2013-02-25
i think i am wrong and all the other fella's are right :)

---

### Post by Dirich on 2013-02-25
> **spjackson said:**
> The automatic object var has a duration that ends on exit from the try block. What is thrown and caught is a pointer. The caught pointer points to memory that is no longer valid. Accessing that memory is undefined behaviour.

It is similar to this:
```

MyType * foo()
{
   MyType var[3];
   var[0] = 0;
   
   return var;
}

```What you catch is a copy of what was thrown. This works for basic types and (copyable) class objects. However, in the case of arrays, it is the pointer that is copied, not the thing pointed to.

If you wrap your array in a struct and throw and catch the struct, that will remove the undefined behaviour.

Ok, thanks! (and thank you General Zodd too).
If not for the big coincidence that the int [2] array always gave the right results... that mislead me.

Since structures can be passed by value, I should be safe with them.

---

### Post by dwhitney67 on 2013-02-25
> **Dirich said:**
> 
What I mean by "not working" is that when I write...
I do not get the same result as when I do...
The first one gives me some random value, the second one gives me the correct value of 0 in output.


It's not very wise to test with the value zero, since it can be difficult to determine if it is indeed the same value you set, or just merely the value that the array is initialized to.

Anyhow, I've never seen anyone ever attempt to throw an array (generally there's no point in such), however, for grins, I attempted your little program, and it appears to work fine for me.  Perhaps you did not compile the program, or run the correct one?
```

#include <cassert>

typedef short unsigned int MyType;

int main()
{
    try
    {
        MyType mt[3];

        mt[0] = 10;
        mt[1] = 20;
        mt[2] = 30;

        throw mt;
    }
    catch (MyType var[3])     // btw, the code in between the parenthesis is a declaration of an array
    {
        assert(var[0] == 10);
        assert(var[1] == 20);
        assert(var[2] == 30);
    }
}

```

---

### Post by GeneralZod on 2013-02-25
> **dwhitney67 said:**
> It's not very wise to test with the value zero, since it can be difficult to determine if it is indeed the same value you set, or just merely the value that the array is initialized to.

Anyhow, I've never seen anyone ever attempt to throw an array (generally there's no point in such), however, for grins, I attempted your little program, and it appears to work fine for me.  Perhaps you did not compile the program, or run the correct one?
```

#include <cassert>

typedef short unsigned int MyType;

int main()
{
    try
    {
        MyType mt[3];

        mt[0] = 10;
        mt[1] = 20;
        mt[2] = 30;

        throw mt;
    }
    catch (MyType var[3])     // btw, the code in between the parenthesis is a declaration of an array
    {
        assert(var[0] == 10);
        assert(var[1] == 20);
        assert(var[2] == 30);
    }
}

```

This works only by fluke; you're still dereferencing a pointer to an object whose lifespan has ended: you got lucky that this implementation of C++ doesn't bother to "destroy" unsigned ints declared on the stack :)

Consider e.g.

```

#include <cassert>
#include <iostream>

class MyType
{
public:
    MyType() : m_a(10) {};
    ~MyType() { m_a = -1; };
    MyType(const MyType& other) : m_a(other.m_a) {};
    int a() { return m_a;};
private:
    int m_a;
};

int main()
{
    try
    {
        MyType mt[3];
        throw mt;
    }
    catch (MyType var[3])     // btw, the code in between the parenthesis is a declaration of an array
    {
        std::cout << "blah: " << var[0].a() << std::endl;
        assert(var[0].a() == 10);
    }
}

```

---

### Post by muteXe on 2013-02-25
> 
 // btw, the code in between the parenthesis is a declaration of an array


yea that threw me a bit (no pun intended).  Looks strange to me.

---

### Post by Dirich on 2013-02-25
> **dwhitney67 said:**
> It's not very wise to test with the value zero, since it can be difficult to determine if it is indeed the same value you set, or just merely the value that the array is initialized to.

Anyhow, I've never seen anyone ever attempt to throw an array (generally there's no point in such), however, for grins, I attempted your little program, and it appears to work fine for me.  Perhaps you did not compile the program, or run the correct one?
```

#include <cassert>

typedef short unsigned int MyType;

int main()
{
    try
    {
        MyType mt[3];

        mt[0] = 10;
        mt[1] = 20;
        mt[2] = 30;

        throw mt;
    }
    catch (MyType var[3])     // btw, the code in between the parenthesis is a declaration of an array
    {
        assert(var[0] == 10);
        assert(var[1] == 20);
        assert(var[2] == 30);
    }
}

```

Yep, I tried this version too and it works. Also in my true program when I try...catch in the same function it works. I had problems only when I threw from inside a function and the catch was in the function calling the first one.
(my code is thousands of lines, it's no use to link it here, so I went for a fast description).

Anyway, the probably not orthodox way I use exceptions is like this:
if I have an input file that asks to specify sites in a lattice of dimension NxM, when I do a check to see if the site from the input actually belong to this lattice (row € [1,N], column € [1,M]), if the check fails I throw an exception of type
```

typedef struct
{
      unsigned short int TypeOfError;  // ID of some specific error
     unsigned short int InputLine;  // line in the file where the wrong input is
     unsigned short int Row;
     unsigned short int Column;
} myMADexception;

```
Btw, I also use them the normal way (to catch real exceptions). :p

---

