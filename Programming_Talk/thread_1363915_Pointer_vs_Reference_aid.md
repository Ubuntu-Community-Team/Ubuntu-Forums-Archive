---
title: "Pointer vs Reference aid"
date: 2009-12-25
forum: Programming Talk
---

### Post by Syndacate on 2009-12-25
Hey,

I know C/C++ to a pretty decent extent (enough to work, anyway).  Though I just had a few questions about pointers in general - please don't link me to a FAQ on how they work - I understand that aspect of them.

Problem 1:

When would I use this:
```

void foo(int& var);
// Definition of function

int main() {
   int a = 5;
   foo(a);
}

```

Over the standard way I would do that:
```

void foo(int* var);

int main() {
   int* a = 5;
   foo(a);
}

```

The only difference I know of between the two is if type "int" was a struct (I know it's not, but say it was), and you were to access a data member of it, in the first example, it would be allowed to be accessed via the dot operator, ie.

```
a.value
```

Though as the other is declared as a pointer, it would have to be dereferenced, so:

```
a->value
```
or
```
(*a).value
```

Now when would I use one over the other as they seem to be the same in terms of function.  Both should be on the stack, and pop off on return, correct?  As "new" or "malloc" isn't being used for the pointers because they're static assignments, so there shouldn't be anything on the heap that would cause memory leaks in either of these situations, right?

Problem 2:
Why use syntax like this?
```

void foo(int &*var);

foo(int &*var) {
   (*var)++;
}

int main() {
  int* var = 5;
  foo(var);
  printf("%i",*var);
}

```

That will print "6" - but so will simply creating and passing it as a pointer, and it would work the same way.  Why reference a pointer?

Also, what's the difference between something that was declared as a reference to something (pointing..) and a pointer itself?  Besides the dereferencing, does it do anything?

Problem 3:
Simply:  Is anything besides stuff created with memory commands such as "new" and "malloc" created dynamically on the heap?   A pointer to a primitive (or any pointer created without using a memory command) is simply created on the stack, and would be null unless it's a primitive, correct?

By null I mean if you did:
```

struct containerA {
   int value;
}

struct containerA* conA;
containerA->value = 7; //Would throw error?

```

That would throw an error, right?  Because no space was allocated - fine - makes sense, but why if I did:

```

int* value;
*value = 5;

```

It would be perfectly ok with it?  Is this simply because of the way primitives are treated opposed to objects or non-POD items?

Sorry for all the newb questions, just want to make sure I got the stories straight here as references are kind of weird - they act like pointers with the "pointer aspects" removed, so it could be treated as if it was a standard variable created locally on the stack.

Thanks in advance.

---

### Post by MadCow108 on 2009-12-25
1. a reference acts like a pointer (internally it even is). It just has some restrictions:
a reference can't be reassigned, you can't assign null to it and you can't have pointers to references.
So they are basically abstracted pointers, instead of a pointer to a memory location they are a reference to an object. Mostly you only need the latter.
Also they clean up the syntax by allowing to use the dot operator nearly everywhere instead of a mix of dots and arrows like in C and you don't need the dereference operator.

2. a reference to a pointer (int *& a) [note: the *& are swapped, &* is pointer to reference, not allowed] is nearly the same as a pointer to a pointer (int **a).
it allows the function to change the pointer value itself.
```

void f(int *& a) {
a++;
}
// or
void f2(int ** a) {
(*a)++;
}

main() {
int *a = new int[2];
ar[0] = 1;
ar[1] = 4;

printf("%d\n", *ar); // 1
f(ar);
printf("%d\n", *ar); // 4
// pointer variant:
ar--;
printf("%d\n", *ar); // 1
f2(&ar);
printf("%d\n", *ar); // 4
}

```

3. both  examples are wrong.
In both cases you have a pointer pointing to nothing (aka dangling pointer)
a pointer needs a memory location to point to, or all operations will created errors.
[there are cases in which you can actually get gcc to produce valid code without giving the pointer a location, but that is connected to the way gcc handles classes and should not be done]
This is another place where references are safer.
your code compiles with no errors with pointers, but if you use reference the compiler spot the bug and complain:
```

xy declared as reference but not initialized

```
it will even detect when you try to make a reference to a temporary memory location:
```

int &a = 5;
-> invalid initialization of non-const reference of type 'int&' from a temporary of type 'int'

```
note that the upper works with const references:
```

const int &a = 5;

```
this is because the compiler will extend the lifetime of the object pointed to by const references until the end of the stack frame, instead of the end of the line.

conclusion:
references are similar to pointers but a bit safer to use and with a cleaner syntax.
You should always use references if you don't need the properties of pointers (like pointer arithmetic or polymorphism).
If you do need pointers it is better to use smart pointers provided for example by the boost library: [http://www.boost.org/doc/libs/1_41_0/libs/smart_ptr/smart_ptr.htm](http://www.boost.org/doc/libs/1_41_0/libs/smart_ptr/smart_ptr.htm)
they ease memory management and exception safety.

---

### Post by CptPicard on 2009-12-25
References are best understood IMO as a compile-time "label" for some program entity. They are not real, existing pieces of data during runtime, as pointers are (although the compiler will often, but not always, implement references as pointers, the language does not reflect this to the programmer side).

Whenever you make use of a reference X to some object, the compiler will use X as another name for the object, and where-ever X is used, then what actually is used then strictly *is* the object that is being referred to. It is actually very detrimental to try to see this in terms of some "hidden implementation strategy" as it may lead you to make wrong assumptions. How the compiler makes your referred-to object magically "be there" at the reference usage point, is its own problem.

---

### Post by Syndacate on 2009-12-26
> **MadCow108 said:**
> 1. a reference acts like a pointer (internally it even is). It just has some restrictions:
a reference can't be reassigned, you can't assign null to it and you can't have pointers to references.
So they are basically abstracted pointers, instead of a pointer to a memory location they are a reference to an object. Mostly you only need the latter.
Also they clean up the syntax by allowing to use the dot operator nearly everywhere instead of a mix of dots and arrows like in C and you don't need the dereference operator.

What do you mean they can't be re-assigned.  You mean if I pass a regular int by reference to a function, I can't say var = 0; or something similar?  I'm pretty sure you can, so I think I'm mis-understanding you.

> **MadCow108 said:**
> 2. a reference to a pointer (int *& a) [note: the *& are swapped, &* is pointer to reference, not allowed] is nearly the same as a pointer to a pointer (int **a).
it allows the function to change the pointer value itself.
```

void f(int *& a) {
a++;
}
// or
void f2(int ** a) {
(*a)++;
}

main() {
int *a = new int[2];
ar[0] = 1;
ar[1] = 4;

printf("%d\n", *ar); // 1
f(ar);
printf("%d\n", *ar); // 4
// pointer variant:
ar--;
printf("%d\n", *ar); // 1
f2(&ar);
printf("%d\n", *ar); // 4
}

```

I see, but the same things can be done with regular pointer to pointers, right?

> **MadCow108 said:**
> 
3. both  examples are wrong.
In both cases you have a pointer pointing to nothing (aka dangling pointer)
a pointer needs a memory location to point to, or all operations will created errors.
[there are cases in which you can actually get gcc to produce valid code without giving the pointer a location, but that is connected to the way gcc handles classes and should not be done]
This is another place where references are safer.
your code compiles with no errors with pointers, but if you use reference the compiler spot the bug and complain:
```

xy declared as reference but not initialized

```
it will even detect when you try to make a reference to a temporary memory location:
```

int &a = 5;
-> invalid initialization of non-const reference of type 'int&' from a temporary of type 'int'

```
note that the upper works with const references:
```

const int &a = 5;

```
this is because the compiler will extend the lifetime of the object pointed to by const references until the end of the stack frame, instead of the end of the line.[/CODE]

I see, so in general if I have the option of moving things by pointer or by reference I should opt for the later?

> **MadCow108 said:**
> 
conclusion:
references are similar to pointers but a bit safer to use and with a cleaner syntax.
You should always use references if you don't need the properties of pointers (like pointer arithmetic or polymorphism).
If you do need pointers it is better to use smart pointers provided for example by the boost library: [http://www.boost.org/doc/libs/1_41_0/libs/smart_ptr/smart_ptr.htm](http://www.boost.org/doc/libs/1_41_0/libs/smart_ptr/smart_ptr.htm)
they ease memory management and exception safety.
[/QUOTE]

So basically, don't use pointers unless you really have to?

Any bits of wisdom about the stack vs heap question(s)?

> **CptPicard said:**
> References are best understood IMO as a compile-time "label" for some program entity. They are not real, existing pieces of data during runtime, as pointers are (although the compiler will often, but not always, implement references as pointers, the language does not reflect this to the programmer side).

Whenever you make use of a reference X to some object, the compiler will use X as another name for the object, and where-ever X is used, then what actually is used then strictly *is* the object that is being referred to. It is actually very detrimental to try to see this in terms of some "hidden implementation strategy" as it may lead you to make wrong assumptions. How the compiler makes your referred-to object magically "be there" at the reference usage point, is its own problem.

Ah, I see, almost like a global scoping with a find and replace all to its place of calling...

That makes sense in terms of pointers vs references.

Thanks a lot for the answers thus far, they've been really helpful.  Now anybody up for those stack/heap questions? :-P.

I'll reiterate them better here:
- References basically create pointers, but you don't explicitly allocate the space as you would with a pointer.  Does this mean that it handles the allocation/deallocation with references?
- When you do something along the lines of:
```

char* a = "X";

```

That's perfectly valid but for some oddball reason (probably because it can be resolved at compile time) doesn't require memory allocation, though is the char "X" still created on the heap, as if space was allocated using malloc or something similar?  _Would that pointer still have to be freed?_

- Is anything else besides dynamic data stored on the heap - ie. if my program had no pointers, would anything be on my heap?

Thanks again :)

---

### Post by LKjell on 2009-12-26
You cannot reassign mean you cannot change what the reference is pointing to (Memory address). Because you will just change the value of it.

Stack = static memory allocation. FIFO
Heap = dynamic memory allocation.

---

### Post by Some Penguin on 2009-12-26
There *isn't* allocation/deallocation to worry about with references, not because it's automagic but because it doesn't happen at all -- the reference must be referring to something that already exists and will persist even after the call-by-reference call terminates.

I'll note that pointers can be *very* efficient to handle and rather flexible.  There's something to be said for powerful language features that teach you to be disciplined and careful because you're probably going to have an unpleasant time debugging if you aren't.

---

### Post by Syndacate on 2009-12-26
> **LKjell said:**
> You cannot reassign mean you cannot change what the reference is pointing to (Memory address). Because you will just change the value of it.

Oh, yeah, got ya.  Like a statically pointed pointer.

> **LKjell said:**
> 
Stack = static memory allocation. FIFO
Heap = dynamic memory allocation.

Yeah, I know what they actually are, I took all the CS classes and the like quite a bit ago, but I was just wondering about what went on them in terms of pointers/references - I think in the above I said it correctly, though.

> **Some Penguin said:**
> There *isn't* allocation/deallocation to worry about with references, not because it's automagic but because it doesn't happen at all -- the reference must be referring to something that already exists and will persist even after the call-by-reference call terminates.

That's true, that makes sense, so the stuff is typically on the stack, and since it was passed it'd be "under" where the stack pointer currently is..  Same goes for a reference to a pointer I assume, even if the memory pointed to by the pointer is on the heap, right?

> **Some Penguin said:**
> I'll note that pointers can be *very* efficient to handle and rather flexible.  There's something to be said for powerful language features that teach you to be disciplined and careful because you're probably going to have an unpleasant time debugging if you aren't.

Yeah, I haven't had any leaking programs, but then again, I haven't really made any huge projects which is where leaks usually occur.  Though I do know what you mean.

---

