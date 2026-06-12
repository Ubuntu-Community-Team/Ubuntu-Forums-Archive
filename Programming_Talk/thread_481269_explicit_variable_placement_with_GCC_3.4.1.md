---
title: "explicit variable placement with GCC 3.4.1"
date: 2007-06-22
forum: Programming Talk
---

### Post by tomane on 2007-06-22
Hi everyone.

Is it possible to instruct gcc to place (or at least try to) a variable in a specific location?
I'm using a port of gcc3.4.1 for the microblaze architecture.

I could use something like
```
#define MY_VAR (*(volatile int32_t *)0x12345678)
MY_VAR = .... ;
```but It left me wondering if gcc would be able to generate optimal code if I could instruct it to place a variable in a specific address like:
```
int32_t my_var [some directive to say the location];
my_var = .... ;
```Is this possible? Or should I just move along using the address dereferencing manner?

cheers,
--to

---

### Post by aks44 on 2007-06-22
The so called **placement new** does this :

```
volatile int32_t* myVar = new((void*)0x12345678) int32_t;
```

If you don't want to bother dereferencing the pointer everytime you use it, you can do something like :

```
volatile int32_t* myVarPtr = new((void*)0x12345678) int32_t;
volatile int32_t& myVar = *myVarPtr;
```


However, every access to the variable involves one indirection more than your first proposition (the #define).

The question being : does your solution provide a significant performance enhancement? OTOH it obviously makes it harder to maintain the program.
As far as I'm concerned, I'd go with the **placement new** option., as it is way cleaner.

Remember: premature optimization is the root of all evil ;)

---

### Post by tomane on 2007-06-22
Thanks aks44,

I'll stick to the #define's and avoid the selling my soul to the devil :D
The "variables" are registers of a peripheral which I was trying to access in a "transparent" way but it doesn't seem worth the effort.

Your solutions look like C++ but I'm only using C and look like too much trouble for what I need.

One thing in your post caught my eye...
what's the difference between an int32_t and an int32_t& ?
Is int32_t& some kind of dereferenced pointer variable for which I can assign the address? Some weird stuff you got there :)
They seem to be accessed in the same manner, but apparently I can change the address of an int32_t& ? I never saw such thing in C :)

cheers,
--to

---

### Post by aks44 on 2007-06-22
My bad, I didn't realize that you were asking for C advice, not C++. My post was indeed a C++ solution, sorry for that.

As far as C goes, I believe your #define solution is fine, you can hardly do better.


FWIW, the & thing is a C++ type modifier, called a **reference**, it works almost like pointers but
- you must set the address at initialization (it is illegal to have a non-initialized reference)
- you can't change the address during the variable's lifetime
- a reference MUST point to a valid object / variable (ie. there is no "null reference" contrary to pointers)
- you don't have to dereference it (no need to prefix the variable with * in order to access its contents)

IOW, a reference is really an alias of another variable, but has the same semantics than pointers when a function takes it as an argument.

eg. both functions below are equivalent in C++ :

```
void pointer_function(int* ptr)
{
  assert(ptr!=NULL);
  *ptr = 123456;
}

void reference_function(int& ref)
{
  ref = 123456;
}

void usage_example()
{
  int myVar = 0;
  pointer_function(&myVar);
  reference_function(myVar);
}
```

---

### Post by tomane on 2007-06-22
I see, thanks for the explanation, I almost got it all except the part that I can't change the address of type& after it has been declared.
Yep, I guess I'll be using the #defines all the way. On my first post I was looking more for some kind of gcc extension which would allow to control the location of the variable. But on a second thought, using a #define ends up being a little more portable and even clean.

Cheers,
--to

---

