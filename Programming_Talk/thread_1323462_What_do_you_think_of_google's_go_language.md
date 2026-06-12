---
title: "What do you think of google's go language?"
date: 2009-11-11
forum: Programming Talk
---

### Post by whoop on 2009-11-11
Just wondering what you guys think about google's new open source programming language go?
[http://golang.org/](http://golang.org/)

Although I didn't do extensive research I find it rather interesting?
It's not completely what I'm waiting for, though. I am still waiting for an open source C# like language that compiles binary code (that runs without a runtime environment).

I also think go is clean, but tries to be a little too clean at times, making it unnecessarily cryptic.

---

### Post by cszikszoy on 2009-11-11
> **whoop said:**
> I am still waiting for an open source C# like language that compiles binary code (that runs without a runtime environment).
 
What about Vala?  Also Mono applications can be compiled into a standalone binary (all of the referenced parts of the runtime are embedded into the binary).

---

### Post by whoop on 2009-11-11
> **cszikszoy said:**
> What about Vala?  Also Mono applications can be compiled into a standalone binary (all of the referenced parts of the runtime are embedded into the binary).

Cool!!! I'll look into that...

---

### Post by days_of_ruin on 2009-11-11
> **whoop said:**
> Cool!!! I'll look into that...

And unlike C#, with Vala you can actually use GtkBuilder.:D

---

### Post by cszikszoy on 2009-11-11
> **days_of_ruin said:**
> And unlike C#, with Vala you can actually use GtkBuilder.:D

MonoDevelop has a *great* visual GTK designer.

---

### Post by SunSpyda on 2009-11-14
I just took a look at it, and it doesn't look great tbh. Looks like old, dated concepts slightly rehashed. Nothing really that exciting.

It seems to combine the worst points of so many languages, without any of the good points. Also seems inconsistent in areas.

As far as low level programming goes, I think C or even C++ would be far more suitable, & for higher level stuff, I think Vala, Java, C# and the others have more impressive features.

I would have expected better of Google in all honesty.

---

### Post by scourge on 2009-11-14
> **SunSpyda said:**
> I just took a look at it, and it doesn't look great tbh. Looks like old, dated concepts slightly rehashed. Nothing really that exciting.

It seems to combine the worst points of so many languages, without any of the good points. Also seems inconsistent in areas.

As far as low level programming goes, I think C or even C++ would be far more suitable, & for higher level stuff, I think Vala, Java, C# and the others have more impressive features.

I would have expected better of Google in all honesty.

Maybe you could expand those arguments a bit. What exactly are the old, dated, slightly rehashed concepts that make Go suck so much? What are the worst points of other languages that Go combines? Any examples of the inconsistencies?

I find Go very interesting. Some big and small things that I really like:
- Code compiles super fast, and there's no C++ -like dependency hell
- Google claims that the performance is typically within 10-20% of C/C++, so it's suitable for performance critical applications
- The "defer" statement which means I can use RAII like in C++
- Functions can return multiple values
- The ":=" short declaration, which means the compiler derives the type from the expression. Same as "auto" types in C++0x.
- No implicit fallthrough in switch statements
- Untyped constants
- Interfaces that combine the advantages of dynamically typed languages and compile-time type-checking
- The concurrency stuff looks very simple and powerful when compared to threads, mutexes, condition variables, etc.

---

### Post by hockey97 on 2009-11-14
I  think it's stupid. Unless this lango is commonly used with their own OS.

I rather stick with commonly used programming langos. The reason is that if for some reason you need a job as a programmer you will have a hard time finding jobs or work that will require langos that are not commonly used.

C++ is commonly used. The others like python and java ... c etc.. they are used commonly.

C++ beats most because it's been around the longest kinda like windows. If you notice alot of people still use windows even though linux is free. They use what is commonly used. That way their is less fuss and hassle. 

Like if windows has a problem before you know it a patch will be out. Compared to new OS never heard before if you use those you may never see a patch work.

This go lango may catch on only if they make it a common use for their OS and other OS'S Or have  the lango to program or support programming for cellphones easily. 

I am not well experienced in making software but just my thoughts. I just know it boils down to how society embarrasses it. If many people uses it then you will be moving in that direction. Just because their is more support and also jobs out their that will require those langos to know.

So I guess it depends on  the trend. To me I dont fully see what's the difference between go and c++ or any programming lango just the syntax is different but concepts are pretty much the same to some extent.

---

### Post by grayrainbow on 2009-11-14
What in the float hell "open source language" mean?!? Is it got ISO standard, or any kind of standard that everybody could implement? You can say that it use open source RT or open source compiler, but "open source language"...come on, sometimes it's really ugly how companies use the idea of open world to just advertise themselfs! BLAH! It really taste very bad! BLAH!

About the language itself: putting enough money, every library turn into "language" could become as much popular as java/c#, etc. The fast compilation time, when it comes to big projects will be really nice, if it holds for large stuff as well and if the laguage emphasise modular programming(like C/C++ which is the biggest power of header files).

P.S. Clean is everything else but sure not constant when it comes to software. Some people will say that one single hidden pointer dereference is "dirty", other that everything else except functions is "messy".

---

### Post by days_of_ruin on 2009-11-14
> **cszikszoy said:**
> MonoDevelop has a *great* visual GTK designer.

Meh, I have used both and I prefer Glade-3. Stetic can't add as many widgets and is C# only. Either way, right now you can't use GtkBuilder in Gtk# (it is simply not fully implemented) and that is a bad thing.

---

### Post by scourge on 2009-11-14
> **hockey97 said:**
> I  think it's stupid. Unless this lango is commonly used with their own OS.

I rather stick with commonly used programming langos. The reason is that if for some reason you need a job as a programmer you will have a hard time finding jobs or work that will require langos that are not commonly used.

By this logic we should never try anything new, because it's not "commonly used".


> C++ beats most because it's been around the longest kinda like windows.

There are way older languages than C++. Ever heard of a language called Java? It's younger than C++, yet it's more widely used. How come? And Unix is significantly older than Windows, yet almost everyone uses Windows. What I'm saying is that the age of the technology isn't as important as you think when it comes to popularity.


> Like if windows has a problem before you know it a patch will be out.

Yeah, MS is best known for their fast patchwork. :roll:


> This go lango may catch on only if they make it a common use for their OS and other OS'S Or have  the lango to program or support programming for cellphones easily.

What we need is documentation, compilers and debuggers for the common platforms, and enough libraries. If I get all that, then I don't care if nobody else uses the language. BWT, Go code can be compiled for ARM, obviously.


> So I guess it depends on  the trend. To me I dont fully see what's the difference between go and c++ or any programming lango just the syntax is different but concepts are pretty much the same to some extent.

Differences between Go and C++: [http://golang.org/doc/go_for_cpp_programmers.html](http://golang.org/doc/go_for_cpp_programmers.html)
It's not just the syntax that's different.

---

### Post by scourge on 2009-11-14
> **grayrainbow said:**
> What in the float hell "open source language" mean?!? Is it got ISO standard, or any kind of standard that everybody could implement? You can say that it use open source RT or open source compiler, but "open source language"...come on, sometimes it's really ugly how companies use the idea of open world to just advertise themselfs! BLAH! It really taste very bad! BLAH!

I think it's just the OP of this thread, not Google, who's using the term "open source programming language". But I agree with you, it doesn't make any sense.

---

### Post by fiddler616 on 2009-11-14
> **scourge said:**
> I think it's just the OP of this thread, not Google, who's using the term "open source programming language". But I agree with you, it doesn't make any sense.

Open source programming language == {Python, PHP, Perl, Ruby, Mono...} == Compiler/interpreter/etc. are licensed under the GPL or similar.

A proprietary programming language would be something like C#, anything .NET or [Rebol]("http://en.wikipedia.org/wiki/Rebol").

---

### Post by cszikszoy on 2009-11-15
> **fiddler616 said:**
> A proprietary programming language would be something like C#, anything .NET

Mono is GPL v2 and the [C# language is an ECMA standard]("http://www.ecma-international.org/publications/standards/Ecma-334.htm").

---

### Post by Frak on 2009-11-15
> **fiddler616 said:**
> A proprietary programming language would be something like C#

C# is an ECMA standard and Mono is Open Source. A closed source language would be something like [REALBasic]("http://www.realsoftware.com/realbasic/").

---

### Post by nvteighen on 2009-11-15
1. As far as my observation tells me, a language is considered to be "open source" when it's official compiler and runtime are both licensed under an open source license. The "open source" nomenclature is obviously nonsense, because languages have no "source" and somebody could develop a propietary runtime, but it's the way people sometimes call languages like Perl or Python.

2. The issue is whether the language is an international standard or not. Languages that are standarized are automatically "open source" because they allow the creation of non official implementations. This is the case of C, C++ and C#: you've got a standard and people (should) follow it to create a compiler. The C# case is a bit different in the sense that the original compiler and runtime (.NET) is propietary, but there you have Mono...

3. On Go... I've read the website and it honestly seems a really boiled-down version of Objective-C. The main difference between Go and Objective-C is that the later has a reason to exist (create a strict "C with Classes" that doesn't gets into C++'s complexity) and the first, at least for now, seems to be just an excuse by Google to say "hey, we've got our own language!". It doesn't bring anything new yetlike e.g. Clojure (having a Lisp running in JVM might be a great platform in future); I hope they will introduce something new and interesting or humbly stop polluting the already-too-much clouded world of programming languages.

---

### Post by Frak on 2009-11-15
> **nvteighen said:**
> 1. As far as my observation tells me, a language is considered to be "open source" when it's official compiler and runtime are both licensed under an open source license. The "open source" nomenclature is obviously nonsense, because languages have no "source" and somebody could develop a propietary runtime, but it's the way people sometimes call languages like Perl or Python.

2. The issue is whether the language is an international standard or not. Languages that are standarized are automatically "open source" because they allow the creation of non official implementations. This is the case of C, C++ and C#: you've got a standard and people (should) follow it to create a compiler. The C# case is a bit different in the sense that the original compiler and runtime (.NET) is propietary, but there you have Mono...

3. On Go... I've read the website and it honestly seems a really boiled-down version of Objective-C. The main difference between Go and Objective-C is that the later has a reason to exist (create a strict "C with Classes" that doesn't gets into C++'s complexity) and the first, at least for now, seems to be just an excuse by Google to say "hey, we've got our own language!". It doesn't bring anything new yetlike e.g. Clojure (having a Lisp running in JVM might be a great platform in future); I hope they will introduce something new and interesting or humbly stop polluting the already-too-much clouded world of programming languages.
I'll have to agree with u thar.

---

### Post by SunSpyda on 2009-11-15
> **scourge said:**
> Maybe you could expand those arguments a bit. What exactly are the old, dated, slightly rehashed concepts that make Go suck so much? What are the worst points of other languages that Go combines? Any examples of the inconsistencies?

I find Go very interesting. Some big and small things that I really like:
- Code compiles super fast, and there's no C++ -like dependency hell
- Google claims that the performance is typically within 10-20% of C/C++, so it's suitable for performance critical applications
- The "defer" statement which means I can use RAII like in C++
- Functions can return multiple values
- The ":=" short declaration, which means the compiler derives the type from the expression. Same as "auto" types in C++0x.
- No implicit fallthrough in switch statements
- Untyped constants
- Interfaces that combine the advantages of dynamically typed languages and compile-time type-checking
- The concurrency stuff looks very simple and powerful when compared to threads, mutexes, condition variables, etc.

OK, I know little about the language, only taking a brief detour of it, so please correct me if I'm wrong... :)

> Code compiles super fast, and there's no C++ -like dependency hell
This actually sounds quite good. How does the packaging work? Something like C#/Java, or a traditional system like C++ with a few addons to make it more usable?

> Google claims that the performance is typically within 10-20% of C/C++, so it's suitable for performance critical applications
Do you mean it can potentially be 10x faster than C? Is that what you meant by 10% of C's performance, or have I misunderstood? If I understood correctly, then I have great difficulty believing this.

> Functions can return multiple values
Now that is quite handy.

> The ":=" short declaration, which means the compiler derives the type from the expression. Same as "auto" types in C++0x.
Being able to skip a type specifier doesn't seem like a massive advantage to me. A language should either be strongly or loosely typed, not strongly typed with a few bolt-ons to make it more loose. Things like this kind of make me think Google want to make this a all-purpose language, rather than one that's actually really good at any specific thing. It's like it's trying to be JavaScript and C at the same time... and we all know what happens to languages that try stuff like that.

> No implicit fallthrough in switch statements
About time a C-Style language had this!

> Untyped constants
Again, having some parts of a language strong and others loose isn't a great idea. I thought this when I saw Pascal constants as well.

> Interfaces that combine the advantages of dynamically typed languages and compile-time type-checking
Sorry if I'm wrong, but isn't this pretty much the only OOP it has? Seems quite limited if you ask me, even if it is more simple.

> The concurrency stuff looks very simple and powerful when compared to threads, mutexes, condition variables, etc.
I can believe this, seeing as it is such a new language.

**EDIT**

> Any examples of the inconsistencies?
Some examples of the Go site. These could be wrong due to my lack of experience with the language. Okay, I'm nitpicking but...

```

// Both do the same thing.
var i = i2;
i := i2;


// These are both valid...
if a < b { f() }
if (a < b) { f() }

// But one of these isn't?
for i = 0; i < 10; i++ {}
for (i = 0; i < 10; i++) {}

// Again, both so the same thing...
var (i int)
var i int;

// And again...
func f (a int, b int, c int);
func f (a, b, c int);

```

I'm sure I could find more if I looked.

---

### Post by apmcd47 on 2009-11-15
Just wondering as someone who doesn't have the time to compare new languages, how does this compare to Digital Mars' D programming language? I only ask as D also compiles to machine code, uses a variant of import rather than preprocessor/include files and borrows heavily from C/C++.

Andrew

---

### Post by 0cton on 2009-11-15
I am skipping it big time.
It's the segway of programming languages :)

---

### Post by scourge on 2009-11-15
> **SunSpyda said:**
> This actually sounds quite good. How does the packaging work? Something like C#/Java, or a traditional system like C++ with a few addons to make it more usable?

Go's package model uses explicit dependencies for fast build times. This is what the "Go talk" PDF says:
> **Google]The Go compiler pulls transitive dependency type
info from the object file - but only what it needs.

If A.go depends on B.go depends on C.go:
- compile C.go, B.go, then A.go.
- to compile A.go, compiler reads B.o not C.o.
At scale, this can be a huge speedup.[/quote]


> Do you mean it can potentially be 10x faster than C? Is that what you meant by 10% of C's performance, or have I misunderstood? If I understood correctly, then I have great difficulty believing this.

No, I meant that performance is typically only 10-20% slower than C/C++.


> Being able to skip a type specifier doesn't seem like a massive advantage to me.

Every little thing counts. Not only do the short declarations reduce typing, it also means that there's one less find & replace I have to do if the type returned by the expression changes.


> A language should either be strongly or loosely typed, not strongly typed with a few bolt-ons to make it more loose.

Do you mean that a language should either be statically or dynamically typed? I mean Python is strongly typed too...
Anyway, auto types don't take away any of the advantages of static typing - performance and compile-time type-checking - so I don't see why they're bad.


> Again, having some parts of a language strong and others loose isn't a great idea. I thought this when I saw Pascal constants as well.

I think of untyped constants as C's #define constants (which you would surely describe as loose), only better  said:**
> Sorry if I'm wrong, but isn't this pretty much the only OOP it has? Seems quite limited if you ask me, even if it is more simple.

When you really think about it, what other OOP stuff do you need? You've got powerful polymorphism (interfaces) and even a kind of inheritance (methods of anonymous fields are promoted to become methods of the enclosing type).


> Some examples of the Go site. These could be wrong due to my lack of experience with the language. Okay, I'm nitpicking but...

```

// Both do the same thing.
var i = i2;
i := i2;


// These are both valid...
if a < b { f() }
if (a < b) { f() }

// But one of these isn't?
for i = 0; i < 10; i++ {}
for (i = 0; i < 10; i++) {}

// Again, both so the same thing...
var (i int)
var i int;

// And again...
func f (a int, b int, c int);
func f (a, b, c int);

```

I'm sure I could find more if I looked.

I'd definitely call that nitpicking. In just about every language that doesn't require expressions to be parenthesized, you can still do that if you want to. And in C you can also declare and initialize variables in more than one way.

---

### Post by hessiess on 2009-11-15
How does the concurrency support compare to a language with immutable data and luckless concurrency, i.e. clojure.

---

### Post by CptPicard on 2009-11-15
I have not really taken a deep look and I am certainly careful enough not to mouth off anything about a language before actually using it to see how it feels like, but my initial impression is that Go has just some weird, needless rehashing of C to it, annoying keyword additions (func, var -- unless they really serve a deeper purpose in the design, I don't know yet), and the concurrency things could just as well be taken from libraries...

And, in addition to that, it just doesn't move far enough from its C roots... I might be in agreement with nvteighen about objective-C already filling this niche quite well.

> **scourge said:**
> Do you mean that a language should either be statically or dynamically typed? I mean Python is strongly typed too...
Anyway, auto types don't take away any of the advantages of static typing - performance and compile-time type-checking - so I don't see why they're bad.


Hmm, question... do auto types generate different versions of code for each "binding" of the auto type somewhere else in the code? Otherwise it is just an intentionally uninformative opaque word you have to type... whatever type information can be inferred through static code analysis is easily handled by the IDE, so those find-replace issues do not generally bother me at all.. ;)

---

### Post by grayrainbow on 2009-11-15
> Do you mean it can potentially be 10x faster than C? Is that what you meant by 10% of C's performance, or have I misunderstood? If I understood correctly, then I have great difficulty believing this.
10% of the speed of C usually mean that "HelloWorld" run almost as fast as in C ;) When it comes to speed...[http://gcc.gnu.org/install/prerequisites.html]("http://gcc.gnu.org/install/prerequisites.html")


Auto is most useful for generic programming, basicaly C++ template libraries, <put here the biggest problem of templates>, that's why it get into C++0.x. And couse everybody want to be "modern", it's normal to be use in every new mainly explicit type language.

---

### Post by phrostbyte on 2009-11-15
I love it's "object system". :p

It's a fine language and IMO it's "C done right". Hopefully it will see adoption and continued development. Having Google behind it doesn't hurt.

---

### Post by Frak on 2009-11-15
> **phrostbyte said:**
> I love it's "object system". :p

It's a fine language and IMO it's "C done right". Hopefully it will see adoption and continued development. Having Google behind it doesn't hurt.
I'll have to disagree with you on that.

---

### Post by wmcbrine on 2009-11-15
Here's some intelligent analysis, from a guy who works for Google, but not on the Go team:

[http://scienceblogs.com/goodmath/2009/11/googles_new_language_go.php](http://scienceblogs.com/goodmath/2009/11/googles_new_language_go.php)
[http://scienceblogs.com/goodmath/2009/11/the_go_i_forgot_concurrency_an.php](http://scienceblogs.com/goodmath/2009/11/the_go_i_forgot_concurrency_an.php)

---

### Post by kavon89 on 2009-11-15
> **scourge said:**
> 
- Functions can return multiple values


How does this even work?

---

### Post by phrostbyte on 2009-11-15
> **kavon89 said:**
> How does this even work?

Eg:

foo, bar := baz()

Assuming baz returns 2 values.

This is not a new idea though, it's very common in functional languages like Haskell and Scheme to return multiple values (or infinite values via something called a "generator"). There are mathematical constructs called tuples that assist with this.

The really innovative/interesting stuff about Go is in it's type/object system IMO. :P

---

### Post by nvteighen on 2009-11-16
> **wmcbrine said:**
> Here's some intelligent analysis, from a guy who works for Google, but not on the Go team:

[http://scienceblogs.com/goodmath/2009/11/googles_new_language_go.php](http://scienceblogs.com/goodmath/2009/11/googles_new_language_go.php)
[http://scienceblogs.com/goodmath/2009/11/the_go_i_forgot_concurrency_an.php](http://scienceblogs.com/goodmath/2009/11/the_go_i_forgot_concurrency_an.php)

Ok, the first link convinced me that this is a language with very little future on its own (maybe it can have a future because of marketing techniques). Everything I see there is already available in Objective-C: Go's interfaces are ObjC's protocols, Go's "loose" typing is ObjC's (much saner) "id" generic type, the idea of having everything receive a method/message is also a copy, the lack of a type constructor, etc. Except for some little other constructs like **for c:= range chars**, which is present in Python, this is pretty much just a cosmetic change of C or Objective-C.

The sole advantage I see over ObjC is that you don't have to rely on the OpenStep libraries to do anything useful...

---

### Post by phrostbyte on 2009-11-16
> **nvteighen said:**
> Ok, the first link convinced me that this is a language with very little future on its own (maybe it can have a future because of marketing techniques). Everything I see there is already available in Objective-C: Go's interfaces are ObjC's protocols, Go's "loose" typing is ObjC's (much saner) "id" generic type, the idea of having everything receive a method/message is also a copy, the lack of a type constructor, etc. Except for some little other constructs like **for c:= range chars**, which is present in Python, this is pretty much just a cosmetic change of C or Objective-C.

The sole advantage I see over ObjC is that you don't have to rely on the OpenStep libraries to do anything useful...

Doesn't Obj-C still use #include directives?

---

### Post by wmcbrine on 2009-11-16
> **nvteighen said:**
> Ok, the first link convinced me that this is a language with very little future on its ownBut the second link changed your mind. Right? :D

---

### Post by SunSpyda on 2009-11-16
> **phrostbyte said:**
> Doesn't Obj-C still use #include directives?
#import

---

### Post by nvteighen on 2009-11-16
> **phrostbyte said:**
> Doesn't Obj-C still use #include directives?

It allows you to use #include, but #import is much better as it checks for double inclusion.

---

### Post by dsiembab on 2009-12-04
The thing I just love about google projects is that they almost always reinvent the wheel, but instead of wheel they call it something like "round rotator".
The funniest thing is that some people actually believe the self proclaimed hype. "Well I read this article by people who work at google saying go is going to be the best programming language out there." now that's getting the facts, that's funny.:lolflag:

---

### Post by hariwonderful on 2011-07-14
[SIZE=3]I think its a little hard to adjust to. Kinda confuses between java, c and c++. [/SIZE]
[SIZE=3]I tried some stuff to get a hang of it but i keep getting errors like unexpected semicolon although i dont use it where its not supposed to be used.[/SIZE] 

[SIZE=3]But I think it's pretty promising for a system language[/SIZE].

---

### Post by JupiterV2 on 2011-07-14
The funny thing about the "old" responses to Go are...they're comparing a beta language to old, mature, existing languages. That's not necessarily unfair, if it brings nothing to the table that other more mature languages already offer, then why bother? However, the language has continued to develop and mature. I, personally, like it. Is it the end-all be-all? Heck no. Does it have tons of third-party library support. Not really but they're coming along. Does it have the wide-spread adoption that Google likely hoped for? Not, really no. The end result is that Go is designed for a specific task within Google and they just happened to release it to the public as a pet project. I'm not really sure what motivation they had in releasing it outside of the company. Either way, I'm enjoying it. It's been fun to learn and I'll continue to noodle with it.

The one major strength it has is that it is a compile to binary write once, compile and run anywhere language. It has no reliance on a virtual machine to run yet the standard libraries are OS agnostic. No POSIX vs. ANSI vs. whatever conflicts when trying to write portable C-like code.

Anyway, it's not perfect by any means. I desperately wish it had a range/xrange function more akin to Python's. I think they've added positional variables recently to print statements, I need to confirm that, but if it doesn't I'd love to see that too (another +1 for Python).

Comments of "Oh, its been done before" make me giggle. If its been done before, and the feature is a good one, doesn't it make sense to include it in other languages too? Go isn't especially novel. I like that the concurrency/inter-thread communication and the interface/type system they've implemented do NOT require external libraries. Yet, the ideas are nothing new. However, those are features which should be incorporated into a language, that don't require you hunt them down and install them on every computer you need to use them on (I'm looking at you C, C++, JVM, Python interpreter).

There's lots of arguments for Go and plenty of them against. Me? I just find it works for me and I hope it continues to grow and thrive. Will it become other C, C++, or Java? I doubt it very much but I think it will find its place.

With that said, "Code on!"

---

