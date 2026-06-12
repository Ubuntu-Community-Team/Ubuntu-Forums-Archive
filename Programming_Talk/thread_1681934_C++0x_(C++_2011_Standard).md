---
title: "C++0x (C++ 2011 Standard)"
date: 2011-02-05
forum: Programming Talk
---

### Post by liquid87 on 2011-02-05
Hi all what do you guys think of the C++ 2011 standard, and yes I am aware of Qt. Do you think they should incorporate a standard socket library/media library/ any other type library. I am by no means an experienced C++ developer, I would just like to get better and know the best set of libraries when developing. Even though I have not programmed in Java I really appreciate there one stop spot for documentation and all the libraries they support from the get go. If I made any mistakes please correct me if I am wrong, and if you have any tips for a C/C++ developer please share.

:p
[http://en.wikipedia.org/wiki/C%2B%2B0x#Candidate_changes_for_the_impending_standard_update]("http://en.wikipedia.org/wiki/C%2B%2B0x#Candidate_changes_for_the_impending_standard_update")

---

### Post by worksofcraft on 2011-02-05
> **liquid87 said:**
> Hi all what do you guys think of the C++ 2011 standard, and yes I am aware of Qt. Do you think they should incorporate a standard socket library/media library/ any other type library. I am by no means an experienced C++ developer, I would just like to get better and know the best set of libraries when developing. Even though I have not programmed in Java I really appreciate there one stop spot for documentation and all the libraries they support from the get go. If I made any mistakes please correct me if I am wrong, and if you have any tips for a C/C++ developer please share.

:p
[http://en.wikipedia.org/wiki/C%2B%2B0x#Candidate_changes_for_the_impending_standard_update]("http://en.wikipedia.org/wiki/C%2B%2B0x#Candidate_changes_for_the_impending_standard_update")
I don't think software libraries should ever become part of a programming language. Things like media are add on features and highly dependent on the technology you are aiming for.

OTOH very fundamental functions like file I/O and maths and also the various container classes of STL are sufficiently general purpose to be standardized.

From the C++0x standard I've already found things like variadic templates indispensable, but I'm not a big fan of some of the other additions:

Things like lambda expressions and tuples I just don't see what benefit they possibly offer and I think they will simply end up making code much harder to read.

Beyond that IMO char16_t and char32_t are just plain dumb as is the new "smart" reference counting shared_ptr. In the first instance they could have looked to creating a more general purpose solution like Pascal has with it's subrange ordinal types and for the second one they could have scrapped all these dumb auto_ptr things and specified standard behavior for a proper garbage collection mechanism (like they have in Java).

---

### Post by MadCow108 on 2011-02-05
> **worksofcraft said:**
> Beyond that IMO char16_t and char32_t are just plain dumb as is the new "smart" reference counting shared_ptr. In the first instance they could have looked to creating a more general purpose solution like Pascal has with it's subrange ordinal types and for the second one they could have scrapped all these dumb auto_ptr things and specified standard behavior for a proper garbage collection mechanism (like they have in Java).

smart pointers are essential to RAII, the alternative to garbage collection.
It is one of the most important addition of the standard in my opinion.

And there is standard ABI for garbage collection included in the standard so implementations will pop up with time.

---

### Post by worksofcraft on 2011-02-05
> **MadCow108 said:**
> smart pointers are essential to RAII, the alternative to garbage collection.
It is one of the most important addition of the standard in my opinion.

And there is standard ABI for garbage collection included in the standard so implementations will pop up with time.

Ah cool :)
I didn't notice anything about a garbage collector... I'll have to look again.

Reference counting pointer types OTOH have always been easily implemented as an add on library function.

These smart pointers however impose a deceptively heavy run time penalty and the new standard implementation malfunctions with circularly linked garbage so it isn't even a good standard to set :shock:

---

### Post by forrestcupp on 2011-02-05
IMO, if you want a garbage collector, use a language that has one. One of the great things about C/C++ is having power over your memory management. There's no point in turning C++ into Java when we already have a Java.

---

### Post by Simian Man on 2011-02-05
I just can't see looking at C++ and thinking "You know what this language needs?  More features."  Of course things like lambdas, tuples and type inference are awesome, but the real issue is that people are using C++ when it's not the most appropriate tool for the job.  If you want a high-level language, use one.  The people using C++ for what it's really good at by and large won't use the new stuff anyway - heck most of them don't even use most of the features C++ currently has!

---

### Post by worksofcraft on 2011-02-05
> **MadCow108 said:**
> ...
And there is standard ABI for garbage collection included in the standard so implementations will pop up with time.

update:
I checked the [wiki]("http://en.wikipedia.org/wiki/C%2B%2B0x#Allow_garbage_collected_implementations") and all it apears to say about garbage collection is:

> It is implementation defined whether unreachable dynamically allocated objects are automatically reclaimed.


So it isn't really clear whether it will do things like run the collected object's destructors, whether circularly linked garbage will be considered "unreachable", or whether it would be intended more as a kind of safety net than as a substitute for explicit memory management and "smart" pointers.

---

### Post by lisati on 2011-02-05
The idea of libraries has been around for years. I first encountered it as a mechanism for providing standard functionality for helping with things like basic I/O and "built in" scientific/mathematical tools e.g. sin & cosine.

---

### Post by MadCow108 on 2011-02-05
> **worksofcraft said:**
> update:
I checked the [wiki]("http://en.wikipedia.org/wiki/C%2B%2B0x#Allow_garbage_collected_implementations") and all it apears to say about garbage collection is:



So it isn't really clear whether it will do things like run the collected object's destructors, whether circularly linked garbage will be considered "unreachable", or whether it would be intended more as a kind of safety net than as a substitute for explicit memory management and "smart" pointers.

the wiki is not particularly extensive, the actual draft says more.
anyhow the standard implies no specific implementation only a abi, its behavior and some details to ease (the optional) implementation

circular references are no problem for non-naive garbage collector implementations.
But it is complicated by the direct access to pointers in C++. In certain (border) cases you need additional code in your application for the collector
see section 20.9.12 of the current draft and [http://portal.acm.org/citation.cfm?doid=1542431.1542437](http://portal.acm.org/citation.cfm?doid=1542431.1542437)

I don't know how backward compatible implementations will be. Probably old code will not run with garbage collection (e.g. because of destructors)

The whole point of this is to see how it works out in praxis and then possibly standardize it properly next time.

---

### Post by worksofcraft on 2011-02-05
> **MadCow108 said:**
> 
...
circular references are no problem for non-naive garbage collector implementations.


If you have circular references and want to run destructors there will be ambiguity about which destructor should run first. e.g. say one of those destructor uses a reference to something that has already been destroyed it likely results in undefined behavior. :shock:

IDK how it is resolved in other programming languages :confused:

---

### Post by MadCow108 on 2011-02-05
> **worksofcraft said:**
> If you have circular references and want to run destructors there will be ambiguity about which destructor should run first. e.g. say one of those destructor uses a reference to something that has already been destroyed it likely results in undefined behavior. :shock:

IDK how it is resolved in other programming languages :confused:

nvm. too late to think ._.

---

### Post by liquid87 on 2011-02-06
> **forrestcupp said:**
> IMO, if you want a garbage collector, use a language that has one. One of the great things about C/C++ is having power over your memory management. There's no point in turning C++ into Java when we already have a Java.

Totally agree with this statement for IMHO C/C++ is the defacto language in embedded systems.

---

### Post by worksofcraft on 2011-02-06
> **liquid87 said:**
> Totally agree with this statement for IMHO C/C++ is the defacto language in embedded systems.

Yeah, me too :mad:
Same for a lot of those other things... lambdas and shared pointers etc... they don't fit with the concept of the C++ language.
They add an unidentified complexity and run time overhead as well as render code unintelligible.

---

### Post by stinky472 on 2011-03-26
> These smart pointers however impose a deceptively heavy run time penalty  and the new standard implementation malfunctions with circularly linked  garbage so it isn't even a good standard to set :shock:

Smart pointers like scoped_ptr have virtually no runtime penalty. @see original boost benchmarks from which the new standard implementations are based on.

shared_ptr has a very light runtime penalty for reference counting. It's not particularly hidden.

> Same for a lot of those other things... lambdas and shared pointers etc... they don't fit with the concept of the C++ language.

If we take the original conception of C++, I'd agree with you about lambdas. I'm pretty sure Stroustrup did not anticipate anyone trying to do functional programming in C++, and regardless of the additions, functional programming is certainly still quite awkward and ugly.

shared pointers and smart pointers, on the other hand, fit in very strongly with the concept of the language. To understand how essential they are, we have to study RAII. Destructors are often misunderstood because exception-handling is misunderstood. Destructors are not just a convenient, automatic way to clean up resources. They are _essential_ in an exception-handling language which has implicit exits all over a function. Trying to manually clean up resources becomes completely impractical, so any kind of raw resource has to be automatically cleaned up or we have to have try/catch blocks in our code for any code that throws. The whole beauty of C++ over a language like Java (not to say one's better than the other: they both have their pros and cons) is that we don't have to litter our code with try/catch/finally blocks to handle exceptions. We just rely on the destructors of things like smart pointers.

---

