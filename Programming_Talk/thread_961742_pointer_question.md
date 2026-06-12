---
title: "pointer question"
date: 2008-10-28
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-28
so ive leared a decent amount about C/C++ and can understand the code decently and am in the process of making a basic 2d game.  But there is one thing i still dont fully understand...pointers.  i get the syntax and how to use them and stuff but i dont get when there is an advantage to instantiate something as a pointer or a regular object.  same with data types

all the tutorials teach you how to use pointers but not when they are an advantage

thanks

---

### Post by curvedinfinity on 2008-10-28
You should only really care about pointers if you are working "in" memory. Almost always, unless you are working with some kind of binary data, using pointers is optional at best. -- I mean, besides referencing structures/classes and such, but those applications are straight forward.

Here's an example of why you'd want to use pointers:
```

char buffer[128];
int *cursor = (int*)buffer;

*cursor = 200;
cursor++;
*cursor = 120;

send(buffer,128);

```

Etcetera.

---

### Post by mike_g on 2008-10-28
I find that pointers are generally easier to pass around. Also, if you're creating lots of objects holding lot of data you can blow the stack. Using pointers/memory allocation helps deal with this. In C Pointers are essential for linked lists and other data structures that are very useful. Also, pointer arithmetic is nice to be able to use as well sometimes if you want to optimise. I think thats more or less it.

---

### Post by snova on 2008-10-28
They're a cheap way to pass around large amounts of data. Pointers also fit neatly into registers (more or less by definition).

Secondly, all copies of the pointer will refer to the same data, so updating one copy will update them all. Not that that's always a good thing. ;)

---

### Post by night_fox on 2008-10-28
Also, if you call a function with some arguments, copies of all the arguments are passed to the function, and are not passed back. So by passing a pointer to a variable called foo for instance, even if its just something small, foo would get modified. This is useful if you want to return several variables.

---

### Post by jimi_hendrix on 2008-10-28
so lets say im making my galaga clone (space ship shooter for those who dont know) and i get a bunch of little spaceships on screen

its safer/quicker to use pointers than to instantiate the objects?

---

### Post by mike_g on 2008-10-28
I'd use pointers and allocate your objects. No stack issues and you can easily add remove enemies to/from a list when they spawn/die.

---

### Post by dribeas on 2008-10-28
> **jimi_hendrix said:**
> so ive leared a decent amount about C/C++

<rant>That's what you get when C++ is considered a C extension. They are different languages!</rant>

> **jimi_hendrix said:**
> its safer/quicker to use pointers than to instantiate the objects?

It is never safer to use pointers. It may be the only solution, but if you can choose from two solutions and one does not require pointers it will probably be safer.

Performance wise, that depends on the language. Passing pointers around is faster than passing the data structures (C) but in C++ you can pass references, that are just as efficient as pointers and safer.

> **mike_g said:**
> I'd use pointers and allocate your objects. No stack issues and you can easily add remove enemies to/from a list when they spawn/die.

If you want to code C, that is the way. If you are using C++ using STL's std::list<> will provide you the advantages pointed by mike_g with the added value that you don't have to care about object destruction.

```

class EnemyShip { ... }
std::list<EnemyShip> createEnemies()
{
   std::list<EnemyShip> tmp;
   tmp.push_back( "Scout" ); // EnemyShip is allocated inside a node structure in the heap
   tmp.push_back( "Fighter" );
   tmp.push_back( "AnotherScout" );
   return tmp;
} // *

```

The line marked with * deserves attention. While it implies making a new list that is an exact copy of the tmp list and passing it to the caller, the fact is that compilers are allowed to (and they do) optimize away the copy.

Note that if you had allocated the memory in the heap yourself you will need to delete all allocated memory or else you would be leaking resources. std::list<> takes care of it so that you can focus on your algorithms and not on the memory management.

---

### Post by jimi_hendrix on 2008-10-28
> **dribeas said:**
> <rant>That's what you get when C++ is considered a C extension. They are different languages!</rant>


maybe ive looked at both languages :popcorn:

thanks for pointing out the std::list template

---

### Post by dribeas on 2008-10-30
> **jimi_hendrix said:**
> maybe ive looked at both languages :popcorn:

thanks for pointing out the std::list template

The reason I posted that *rant* is that there are different answers for your question depending on your language of choice. Pointers are required in C to get pass-by-reference semantics, but in C++ you do have references. That makes a whole difference on the question of 'when do I use pointers' for each language.

In C++ you should not (even if you can) use pointers to get pass-by-reference semantics in your functions/methods, even if you must in C.

The fact is that I started to write a comprehensive answer on the use of pointers in both languages, but it became huge and unmanageable when you must compare each use of pointers with the tools provided in both languages. I finally gave up after two tries and just left a comment on heap allocation (much smaller scope than the initial question)

---

### Post by CptPicard on 2008-10-30
> **dribeas said:**
> 
The line marked with * deserves attention. While it implies making a new list that is an exact copy of the tmp list and passing it to the caller, the fact is that compilers are allowed to (and they do) optimize away the copy.


Considering that we've been engaging in some C++ discussions, I need to pipe up and point out that the pitfalls of "returning large objects" in C++ is one of my pet hates regarding the language. It is such a typical, simple thing to do in a program, but the point is that one still often needs to really rely on the knowledge that the compiler *will**bypass copy creation. IIRC in g++ if you don't use optimizations, you can easily for example end up in a situation where your object internals get destroyed by destructor when tmp goes out of scope and the caller gets an object copy with broken pointers.

Just trusting the compiler makes me feel queasy, especially when this is not mandated by the language standard, and if you really want to manage the situation yourself, you need to carefully plan your copy constructors, assignment operators... which can, if you're making deep copies, be very costly and architecturally problematic. And if you don't do deep copies, you need to do something like managed pointers, which can even lead you into having to do reference counting for such a simple thing as returning stuff from a function...

Then there's the alternative of using builder methods -- allocating your big object as empty on stack and passing it in instead of returning it. But this doesn't necessarily play well with encapsulation...

I mean, it's a triviality, but C++ makes it *so* hard. Or maybe I just suck :)

---

### Post by Delever on 2008-10-30
Well yeah, that is the problem.

Now I am dealing with it like this:

I keep my objects in hierarchy, parent creates needed child objects, and destroys them when it is destroyed.

The only methods which can return objects as pointers are methods which create them, thats 'factory' methods, and they are strictly marked as such. They are usually part of hierarchy.

However, you can't keep everything in single hierarchy (usually inefficient), so in that case, *top* object from a hierarchy has a methods to get objects and put them back *from outside*, so it can be known if any are in use (reference-counting). Usually i have std::map<object,use_count> inside of hierarchy to track used objects.

I use copy constructors (pass objects instead of pointers), only for simple data objects, which usually do not have any methods. So copy constructors are compiler-generated.

I have only recently started with C++, and any recommendations are welcome :)

---

### Post by dribeas on 2008-10-30
As we have already discussed, there are quite a lot of uninformed prejudice against programming languages, there are with functional languages that you defend and there are with C++. Now I will try to clear erroneous concepts if I can. I will post both the pros and cons of the language so that things are clear.

> **CptPicard said:**
> IIRC in g++ if you don't use optimizations, you can easily for example end up in a situation where your object internals get destroyed by destructor when tmp goes out of scope and the caller gets an object copy with broken pointers.

I don't understand that part above. Whether you use optimizations or not, the result of the execution of the code will be the same (else there is a bug in the optimizer, which has happened before). Optimizations are allowed to change performance (speed/memory/...) but never ever behavior or semantics. 

Now, if you return _pointers_ or references to temporaries/function (auto) variables from a function, whenever the object goes of scope you get a dangling pointer, just as if you keep two pointers to a place in memory and delete the memory through one of them.

> **CptPicard said:**
> Just trusting the compiler makes me feel queasy, especially when this is not mandated by the language standard

g++ does that optimization always, and it is the only optimization I know of that is defined in the standard. You can easily test it

```

struct X
{
   X() { std::cout << "X" << std::endl; }
// [1]
   X( X const & ) { std::cout << "X copy constructor" << std::endl; }
};

X f()
{
   X tmp;
   return tmp;
}

int main()
{
   f();
}

```

You won't see 'X copy constructor' anywhere in the output. The standard requires copy constructors to be exactly that and states that compilers are free (and all current compilers will) optimize the call away.

It is not that there is no copy construction in the code in main() and f(), just that it is optimized away. If you mark the copy constructor private (adding private: at [1]) then the code will not compile. Even if the copy constructor is not really called, the compiler must behave as if it were.

Once again, the standard does not mandate the optimization, but it is quite clear on the expected behavior of the code, and whether the optimization is performed affects only performance, and never behavior.

> **CptPicard said:**
> and if you really want to manage the situation yourself, you need to carefully plan your copy constructors, assignment operators... which can, if you're making deep copies, be very costly and architecturally problematic.

If you need deep copies, in any language you mention you must perform deep copy and it will be as costly. I don't have enough experience with functional programming to provide an example there (there probably is), but choose your language between C, C++, Java, .NET (C# or variants) and the situation is the same. If you must hold two copies of an object, you must do two copies of it. Funny enough in Java you don't only need to create the method for deep copying, but the user must call an specific method (.clone()) for it to work.

I don't really see what is the 'architectural problem', but if you further explain we can discuss it.

> **CptPicard said:**
> And if you don't do deep copies, you need to do something like managed pointers, which can even lead you into having to do reference counting for such a simple thing as returning stuff from a function...

I take that you are calling plain copies 'deep copying', and recefence/pointer copying as 'no deep copies'.

To follow your argument, in C++ you are free to use references, pointers and smart pointers, std::auto_ptr<> in C++03, more of them including std::tr1::shared_ptr<> from TR1 (dating three years ago in 2005). 

In most cases you don't need to return pointers, as returning real copies, as stated above, usually carries no overhead as the copy construction will be optimized if you are returning an temporary or auto variable (variable created in the scope of the block). And yes, it is defined in the standard.

Returning references is only valid as long as the referred object is still alive, which is probably the problem you stated in the beginning, where you talked about temporaries being destroyed and causing all sorts of havoc.

Returning plain pointers (working with plain pointers in general) can be a source of resource of resource leakage or at least headaches as you must keep track of what class or block has responsibility over the deletion of the object.

std::auto_ptr is a not-shared smart pointer. Its semantics state that only one auto_ptr holds control of the given memory. This can be source of unexpected situations as in an assignment both sides of the equals sign change. This has the side effect of inhibiting the use of std::auto_ptr inside STL containers, but once you know this, it is of quite some use.

std::tr1::shared_ptr (or boost::shared_ptr) do reference counting. Now, the programmer does not need to implement reference counting, it is provided by the library. And if you worry about performance (and not programmer's time) then probably this is still much better than many other languages performance.

> **CptPicard said:**
> Then there's the alternative of using builder methods -- allocating your big object as empty on stack and passing it in instead of returning it. But this doesn't necessarily play well with encapsulation...

!!!! wow !!!!! I wonder how many people does what you are saying. I have never done it, I have never seen it in code, and I would advise against it. Most importantly, there are many different solutions that are better than that, and if someone just wants to write bad code, the language won't be a barrier.

> **CptPicard said:**
> I mean, it's a triviality, but C++ makes it *so* hard. Or maybe I just suck :)

If it were as bad as you pointed before, then it would by no means be a triviality, but I don't believe it is. C++ is not as hard as many people see it, but I don't quite like the way the language is being taught (in classes, in books and tutorials) Too often there is a whole amount of emphasis in pointers, probably because they are hard to grasp. This probably make most beginners (and not so beginners) think that pointers are the only solution to everything and in believing so they don't learn the facilities that the language provide.

Finally, I don't think you suck by no means :) For what it is worth, I cannot but say that even if we do not share views, discussing with you can be done in a logic level. You have your position and you defend it by reasoning, not with plain fanaticism. That is valuable and unfortunately, scarce on the internet.

---

