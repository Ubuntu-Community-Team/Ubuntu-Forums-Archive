---
title: "CPP question: difference of const pointers and references"
date: 2007-10-08
forum: Programming Talk
---

### Post by Dislimit on 2007-10-08
C++ question: difference of const pointers and references

What's the difference of const pointers (not pointer to const) and references (except syntax)? 
Seems they have duplicated functions. Both points to some memory locations 
and both unchangeable. Basically I'm asking why shall we have both.

C a();

//const pointer:
C* const pa=&a;

//reference:
C& ra=a;

---

### Post by LaRoza on 2007-10-08
> **Dislimit said:**
> CPP question: difference of const pointers and references

What's the difference of const pointers and references (expect syntax)? 
Seems they have duplicated functions. Both points to some memory locations 
and both unchangeable.

A reference can change, and be reassigned to reference another value. A const anything can not change. There are many cases in programming where two or more things are similar, but have different uses. Use const data when it should not change. 

The main advantage is that the compiler will catch any attempts to violate rules and give an error. Let the compiler catch errors for you, not the user.

---

### Post by ryno519 on 2007-10-08
> **LaRoza said:**
> The main advantage is that the compiler will catch any attempts to violate rules and give an error. Let the compiler catch errors for you, not the user.

That's essentially it, right there. As a rule of thumb you should use const reference instead of const pointer unless you have a reason. No sense making the guy using your code pass their object by memory address when you're not doing anything that requires pointer arithmetic.

---

### Post by hod139 on 2007-10-08
> **LaRoza said:**
> A reference can change, and be reassigned to reference another value. A const anything can not change. 

> **ryno519 said:**
> That's essentially it, right there. As a rule of thumb you should use const reference instead of const pointer unless you have a reason. 

These are both wrong statements.  A const pointer (not a pointer to a const) is very similar to a reference.  A reference cannot change, it cannot be rebounded or reseated to another object.  Depending on the type of const, things can change.  A const pointer can change the value of what it is pointing too, but not change what it is pointing too (identical to a reference).  A pointer to a const cannot not change the value of what it is pointing too, but can change what it points too.  A const pointer to a const cannot change the value of what it is pointing too, or change what it is pointing too (similar to a const reference).

Even though const pointers and reference are very similar, pointers and references are very different.

---

### Post by ryno519 on 2007-10-08
> **hod139 said:**
> These are both wrong statements.  A const pointer (not a pointer to a const) is very similar to a reference.  A reference cannot change, it cannot be rebounded or reseated to another object.  Depending on the type of const, things can change (and there there is always the ugly const_cast which can ignore the const protection).  

Even though const pointers and reference are very similar, pointers and references are very different.

Explain how it's a "wrong statement".

---

### Post by hod139 on 2007-10-08
> **ryno519 said:**
> Explain how it's a "wrong statement".
I edited my first post to hopefully clarify.  A const reference is different than a const pointer.  Hopefully my previous post makes that more clear.

---

### Post by ryno519 on 2007-10-08
> **hod139 said:**
> I edited my first post to hopefully clarify.  A const reference is different than a const pointer.  Hopefully my previous post makes that more clear.

Ah, I stand corrected. I misread LaRoza's post and thought his last sentence was in reference to a const reference, instead of any type of const.

---

### Post by aks44 on 2007-10-08
In addition to hod's post (which describes very well the similarities between a const pointer and a reference), I may add that contrary to pointers, there is no such thing as a "null reference".

A good way to choose between reference and const pointer:
- you *need* a pointed-to object? use a reference
- you can have either a pointed-to object or *optionally nothing*? use a const pointer


FWIW if a function in my code takes a pointer as a parameter, it means that it is an optional argument (ie. it can *safely* be passed a null pointer). Otherwise I stick with references.

---

### Post by Wybiral on 2007-10-08
References don't have to be dereferences to grab the pointed value, unlike pointers. You also don't have to reference a variable to assign it's address to a reference "int &y = x;" instead of "int *y = &x;"

```

#include <iostream>

void example1(int &i)
{
    std::cout << i << std::endl;
}

void example2(const int *i)
{
    std::cout << *i << std::endl;;
}

int main()
{
    int x = 20;
    example1(x);
    example2(&x);
}

```

Basically, references BECOME the variable assigned to them, while pointers still just point to the address.

---

### Post by Dislimit on 2007-10-08
Thx Hod for clarifying some brothers' confusion. And thx Aks44 for giving some meaningful difference between const pointers and references. 

Pls excuse me if I have missed anything and allow me to ask again. Is there any other differences (like efficiency or safety) between the two?

---

### Post by hod139 on 2007-10-08
> **Wybiral said:**
> Basically, references BECOME the variable assigned to them

I would emphasize this sentence.  References are an alias to the object, not an object itself.  Taking the address of the reference gives gives the address of the object (referent).  The reference is its referent.

---

### Post by hod139 on 2007-10-08
> **Dislimit said:**
> Is there any other differences (like efficiency or safety) between the two?
Between a const pointer and a reference, the only difference is syntax.  The const syntax in C++ is terrible.

Of course, the differences between references and pointers is huge, so don't confuse those two.

---

### Post by aks44 on 2007-10-08
> **Dislimit said:**
> Is there any other differences (like efficiency or safety) between the two?

A truth that *must not be spoken of* is that under the hood on all architectures (that I know of) references are just syntactic sugar around pointers. But please don't misunderstand me, references are *not* pointers in disguise, for the very reason that the standard specifies it as implementation-dependent (thus a compiler may choose to represent references another way, just dont ask me how ;)).

Performance-wise, you can safely assume that this is the same (ie. access to an object needs an indirection).

Safety-wise, references are "guaranteed" to point to a real object, while pointers can be null (segfault / access violation anyone?). But it needs no more effort to play tricks with references than with pointers:

```
int* ptr = 0;
int& ref = *ptr;
```

Most compilers won't even blink on this, as they won't dereference ptr until ref is really accessed.

I can hear you now: "*wait, here's the way to have a null reference!*". Sorry to disappoint you, but the code above is undefined behaviour as per the standard. Some compilers will "accept" it (because as an optimization they don't dereference until really necessary) but some other compilers will make your machine explode *and* curse your whole family for 666 generations. Take the chance if you dare... ;)


IOW references, just like pointers, are as safe as the programmer's discipline allows them to be.

---

### Post by aks44 on 2007-10-08
> **hod139 said:**
> Between a const pointer and a reference, the only difference is syntax.

Call me picky, but I'll again throw in the "null pointer" thing. So there is indeed another difference than syntax. ;)

---

### Post by hod139 on 2007-10-08
> **aks44 said:**
> Call me picky, but I'll again throw in the "null pointer" thing. So there is indeed another difference than syntax. ;)

Ok, you're picky.    Seriously though, I don't follow how this is a difference between const pointers and references.

```

// Why would you do this!!!!
  int* ptr = 0;
  int& ref = *ptr;  // reference
  int* const ptr_ = &(*ptr); // const pointer
  
   int a = 0;
   //ptr_ = &a; //compiler error, sorry dumb programmer, you made the pointer const and are forever stuck with an exploding pointer

  //std::cout << " ref = " << ref << std::endl; // boom
  //std::cout << " *ptr_ = " << *ptr_ << std::endl; // boom

```Both the const pointer and reference will let you make this mistake, and both will explode when you try to use them.  How is their behavior different?

Note: I understand that in general pointers and references are different, but I fail to see how your example illustrates a difference in behavior between const pointers and references.

---

### Post by aks44 on 2007-10-08
> **hod139 said:**
> I don't follow how this is a difference between const pointers and references.

Testing for a null pointer is defined behaviour (part of the language), while there is no safe way to test for a "null reference" (as they don't exist in C++).

IOW &ref CAN'T return a null pointer in C++. If it does, this is not compliant C++. Here is the difference from my POV.


> **hod139 said:**
> I fail to see how your example illustrates a difference in behavior between const pointers and references.

My whole point indeed was that it's as easy to tinker with references than with pointers, and than none is safer than the other if you're determined enough.
Sorry if I didn't make it clear.

---

### Post by hod139 on 2007-10-08
> **aks44 said:**
> Testing for a null pointer is defined behaviour (part of the language), while there is no safe way to test for a "null reference" (as they don't exist in C++).

I see now, yes that is a very good point.

---

