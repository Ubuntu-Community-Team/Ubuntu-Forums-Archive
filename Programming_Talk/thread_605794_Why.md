---
title: "Why???"
date: 2007-11-07
forum: Programming Talk
---

### Post by rekahsoft on 2007-11-07
Hi all..i am quite torn between Desktop Environments Gnome and KDE....I am planning on developing for one of the two..i don't like how gnome is written all in C with glib..i have looked at the code and it seems to be really ugly..why would they use C? is there really that much of a speed improvement?...what is the advantages/disadvantages of working with either project?

---

### Post by ankursethi on 2007-11-07
KDE uses C++ with Qt and, since you don't seem to like C, it might suit you better. Yet, GNOME is more friendly to commercial software than KDE. Take your pick.

I have no idea why the GNOME team chose C, but I suspect that they used it because both the Linux kernel and most of the GNU tools were in C (how this is to everyone's advantage, I don't know). But these days, many (smaller) GNOME apps are either in a scripting language (Python, Ruby) or (shudder) C# with Mono.

---

### Post by LaRoza on 2007-11-07
> **ankursethi said:**
> 
I have no idea why the GNOME team chose C, but I suspect that they used it because both the Linux kernel and most of the GNU tools were in C (how this is to everyone's advantage, I don't know). 

C is more portable, C is more powerful, and C is used everywhere in *nix programming.

In Python, which was also originally written in C, many modules are in C. Also, you can use GTK, QT, and wxWidgets in Python. Python is a good choice for development. Any thing that requires more speed can be written as a module.

---

### Post by rekahsoft on 2007-11-07
I just find that there is not much reason to use C now a days...it is definitly a neat language just i do not like how doing somethings (an object oriented system for example) is ugly and takes a long time just to do something simple...the one thing i do like about C is that you have a LOT of control... i really like both projects so i am defintly having some trouble with this decision...i definitly would preffer to code in C++, python, java, or C#...also ...is there a good reason to get lots of C experiance?

---

### Post by LaRoza on 2007-11-07
> **rekahsoft said:**
> ...is there a good reason to get lots of C experiance?

Yes. If you use Python, you can easily write modules in C to improve efficiency. Also, understanding how things work in higher level languages will enable you to use them efficiently. After learning C, learn Assembly.

C is also used in most GNU software, and if you want to join a project, or start one, C is good to know. C is the "universal" language. The first thing a new computer needs is a C compiler.

---

### Post by ankursethi on 2007-11-07
Actually, C + Python is a killer combination. With C, you get performance, speed and control. With Python you get all the OO goodness, ease of use and gazillions of modules.

You can use anything you want. Really, both Qt+KDELibs and GTK+ are equally good.

---

### Post by LaRoza on 2007-11-07
> **ankursethi said:**
> 
You can use anything you want. Really, both Qt+KDELibs and GTK+ are equally good.

wxPython is good also.

---

### Post by rekahsoft on 2007-11-07
Hmm..ok...so i will learn more C...i only know little at the moment :S...but that does still not solve my problem of which project i should focus on....

---

### Post by LaRoza on 2007-11-07
> **rekahsoft said:**
> Hmm..ok...so i will learn more C...i only know little at the moment :S...but that does still not solve my problem of which project i should focus on....

Do both. You can use GTK, wxWidgets, QT on both. I would go for wxWidgets, but you could try them all to see what you like better.

---

### Post by rekahsoft on 2007-11-07
but i would want to learn the libraries of the DE...and the libraries tend not work as well in other DE's

---

### Post by AlexThomson_NZ on 2007-11-07
When you say you want to develop for Gnome or KDE, do you mean ON or FOR?

You can develop C++ apps on Gnome using gtkmm.

---

### Post by rekahsoft on 2007-11-07
When i say i want to develop for gnome or kde i mean collobrate with the project to produce release and better and bett software...so work ON the project..and i know i can develop C++ apps for gnome using gtkmm..i have actualy went through quite a bit of the tutorial...i am just torn between the desktops..although...i am leaning towards KDE...

---

### Post by ssam on 2007-11-07
[http://www.gtkmm.org/](http://www.gtkmm.org/) lets you use C++ and GTK

it is used by some big projects like inkscape, gparted and glom
[http://www.gtkmm.org/extra.shtml](http://www.gtkmm.org/extra.shtml)

---

### Post by Quikee on 2007-11-07
[Vala]("http://live.gnome.org/Vala") is also gaining popularity lately. It is a programming language similar to C# and uses Glib and C the same way Java/C# uses byte code - as the intermediate layer. The advantage is that it is slightly faster (in some benchmarks i have seen - however slower than plain C) and more lightweight than C#/Java/Python because you don't have a virtual machine + you don't need special vala libraries for running applications - only the C libraries. ;)

---

### Post by bruce89 on 2007-11-07
> **Quikee said:**
> [Vala]("http://live.gnome.org/Vala") is also gaining popularity lately. It is a programming language similar to C# and uses Glib and C the same way Java/C# uses byte code - as the intermediate layer. The advantage is that it is slightly faster (in some benchmarks i have seen - however slower than plain C) and more lightweight than C#/Java/Python because you don't have a virtual machine + you don't need special vala libraries for running applications - only the C libraries. ;)

It is plain C, how can it be slower?

Vala translates vala programs into C, then it compiles it with GCC.

> **rekahsoft said:**
> When i say i want to develop for gnome or kde i mean collobrate with the project to produce release and better and bett software...so work ON the project..and i know i can develop C++ apps for gnome using gtkmm..i have actualy went through quite a bit of the tutorial...i am just torn between the desktops..although...i am leaning towards KDE...

GNOME is a pretty difficult thing to get into, also you have to be pretty good at C to even think about it.

---

### Post by Quikee on 2007-11-07
> **bruce89 said:**
> It is plain C, how can it be slower?

Vala translates vala programs into C, then it compiles it with GCC.


Because of the translation overhead. 

See [here]("http://code.google.com/p/vala-benchmarks/wiki/BenchResults"). The difference is very small.. but it exists.

---

### Post by j_g on 2007-11-07
Remember that the whole purpose of GTK is to be used by other programs. It's not an application in of itself. Therefore, most of the GTK code consists of shared libraries designed to be used by apps written in a variety of languages. (So too, the Linux operating system is largely the same, although some parts consist of drivers instead of libs -- but the same principle applies that they're meant to be called by apps written in a variety of languages).

There is a reason why people choose C, rather than C++, for making shared libraries (and drivers). The reason is because C involves less requirements for argument passing. All args in C are passed on the stack explicitly (unless otherwise noted -- and it's definitely a no-no to use other argument passing schemes in a shared lib -- such as passing args in registers). This is easy for most any language's compiler/interpreter to handle (since it wouldn't be a very useful language if it didn't know how to push/pop things on the stack).

On the other hand, C++ functions expect the object (whose function is being called) to be the first arg passed to the function. It is said to be "hidden" because, although it must be the first arg, in the declaration of the function, that arg isn't explicitly listed. The C++ compiler throws that hidden arg into the mix when the function is called. (Sure, you could use static functions in C++, but then, if you use any object, you've got to have a pointer to it stored somewhere in the shared lib, and that means using local, global mem. That introduces its own problems, such as making threadsafe code a pain in the ***, or making it impossible for two different threads to operate upon the same "object"). And there isn't really a standard for passing this hidden arg. For example, Microsoft's Visual C++ passes this hidden arg in the EDX register.

So, say you want to write an interpreter for some new language. You decide to code your interpreter in C++. Ok, you're all set to go with either QT or Gnome. But instead, you decide to write your interpreter in C, or delphi, or basic, or anything but C++. Now you've got a problem with QT, because it expects your calls to all QT functions to include this hidden arg. Are you supposed to pass it in the EDX register? Now you've got to write your interpreter so that it knows to store any QT object, and when calling a function associated with that object, the object must be passed in EDX. There's more coding you have to do in your interpreter (and you may have to resort to asm code, as your language of choice may not have any "instructions" that implement C++ arg passing). With a C shared lib, it's less of a hassle to implement arg passing, regardless of what language you're using. Most any language can take a C function definition and push args on the stack (with some minimum arg translation perhaps). For example, Visual Basic has a LIBRARY statement to do this. On the other hand, there is no equivalent LIBRARY statement to call a C++ object's function. Why? Because it's a lot more hassle and bookkeeping involved.

Frankly, I think that TrollTech's decision to code QT in C++ was a bad choice. C++ is not a good language if you're making something that you want to interface to a great many other languages. It's suitable only if you want to interface with other C++ code.

---

### Post by Wybiral on 2007-11-07
> **j_g said:**
> Frankly, I think that TrollTech's decision to code QT in C++ was a bad choice. C++ is not a good language if you're making something that you want to interface to a great many other languages. It's suitable only if you want to interface with other C++ code.

I agree. It makes more sense to code the library in C, then write a C++ wrapper for it. It's always easier to write a C++ wrapper for a C library than to write a C wrapper for a C++ library.

---

### Post by Mark Grice on 2007-11-07
> **rekahsoft said:**
> Hmm..ok...so i will learn more C...i only know little at the moment :S...but that does still not solve my problem of which project i should focus on....

I guess what confuses me is how you know C++ but only know "a little C".

The concept of classes is new in C++ but syntactically, the two are very similar.

As for me, I much prefer C over C++,.. always have...

---

### Post by Wybiral on 2007-11-07
> **Mark Grice said:**
> I guess what confuses me is how you know C++ but only know "a little C".

The concept of classes is new in C++ but syntactically, the two are very similar.

As for me, I much prefer C over C++,.. always have...

Syntax means nothing, there is a world of difference between C and C++ programming (much more than just classes). Aside from the major changes in design strategies you use in each, there's differences in templates/references/type casts/etc... Not to mention the STL (which should radically alter your program designs).

---

### Post by Mark Grice on 2007-11-08
> **Wybiral said:**
> Syntax means nothing, there is a world of difference between C and C++ programming (much more than just classes). Aside from the major changes in design strategies you use in each, there's differences in templates/references/type casts/etc... Not to mention the STL (which should radically alter your program designs).

Well, I'm not going to argue with you...

First of all, syntax is everything :-) Otherwise all languages would be the same...

I still think, though, that a C++ programmer moving to C should have a pretty easy time... The other way around might not be as true...

---

### Post by Wybiral on 2007-11-08
> **Mark Grice said:**
> Well, I'm not going to argue with you...

First of all, syntax is everything :-) Otherwise all languages would be the same...

I still think, though, that a C++ programmer moving to C should have a pretty easy time... The other way around might not be as true...

I'm not trying to argue with you either, I'm just saying that they aren't as similar as people often think. Not if you use them right, that is. A good C++ programmer should rely heavily on RAII, the STL, auto pointers, templates, and all the other goodies that C++ brings.

So a good C++ programmer might have trouble adjusting to the radical difference that plain C imposes where you write code that requires your users to explicitly call things like "free_myObject" and any generic approach is likely going to require the use of macros (which a good C++ programmer will probably never use). C also requires a more extensive understanding of pointer magic, learning how to dereference and handle "multiple star" pointers (which should never come up in C++).

Syntax is not everything. Syntax is only the cosmetic makeup of a language. Semantics, standard libraries, and common design patterns are much more important to a programming language than how it's typed. Once again, I'm not trying to argue here, it's just that I often see statements like "I'm learning C/C++ ... " and that doesn't make sense to me because they really are so different. But for some reason people seem to group them by their cosmetic appearance rather than their real world use (which is incredibly different).

---

### Post by pmasiar on 2007-11-08
> **Mark Grice said:**
> First of all, syntax is everything :-) Otherwise all languages would be the same...

Syntax is a skin deep. Your comment just suggest you did not learned yet couple languages using different paradigm from C or C++. Try to spend a week each on very different languages like Lisp, Forth, XSLT, Prolog, SQL, and simple dynamically typed like Python/Perl/Ruby. You will see that differences go way beyond syntax: **semantics** is different. Task which is trivial in Prolog may take you weeks in C, and vice versa.

And before CptPicard will chime in: not all, but most languages **are** the same underneath the syntax skin, from POV of computability: most are [http://en.wikipedia.org/wiki/Turing_complete](http://en.wikipedia.org/wiki/Turing_complete) . Just warning: computability is a theoretical science, they do not care about solving real-life problems in practice. People who do, distinguis languages not by syntax, but by fitness to solve certain class of tasks.

---

### Post by Mark Grice on 2007-11-08
> **Wybiral said:**
> 

Syntax is not everything. Syntax is only the cosmetic makeup of a language. Semantics, standard libraries, and common design patterns are much more important to a programming language than how it's typed. Once again, I'm not trying to argue here, it's just that I often see statements like "I'm learning C/C++ ... " and that doesn't make sense to me because they really are so different. But for some reason people seem to group them by their cosmetic appearance rather than their real world use (which is incredibly different).

Possibly. 

However, the creator of the C++ language, Bjarne Stroustrup, called it: 

 **“a C language with classes and … Simula67’s stronger sense of data types.” **

Maybe that's where the "confusion" started? ;)

And... pmasiar, you make some pretty big assumptions:

> Syntax is a skin deep. Your comment just suggest you did not learned yet couple languages using different paradigm from C or C++. Try to spend a week each on very different languages like Lisp, Forth, XSLT, Prolog, 

I worked for Inference Corp for 3 years... I did my time in LISP (Language of insipidly stupid parenthesis as we called it) and then did JAVA programming as well. Never got into FORTH. And I'm not sure if SQL really counts, since it is wholly data centric.

Point is: I stand by my assertion:

Syntax matters. It is not merely cosmetic.

But... I'm done now. I didn't mean to hijack the thread...

---

### Post by rekahsoft on 2007-11-08
> **Mark Grice said:**
> I guess what confuses me is how you know C++ but only know "a little C".

The concept of classes is new in C++ but syntactically, the two are very similar.

As for me, I much prefer C over C++,.. always have...

i don;t know all the libraries and have never used a proceedure language before...so new design principles..also i have never done such low level programming

---

### Post by CptPicard on 2007-11-08
> **rekahsoft said:**
> i don;t know all the libraries and have never used a proceedure language before...so new design principles..also i have never done such low level programming

If I were you I wouldn't worry. In my view C is very, very much a subset of C++, and you'll pick up ways to do in C for the stuff you would have needed C++ for. The basic structures are essentially identical, and C is, after all, a much, much *smaller* language than C++.

Then again, I'd recommend KDE and Qt :) You already know C++, and those have really clean APIs. A lot of neat stuff there already, and the design is quite clean.

---

### Post by LaRoza on 2007-11-09
> **CptPicard said:**
> The basic structures are essentially identical

Structures are very different in C and C++. 

@OP learning C is not difficult, but may require you to think about things you may have glossed over in C++.

---

### Post by Wybiral on 2007-11-09
> **CptPicard said:**
> ... C is, after all, a much, much *smaller* language than C++ ...

Yes, but assembly is much smaller than C...

And BrainF*ck is even smaller than assembly...

Heck, you can write in binary if you want, and syntactically binary only has two symbols!

But I think assembly is harder than C, and BrainF*ck is harder than assembly. Syntactically, they are simpler, however developing in them is much more of a challenge because they require a MUCH different approach and background. Which must be learned.

But the simple constructs of the language aren't the entire picture. More importantly is the design patterns that the language implies. Programming in C requires a completely different approach than programming in C++, and you have to learn to think in a completely new way.

---

### Post by Mark Grice on 2007-11-09
> **Wybiral said:**
> Yes, but assembly is much smaller than C...

And BrainF*ck is even smaller than assembly...

Heck, you can write in binary if you want, and syntactically binary only has two symbols!

But I think assembly is harder than C, and BrainF*ck is harder than assembly. Syntactically, they are simpler, however developing in them is much more of a challenge because they require a MUCH different approach and background. Which must be learned.

But the simple constructs of the language aren't the entire picture. More importantly is the design patterns that the language implies. Programming in C requires a completely different approach than programming in C++, and you have to learn to think in a completely new way.

Well, I was going to stay out of this... but OMG, Wybiral, do you think your post was a little over the top? BrainF*ck?

CptPicard's point was that C is a subset of C++. If you know C++, learning C is not as hard as -- say -- going from C++ to FORTH. No one is saying that C and C++ are the same thing... just that a talented C++ programmer should be able to learn C without too much strain...

No one is trying to criticize C++ (or rekahsoft for that matter)...

---

### Post by CptPicard on 2007-11-09
Honestly I do not get this supposed HUGE difference between C and C++ :) 

Assembly and brainf*ck are irrelevant because they're completely different languages. C is enough of a subset of C++, and a small subset at that, that a C++ programmer can reduce his programming to that set. And yes, all the basic building blocks in C are present in C++ as is... (yes you can catch me on trivia here but I don't care really... it's the big picture)

Yes, stripping away OOP makes you structure your stuff differently and losing C++ stdlib is a loss... it's probably because I went from C to C++ that it is just "obvious" to me which bits in C++ are C, but I still believe that for a C++ programmer, reading K&R and familiarizing oneself with some well-built C code should be enough.

---

### Post by Vadi on 2007-11-09
@OP : I think you should see what projects are you interested in contributing to, and then see if they're based on Gnome or KDE.

---

### Post by Wybiral on 2007-11-09
> **CptPicard said:**
> ... Assembly and brainf*ck are irrelevant ...

I only mentioned them because it sounded like you were implying that smaller (syntactically) languages are easier to learn, which isn't the case.

---

### Post by RetiredInMaine on 2007-11-09
If you know C++ you already know c. c ++ is an extension. The major difference is that the c i/o is different than the c++ i/o, and you use different lib headers. In fact most one semester c++ courses actually teach the c subset with maybe one lecture on classes, which are really an extension of the c struct. 

c++ was deliberately designed to be backward compatible which is why for oo programming I prefer a language like java. One mans opinion of course. Lots of programmers I know disagree with me. However if you prefer oo programming take a look at open office programming. I read that it's written in java. :guitar:

---

### Post by pmasiar on 2007-11-09
Syntactically smallest language is probably [whitespace](http://en.wikipedia.org/wiki/Whitespace_%28programming_language%29) - just 3 tokens :-)

---

