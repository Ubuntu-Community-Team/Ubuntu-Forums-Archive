---
title: "[SOLVED] why C instead of C++ in the kernal"
date: 2007-09-15
forum: Programming Talk
---

### Post by nonewmsgs on 2007-09-15
i remember reading about making a custom kernal and you need an older version of GCC and it's in C.    I am by no means an expert in C++, and i my knowledge of C is a few commands that are C++ only so i know not to use them and some vague memory of malloc, calloc, and free.

why is the kernal in C instead of C++?  is it because the original kernal was in C?  are there any advantages to having it in C? and why the old gcc instead of the new one and why don't the newer gcc optomizations work for rebuilding it?

---

### Post by samjh on 2007-09-15
First there was Unix, written in Assembly.

Then there was Unix, re-written in C.

Then there was Minix, which was derived from Unix, and also written in C.

Then there was Linux, which was derived from Minix, and yet again written in C.

Then Linux continued to be developed, using C.  In the early days of LInux, C++ was immature and not standardised.  Thus it would not have been wise to use C++.

After some two decades of accumulated C code, it's hard to switch to any other language, including C++.

C++ is slightly slower than C, and the quality of C++ compilers including g++, were less than mainstream C compilers, especially gcc.

---

### Post by nonewmsgs on 2007-09-15
> **samjh said:**
> First there was Unix, written in Assembly.

Then there was Unix, re-written in C.

Then there was Minix, which was derived from Unix, and also written in C.

Then there was Linux, which was derived from Minix, and yet again written in C.

Then Linux continued to be developed, using C.  In the early days of LInux, C++ was immature and not standardised.  Thus it would not have been wise to use C++.

After some two decades of accumulated C code, it's hard to switch to any other language, including C++.

C++ is slightly slower than C, and the quality of C++ compilers including g++, were less than mainstream C compilers, especially gcc.

thanks :D  Writing an OS entirely in assembler sounds like some kind of torture.  i can only imagine what those people have gone through.

it's neat to learn things like C is actually faster.  i never knew that.  it makes sense about being written since it was ANSI compliant ages before C++ with gcc being superior to gpp.

---

### Post by HermanAB on 2007-09-15
You can get good information on the problems inherent in C++ from the pages of Hans Boehm:
[http://www.hpl.hp.com/personal/Hans_Boehm/gc/](http://www.hpl.hp.com/personal/Hans_Boehm/gc/)
[http://www.hpl.hp.com/personal/Hans_Boehm/gc/issues.html](http://www.hpl.hp.com/personal/Hans_Boehm/gc/issues.html)

The chief problem of C++ is a design flaw: It has no way to deterministically decide when an object can be freed.  If you free an object while it is still in use, the system will fail catastrophically.

Cheers,

H.

---

### Post by ryno519 on 2007-09-15
> **HermanAB said:**
>  If you free an object while it is still in use, the system will fail catastrophically.

As my former professor used to say...

"SO DON'T ******* DO THAT!" :P

Personally, I'd prefer to free my memory myself, rather then let a garbage collector do it.

---

### Post by CptPicard on 2007-09-15
My view on this would essentially be that a lot of the handy things that make C++ nicer for application development are high-level enough that in kernel development you can't make use of them, as you're coding them to begin with. Consider the standard library and iostreams for example.

Also, I am not completely 100% positive on this, but I am not sure how well the increased compiler-created artifacts that have to do with classes would sit inside kernel code. For example virtual functions and polymorphism are one of C++'s raisons d'être, but they make the compiler create the virtual function call table behind the scenes, which already sounds like a bit too much of abstraction for kernel code.

Same goes with a lot of the other C++ programming paradigms... in kernel code you're just better off playing with raw function pointers instead of references to classes, as you're down to the hardware anyway... if you have to strip C++ down so much that you can pretty much just use "classes as structs with methods", why not use plain C?

And about C++ being slower than C... well... C++ is nice because you only pay for what you use. You can essentially write C-speed code in C++, but generally the decreased speed comes from added abstraction and the ways you code when you make use of C++'s features. For example a function call is of course a bit slower through a virtual table lookup instead of directly.

> 
The chief problem of C++ is a design flaw: It has no way to deterministically decide when an object can be freed. If you free an object while it is still in use, the system will fail catastrophically.


You don't know that of C's blocks of memory on the heap either, it's not a C++ flaw per se :)

---

### Post by HermanAB on 2007-09-15
Well, while I can relate to the prof's comment of "don't *** do that", the problem is that there is no deterministic solution, unless you count never freeing anything as a solution, or use a garbage collector as a brute force solution.

The bottom line is that you should not use C++ for a high reliability application unless you combine it with Boehm's or similar garbage collector.  This is certainly one of the major reasons why kernel code is written in flat C and not ++.

Cheers,

H.

---

### Post by ryno519 on 2007-09-15
> **HermanAB said:**
> Well, while I can relate to the prof's comment of "don't *** do that", the problem is that there is no deterministic solution, unless you count never freeing anything as a solution, or use a garbage collector as a brute force solution.

The bottom line is that you should not use C++ for a high reliability application unless you combine it with Boehm's or similar garbage collector.  This is certainly one of the major reasons why kernel code is written in flat C and not ++.

Cheers,

H.

Ahhhhhhhh... What? Never freeing anything? What?

As well as memory being freed at the end of the scope, you can free a pointers memory whenever you want, but chances are if it's a pointer it's going to be around for more than a single function call, so you probably wouldn't want a garbage collector playing with it anyways.

I wouldn't want an application that has to be highly reliable to USE a garbage collector like that. If it needs to be highly reliable I'll handle the dynamic memory myself. I know when it's created and when it needs to be freed. That's the solution. You FREE your memory YOURSELF. It's not that difficult of a concept. For every new, you have a delete. That's one of the first things you learn as a C++ developer.

I don't need to stinkin' garbage collector.

---

### Post by nonewmsgs on 2007-09-15
ok im getting a little confused by the advanced garbage collection stuff.

in C you type free() and everything's fine
in C++ you delete newVariablesOrPointers or use the destructor.
and it goes away, or is the point that for some reason they're broken :???

---

### Post by CptPicard on 2007-09-15
I still don't quite understand the point... how is C any better? new and delete are just malloc and free in disguise, with the difference that they run constructors and destructors.

If in C you free a location of memory while it is being still in use, you get equally serious trouble, and both languages make you do your memory management manually. Invalid pointers are always bad.

And in particular, how is using a GC which is, by the way, a deterministic algorithm (haven't heard of randomized GCs and its even quite *predictable* in its reference counting implementations) -- going to make this situation better especially for a high-reliability piece of code? If I were writing something really high-reliability, I'd do my own memory management and make sure I do it right, instead of letting some outside GC manage my memory in ways I can't directly control... the Boehm GC is probably written in C++ too, by overriding new, so how exactly does it get around the problem? :)

I vaguely recall reading somewhere that destructor order can be undefined somewhere, sometimes, but it's not exactly the same issue, and adding GC is not going to do anything about it.

---

### Post by nonewmsgs on 2007-09-15
> **CptPicard said:**
> 

Also, I am not completely 100% positive on this, but I am not sure how well the increased compiler-created artifacts that have to do with classes would sit inside kernel code. For example virtual functions and polymorphism are one of C++'s raisons d'être, but they make the compiler create the virtual function call table behind the scenes, which already sounds like a bit too much of abstraction for kernel code.


also i don't understand that.  why would it be too much abstraction? is that because of the speed/size increase?

---

### Post by ryno519 on 2007-09-15
> **nonewmsgs said:**
> ok im getting a little confused by the advanced garbage collection stuff.

in C you type free() and everything's fine
in C++ you delete newVariablesOrPointers or use the destructor.
and it goes away, or is the point that for some reason they're broken :???

No, it's not broken. :)

Garbage collection basically will automatically free your memory when it determines you no longer need it. Its big selling point is that it can reduce development time, sometimes by a significant amount. The other thing it has going for it is it can reduce memory leaks. The down side is it adds more overhead to your code and can make it somewhat slower. I prefer freeing my own memory, especially for personal projects where deadlines are not a factor.

Word to the wise. DO NOT PUT A GARBAGE COLLECTOR IN A KERNEL! I REPEAT... DO NOT PUT A GARBAGE COLLECTOR IN A KERNEL! You have been warned. ;)

---

### Post by CptPicard on 2007-09-15
> **nonewmsgs said:**
> why would it be too much abstraction? is that because of the speed/size increase?

Certainly not because of a speed issue anymore, and I'm just speculating here anyway. :) But C++ binaries have all sorts of little features C ones don't... symbol name mangling comes to mind. And the vtable I mentioned... it's been a long time since I wrote anything low-level, but at least back then hardware liked to play with bare function ptrs, instead of hooking an interrupt up to some polymorphized method on a class. :)

Anyway, I am sure that you *could* write at least a big part of a kernel in C++. So the answer to why the Linux kernel isn't written in C++, is that it .. isn't. :) I suspect that using a simpler language lets you feel like you're coding closer to the iron anyway.

> 
Word to the wise. DO NOT PUT A GARBAGE COLLECTOR IN A KERNEL!

Funny, considering it's the OS's job to keep track of memory it's been handing out to processes... would this GC then be forced upon processes too, as there would be no other way for a kernel to know when it can start cleaning up? :)

---

### Post by ryno519 on 2007-09-15
> **CptPicard said:**
> Certainly not because of a speed issue Funny, considering it's the OS's job to keep track of memory it's been handing out to processes... would this GC then be forced upon processes too, as there would be no other way for a kernel to know when it can start cleaning up? :)

I suppose it would have to be. Now my brain hurts. :)

---

### Post by thk on 2007-09-15
You might try:

[http://www.tux.org/lkml/#s15-3](http://www.tux.org/lkml/#s15-3)

---

### Post by slavik on 2007-09-16
1. correction: Linux is not derived from Unix. Ideas are, not the code
2. C++ brings nothing to the table that C cannot handle. An example would be having a custom list. Sure, in C++ you can inherit from std::list and add stuff to it, but this brings much overhead, besides in C you can "build just what you need."

Java for example has a method in lists to check if an element exists, you might not need this, so why include it? (this is only an example).

it's feature vs. size. features add size.

the linux kernel (2.6.20-16-generic amd64 on my system) is 1.7Mbytes big. The size of the /lib/modules/2.6.20-16-generic/ is 105Mbytes. You could probably cut down the kernel into less than a megabyte (by getting rid of things you don't need) for an embedded application (or a microwave)

---

### Post by aks44 on 2007-09-16
One thing one must not forget about C++ is that neither name mangling nor the ABI are standardized. Using C++ for a kernel would practically forbid anyone to use any other compiler than the one used to compile that kernel.

Plus, even though *most* modern languages are OO, that is not true of *all* languages.

C is the lowest common denominator between all languages (on an architectural POV), its ABI and naming scheme are well standardized, so it is the only sane choice. Anything else would lock some language out.


> **HermanAB said:**
> the problem is that there is no deterministic solution, unless you count never freeing anything as a solution, or use a garbage collector as a brute force solution.

Aaah, the good ol' GC argument. LMAO.

C++ *has* a deterministic way of freeing objects, contrary to *most* other languages. That concept is called RAII, and is way more deterministic than any garbage collector could ever be. Plus it is way cheaper in terms of overhead (in fact, if no exception is thrown there is *no* overhead compared to a manual delete).

And garbage collection is certainly not deterministic. I for one don't want my now useless objects to randomly hang around in memory until the GC condescends to pop in, at which point it will use resources that I don't want it to use anyway (see Java's random freezes when the GC pops in).

However I can understand that some programmers can't produce but garbage, so they indeed need something to collect it. :D


```
#include <memory>
int main()
{
  std::auto_ptr<Bar> bar( new Bar() );
  return 0;
}
```

For your own edification, this code has no memory leak, and the new'ed object will be deterministically destroyed when bar goes out of scope. Not before, not after, just at the right moment.


> **HermanAB said:**
> The bottom line is that you should not use C++ for a high reliability application unless you combine it with Boehm's or similar garbage collector.  This is certainly one of the major reasons why kernel code is written in flat C and not ++.

FWIW, unlike C++, C itself suffers from the "flaw" you mentionned. No offense meant, but you don't seem to be aware of how things really work.


> **ryno519 said:**
> For every new, you have a delete. That's one of the first things you learn as a C++ developer.

Not really. For every new, you should have a smart pointer. No need to delete manually then. :)
In fact, *not* using RAII is the best way to write exception-unsafe code and to end up with resource leaks.

---

### Post by ryno519 on 2007-09-16
> **aks44 said:**
> Not really. For every new, you should have a smart pointer. No need to delete manually then. :)
In fact, *not* using RAII is the best way to write exception-unsafe code and to end up with resource leaks.

Yeah, but when you get right down to it a smart pointer is just an object that is able to determine the number of copies of itself and then call a dispose method when that last copy goes out of scope, in which case it will delete the pointer itself. :)

I would like to point out that you should ideally use RAII for memory management, but there are cases when that's just not going to work and you should know how to deal with that memory.

Personally, I don't deal with that auto_ptr mumbo-jumbo. I made my own smart pointer for my personal toolkit which IMHO is much better. :)

Basically, it's a standard reference counting smart pointer, but it also has a second template value. The first of course being the type of the object, but the second being a policy. For instance, consider the class Foo.

```


class Foo
{

public:

    Foo();
    virtual ~Foo();

    virtual void Dispose();

};


```

Now you won't run into this in GNU/Linux too much, but you will find it more in Windows (DirectX objects for instance). In this case, for whatever reason using the destructor without calling Dispose will cause a memory leak. So you can't simply throw Foo in an auto_ptr or any Boost smart pointer. So with my code you would create a policy.

```

struct DisposePolicy
{
    template<T>
    void on_destruct(T* pObj)
    {
        pObj->Dispose();
    }

};

```

And then when creating the smart pointer it goes something like this.

```

SmartPointer<Foo, DisposePolicy> pFoo(new Foo());

```

That will call the dispose method (hopefully ;) ) instead of calling delete on it and causing a memory leak. And of course, if you leave out the second template parameter, it will use the default policy which simply calls delete on the object.

```

SmartPointer<Foo> pFoo(new Foo());

```

---

### Post by CptPicard on 2007-09-16
> **aks44 said:**
> 
And garbage collection is certainly not deterministic. I for one don't want my now useless objects to randomly hang around in memory until the GC condescends to pop in

Just need to chime in for this bit as it was essentially me who said GC is deterministic... yes, I perfectly well understand that from a programmer's perspective GC can be so unpredictable as to essentially behave as if it were nondeterministic, but it's certainly not throwing dice or doing anything genuinely nondeterministic :p

---

### Post by ryno519 on 2007-09-16
> **CptPicard said:**
> but it's certainly not throwing dice

Well, the Java one is. ;)

Essentially the Java GC rolls three dice while the memory it is trying to delete defends by rolling two dice. The GC then matches up the highest two pair and for each lower or equal value the GC loses an army. If the GC roles higher on either two dice he eliminates a defending army. The goal is to eliminate all defending armies from the memory location.

Edit: Take a card at the end of the turn. Collect a matching set of three cards to trade them for additional armies.

And that's how Java works. :)

---

### Post by aks44 on 2007-09-16
> **ryno519 said:**
> I made my own smart pointer for my personal toolkit

Well, it's RAII anyway, so I guess my point still holds true. ;)



As a side note, two-step finalization is just as bad design as two-step initialization IMHO. But indeed at times one has to cope with the shortcomings of badly designed libraries.

Just because *you* are not responsible for the original flaw doesn't render such a design less flawed... Fortunately you have managed to somewhat automate it, making it a bit less error-prone. :)

---

### Post by ryno519 on 2007-09-16
> **aks44 said:**
> Well, it's RAII anyway, so I guess my point still holds true. ;)

Haha, sure. :)

> As a side note, two-step finalization is just as bad design as two-step initialization IMHO. But indeed at times one has to cope with the shortcomings of badly designed libraries.

Just because *you* are not responsible for the original flaw doesn't render such a design less flawed... Fortunately you have managed to somewhat automate it, making it a bit less error-prone. :)

I'll agree there. The funny part is I wrote that smart pointer to cope with a Microsoft library call which required a release method be called to free the memory.

---

### Post by slavik on 2007-09-16
> **ryno519 said:**
> Well, the Java one is. ;)

Essentially the Java GC rolls three dice while the memory it is trying to delete defends by rolling two dice. The GC then matches up the highest two pair and for each lower or equal value the GC loses an army. If the GC roles higher on either two dice he eliminates a defending army. The goal is to eliminate all defending armies from the memory location.

Edit: Take a card at the end of the turn. Collect a matching set of three cards to trade them for additional armies.

And that's how Java works. :)
I didn't know that Java's GC played risk ...

---

### Post by ryno519 on 2007-09-16
> **slavik said:**
> I didn't know that Java's GC played risk ...

And now you do.

---

### Post by nonewmsgs on 2007-09-16
that would have been my sig, but it whined that it was more than 4 lines and as josef II would have said "contained too many notes"

> **ryno519 said:**
> Well, the Java one is. ;)

Essentially the Java GC rolls three dice while the memory it is trying to delete defends by rolling two dice. The GC then matches up the highest two pair and for each lower or equal value the GC loses an army. If the GC roles higher on either two dice he eliminates a defending army. The goal is to eliminate all defending armies from the memory location.

Edit: Take a card at the end of the turn. Collect a matching set of three cards to trade them for additional armies.

And that's how Java works. :)

---

### Post by Ramses de Norre on 2007-09-17
> **ryno519 said:**
> Well, the Java one is. ;)

Essentially the Java GC rolls three dice while the memory it is trying to delete defends by rolling two dice. The GC then matches up the highest two pair and for each lower or equal value the GC loses an army. If the GC roles higher on either two dice he eliminates a defending army. The goal is to eliminate all defending armies from the memory location.

Edit: Take a card at the end of the turn. Collect a matching set of three cards to trade them for additional armies.

And that's how Java works. :)

Your post is as funny as it is unnecessary... Bashing java seems a cool thing to do on these forums but it isn't really functional in this discussion.
If java was as bad as you want to make people believe, it wouldn't be so widespread as it actually is.

---

### Post by ryno519 on 2007-09-17
> **Ramses de Norre said:**
> Your post is as funny as it is unnecessary... Bashing java seems a cool thing to do on these forums but it isn't really functional in this discussion.
If java was as bad as you want to make people believe, it wouldn't be so widespread as it actually is.

It's just a joke, buddy. Not a good joke, perhaps, but a joke nonetheless.

Sheesh... where do these humorless drones come from?

---

### Post by Ramses de Norre on 2007-09-17
> **ryno519 said:**
> It's just a joke, buddy. Not a good joke, perhaps, but a joke nonetheless.

Sheesh... where do these humorless drones come from?

I appreciated the humor and had a good laugh, but I wonder why everyone needs to bash on java here....

---

