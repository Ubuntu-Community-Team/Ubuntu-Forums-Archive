---
title: "Why is C++ rarely used in open source?"
date: 2009-08-07
forum: Programming Talk
---

### Post by cmwslw on 2009-08-07
I don't know it this is just me misunderstanding, but it seems like C++ is rarely used in open source. Are there any reasons for this? C++ just seems like a much more elegant language than C.

---

### Post by kknd on 2009-08-07
C++ is widely used in open source (KDE, for example). Even GNOME has some programs in C++, such as gnome-system-monitor

---

### Post by CptPicard on 2009-08-07
It's just you. ;) On the other hand, elegance seems to be in the eye of the beholder... I've always found C++ to be the hairiest language I've used :p

---

### Post by Simian Man on 2009-08-07
> **cmwslw said:**
> I don't know it this is just me misunderstanding, but it seems like C++ is rarely used in open source. Are there any reasons for this? C++ just seems like a much more elegant language than C.

C++ is a more practical language than C, but it is definitely *not* more elegant.  C++ is a hideous amalgam of a language.

---

### Post by nvteighen on 2009-08-07
I actually what happens is that the Linux kernel is in C and most of the GNU utilities also are because of the GNU project's history (gcc was one of the first things written, along with emacs), so there may be some kind of "inertia" playing in favor of C in the GNU/Linux world... 

IMO, C++ is a very complex beast to tame... an "amalgam language" like Simian Man said. Lots of semantic layers piled one over the other, mixed and interacting in a really messy way all along the whole code... unless you choose to use C-style C++ (but then, why are you using C++?), you'll always have high- and very-high-level constructs living and interacting with low-level ones, at the same time and with no clear boundaries...

Maybe there's also a technical decision behind this, but I'm not sure. Maybe, some programmers share my opinion (which is not just mine) and choose any language over C++, but I really don't believe this may set such a strong tendency. It's probably more related to what I say in the first paragraph... that sort of "pro-C inertia".

---

### Post by Viva on 2009-08-07
Both rms and Linus have spoken against OOP before. Linus ranted about C++ after somebody complained about writing GIT in C. IMO, the bundling of python in most distros greatly reduces the need for C++ at the application level.

---

### Post by Reiger on 2009-08-07
I think a big reason why C++ isn't *that* widely used in the GNU/Linux world is that apart from a let's-just-stick-to-C-and-be-happier-for-it approach there is also the fact that most distro's tend (if only for historical reasons) to bundle other runtimes/enviroments/platforms.

This means there is no need for a stand alone binary written in a language that tries to be it all and gives you that "write once run anywhere" idea in which the onus of your app actually working is largely on the runtime anyway. You "just" have to make sure your logic works. (Which is by all accounts hard enough in itself without worrying about not forgetting about things in your memory. :P)

---

### Post by Can+~ on 2009-08-07
> **cmwslw said:**
> Are there any reasons for this? C++ just seems like a much more elegant language than C.

"Elegant"? C is an elegant language because it provides a few minimal tools that can build up to pretty much anything. C++ is OOP that was stappled on top of C without thinking it too much (I hope C++0x is as good as it's being promised though).

Mainly because even if you have "Object Oriented"-ness you still need to think as memory and work with references and your own memory allocation. Memory leaks become frequent if you don't know what you're doing, breaking the whole point of having an "abstraction" (while the idea is to don't-care how things work and just use them from the outside).

---

### Post by CptPicard on 2009-08-07
> **nvteighen said:**
> you'll always have high- and very-high-level constructs living and interacting with low-level ones, at the same time and with no clear boundaries...


And yet you're still missing the really interesting high-level features such as closures and proper higher-order functions with functions as first-class objects... the high-levelness of C++ is not high level enough to justify the mess.

---

### Post by pepperphd on 2009-08-07
*reads topic* 

I couldn't imagine making any large scale game in spaghetti code.  C++ all the way. 

*crawls back into kdevelop c++*

---

### Post by steve-101 on 2009-08-07
Wow. Admittedly, if you can't write good systems level code, you should stick to Java or c# or whatever interpreter you choose to collect your garbage for you. You will surely shoot yourself in the foot.

I've been coding very large systems for both defense and the gaming (gambling) industry for 23 years, and have absolutely no problem writing "elegant" code in C++. I spent the first 15 of that in C / assemblers, and have since become a complete convert to C++. 

All the power of C native code, with all the neat constructs of any modern OOL.

---

### Post by Can+~ on 2009-08-07
> **CptPicard said:**
> And yet you're still missing the really interesting high-level features such as closures and proper higher-order functions with functions as first-class objects... the high-levelness of C++ is not high level enough to justify the mess.

*looks at avatar*... 'the hell?

---

### Post by CptPicard on 2009-08-07
> **steve-101 said:**
> Wow. Admittedly, if you can't write good systems level code

Nice, another newcomer comes in guns blazing with fighting words so we can start [the same discussion]("http://ubuntuforums.org/showthread.php?t=851794") over and over again. ;) Obviously we "can't" write good code if we have had exposure to thinking in other languages, and like it.


> 
you should stick to Java or c# or whatever interpreter you choose to collect your garbage for you.

Actually they are JIT-compiled. And GC is essentially just a manual, tedious resource-management problem just simply taken out of the way by the machine as it can certainly do it. In addition in languages that, say, have closures support, a garbage collector is essentially a necessity as it would not be particularly meaningful to have to keep track of the lifetime of your environment frames.

> 
I've been coding very large systems for both defense and the gaming (gambling) industry for 23 years, and have absolutely no problem writing "elegant" code in C++.

Elegance is very difficult and subjective matter to judge. Suffice it to say that the more I think about how and why different languages do things, the messier C++ seems no matter how competent one might become in actually using it.

> I spent the first 15 of that in C / assemblers, and have since become a complete convert to C++. 

Which means you are probably thinking quite inside the box. What is your exposure to, say, functional programming? Lisp? Haskell? Declarative programming? Prolog?

> 
All the power of C native code, with all the neat constructs of any modern OOL.

Static-typed OOP can be a bit of a cult in itself, and the way it's grafted onto C in C++ takes the whole thing quite far from the philosophy of languages like Smalltalk. Look at Objective-C for a more lightweight way of creating support for the typical way of creating OOP on top of what is essentially C.

> **Can+~ said:**
> *looks at avatar*... 'the hell?

[http://en.wikipedia.org/wiki/Nasse-set%C3%A4](http://en.wikipedia.org/wiki/Nasse-set%C3%A4)

---

### Post by Cyanidepoison on 2009-08-07
C++ is ugly and I don't like it.

Is that a good enough reason? :P

---

### Post by CptPicard on 2009-08-07
> **Cyanidepoison said:**
> C++ is ugly and I don't like it.

Is that a good enough reason? :P

Yes, it certainly is. Try some Lisp instead. ;)

C++ is certainly learnable after you're a competent programmer, and in some cases it's the (unfortunately) most suitable tool you have, for various different reasons. It doesn't mean one couldn't appreciate the fact that there is a huge deal of stuff to "just know" which is never a good thing in a language...

---

### Post by cmwslw on 2009-08-07
Don't mean to start up another debate, but I have trouble writing certain programs in plain C without the ability to define classes. I think situations like those are the times that C++ should be use. Vectors are always nice, too. But when writing a low level utility, like an ARM microcode debugger, I agree that C is the best choice because C pretty much forces you to really understand how computers work. When I first started programming, I used C++, but now I'm trying to learn how to accomplish the same tasks with good ol' C. I'm finding [this]("http://people.cs.uchicago.edu/~iancooke/osstuff/ccc.html") guide to be very useful.

-Cory

---

### Post by uljanow on 2009-08-07
Because people stick to what they're used to.
E.g. if you want to use object oriented programming just write a C library named gobject.

g_init((myClass *)foo, ...);
g_set_property((myClass *)foo, ...);
g_destroy((myClass *)foo);

That's way more elegent than C++.

---

### Post by TheBuzzSaw on 2009-08-07
C++ is a fabulous language. Low level code is the way to go. ^_^

I am building a fighter engine in C++ at this very moment.

---

### Post by karlmp on 2009-08-07
[http://catb.org/esr/jargon/html/C/C-plus-plus.html](http://catb.org/esr/jargon/html/C/C-plus-plus.html)

---

### Post by soltanis on 2009-08-07
> **uljanow said:**
> 
g_init((myClass *)foo, ...);
g_set_property((myClass *)foo, ...);
g_destroy((myClass *)foo);

That's way more elegent than C++.

I was going to ask "what the hell do you think is elegant?" but then I read the "than C++" part.

Seriously CptPicard, what is with the avatar?

---

### Post by CptPicard on 2009-08-07
> **soltanis said:**
> 
Seriously CptPicard, what is with the avatar?

[http://en.wikipedia.org/wiki/Nasse-set%C3%A4](http://en.wikipedia.org/wiki/Nasse-set%C3%A4)

---

### Post by Can+~ on 2009-08-08
> **CptPicard said:**
> [http://en.wikipedia.org/wiki/Nasse-set%C3%A4](http://en.wikipedia.org/wiki/Nasse-set%C3%A4)

I guess the question should be: Why?

I mean, avatars are usually: "oh this is so cool I want it as my avatar". I wonder how did you get to that image and/or why you chose it. It's kinda creepy to me.

[COLOR="Silver"][I]"Why, why, can we never be sure till we die
Or have killed for an answer"[/I] (Genesis, Time Table)[/COLOR]

---

### Post by CptPicard on 2009-08-08
> **Can+~ said:**
> 
I mean, avatars are usually: "oh this is so cool I want it as my avatar".

I have done this, and it has worked. It is remarkable as to how people have read whatever I have written here to have been spoken by Jean-Luc Picard...

> 
 I wonder how did you get to that image and/or why you chose it.

He is apparently a drunk clown who hates children, and who, through gritted teeth, still pulls through a childrens' tv show...

---

### Post by Mirge on 2009-08-08
> **Can+~ said:**
> I guess the question should be: Why?

I mean, avatars are usually: "oh this is so cool I want it as my avatar". I wonder how did you get to that image and/or why you chose it. **It's kinda creepy to me**.

[COLOR=Silver][I]"Why, why, can we never be sure till we die
Or have killed for an answer"[/I] (Genesis, Time Table)[/COLOR]

CptPicard is still awesome, but that clown is *damn* creepy...:KS

---

### Post by abhilashm86 on 2009-08-08
nope, i'm working on a GUI c++ project, both backend and front end using Qt, its a alternative software to simulink.........

---

### Post by nvteighen on 2009-08-08
> **cmwslw said:**
> Don't mean to start up another debate, but I have trouble writing certain programs in plain C without the ability to define classes. I think situations like those are the times that C++ should be use. Vectors are always nice, too. But when writing a low level utility, like an ARM microcode debugger, I agree that C is the best choice because C pretty much forces you to really understand how computers work. When I first started programming, I used C++, but now I'm trying to learn how to accomplish the same tasks with good ol' C. I'm finding [this]("http://people.cs.uchicago.edu/~iancooke/osstuff/ccc.html") guide to be very useful.

-Cory

An alternative is Objective-C. It nicely adds OOP features and just OOP features to C, addressing only one issue (and not trying to address everything, like C++). The issues it has is that in order to have a decent program you need the OpenStep libraries (which almost act as Objective-C's Standard Library) and those are a bit complex, and that the Objective-C runtime speed is a bit slower than it should... at least on GNU ObjC Runtime based systems... no idea what happens on Mac OS X (which is almost entirely written in ObjC).

> **CptPicard said:**
> I have done this, and it has worked. It is remarkable as to how people have read whatever I have written here to have been spoken by Jean-Luc Picard...

I don't care what you mean with this, but I command you to bring Captain Jean-Luc Picard back to our starship. (*Phasers ready, Commander Riker*)

---

### Post by Sockerdrickan on 2009-08-08
> **uljanow said:**
> g_init((myClass *)foo, ...);
g_set_property((myClass *)foo, ...);
g_destroy((myClass *)foo);

That's way more elegent than C++.
[SIZE=1][COLOR=Silver]is he being ironic[/COLOR][/SIZE][COLOR=Silver]?[/COLOR]

---

### Post by garikaib on 2009-08-08
It is just the way it is. History has a way of shaping the future and this in no exception.

---

