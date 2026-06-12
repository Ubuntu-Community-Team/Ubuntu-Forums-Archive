---
title: "variables definition"
date: 2011-04-17
forum: Programming Talk
---

### Post by ubu@ on 2011-04-17
hello world,

if I define a *int* in the *for* loop, will the compiler optimise it and define it once? and there is other way to check optimisations like that?

thanks, 
ubu@

[using "visual c++" IDE] 

example:
for(int i=0; i<1000; i++){
     [COLOR=Red]**int x = foo();**[/COLOR] 
     x = x + i;
goo(x);
  }

---

### Post by dwhitney67 on 2011-04-17
Why not start by optimizing it by yourself, rather than depend on a compiler?

```

for(int i=0; i<1000; ++i)
{
   goo(foo() + i);
}

```

---

### Post by simeon87 on 2011-04-17
> **ubu@ said:**
> hello world,

if I define a *int* in the *for* loop, will the compiler optimise it and define it once? and there is other way to check optimisations like that?

thanks, 
ubu@

[using "visual c++" IDE] 

example:
for(int i=0; i<1000; i++){
     [COLOR=Red]**int x = foo();**[/COLOR] 
     x = x + i;
goo(x);
  }

In your example, how should the compiler *know* that it can move that declaration out of the loop? What if foo() makes use of mutable state and therefore, that x could be different each time through the loop? If you know that foo() returns the same value each time it is called, you should move it out of the loop yourself to be sure.

---

### Post by NovaAesa on 2011-04-17
Get the compiler to compile to assembler code rather than an executable, and you can check what optimizations have been done yourself. How to do this using VC++, I would have no idea though, I only know how to do it using GCC.

---

### Post by MadCow108 on 2011-04-17
> **simeon87 said:**
> In your example, how should the compiler *know* that it can move that declaration out of the loop? What if foo() makes use of mutable state and therefore, that x could be different each time through the loop? If you know that foo() returns the same value each time it is called, you should move it out of the loop yourself to be sure.

if you mark it *const* it can do that
int foo() __attribute__((const));
(gcc syntax, will not work with visual c++ compiler)

for certain loops not messing with global memory *pure* will also work.
and for very simple functions it can even determine that by itself
gcc 4.6 has a -Wsuggest-attribute flag to help you find potential pure/const candidates


of course it will compile bad code if the function is not really pure or const

---

### Post by ubu@ on 2011-04-19
> **simeon87 said:**
> In your example, how should the compiler *know* that it can move that declaration out of the loop? 
I meant,

example:
```
for(int i=0; i<1000; i++){
     int x = foo(); 
     x = x + i;
     goo(x);
  }
```after optimisation:
```
int x;
for(int i=0; i<1000; i++){
      x = foo(); 
      x = x + i;
      goo(x);
   }
```> **NovaAesa said:**
> Get the compiler to compile to assembler code rather than an executable 

Thanks. I will.

> **MadCow108 said:**
> int foo() __attribute__((const));

*foo() *is not constant. there are some global variables *foo()* is using. but  I will use that technique for other functions.

---

### Post by Arndt on 2011-04-19
> **ubu@ said:**
> I meant,

example:
```
for(int i=0; i<1000; i++){
     int x = foo(); 
     x = x + i;
     goo(x);
  }
```after optimisation:
```
int x;
for(int i=0; i<1000; i++){
      x = foo(); 
      x = x + i;
      goo(x);
   }
```


In what way does this represent an optimization? The declaration as such does not consume any runtime resources - it points out one memory cell (or more likely, register) as the place for x.

---

### Post by ubu@ on 2011-04-21
> **Arndt said:**
> ...The declaration as such does not consume any runtime resources ...

So what your are saying, is that there is **no difference** ,better or worse, between these two:

```

int x;
for (int i=0; i<1000; i++){
      x = foo();
      goo(x+i);
}
``````

for (int i=0; i<1000; i++){
      int x = foo();
      goo(x+i);
}
```No difference in cycles number? number of assembly lines? this program is going to be written on a chip, and this differences are really important? these command is all what this chip is going to do in its life. so every cycle is matter. 

thanks,
ubu@

---

### Post by Arndt on 2011-04-21
> **ubu@ said:**
> So what your are saying, is that there is **no difference** ,better or worse, between these two:

```

int x;
for (int i=0; i<1000; i++){
      x = foo();
      goo(x+i);
}
``````

for (int i=0; i<1000; i++){
      int x = foo();
      goo(x+i);
}
```No difference in cycles number? number of assembly lines? this program is going to be written on a chip, and this differences are really important? these command is all what this chip is going to do in its life. so every cycle is matter. 

thanks,
ubu@

If it's really that important, you should not believe what anyone here tells you. Use the -S flag with the compiler and look what is actually produced (with maximal optimization, obviously), and improve it if necessary by writing in assembler.

But I'd guess that even if there is a difference, you can save more cycles by looking at what goo does.

---

### Post by ubu@ on 2011-04-22
> **Arndt said:**
> ...Use the -S flag with the compiler and look what is actually produced...

thanks. I will.

---

