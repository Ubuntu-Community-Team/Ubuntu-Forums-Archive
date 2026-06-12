---
title: "C++1x final comittee draft published"
date: 2010-04-15
forum: Programming Talk
---

### Post by MadCow108 on 2010-04-15
short while ago the draft for the new c++ standard has finally been published.
Now the features are complete and the rest of the work is improving this draft.

here's the preprint (whooping 1300 pages):
[http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3092.pdf](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3092.pdf)

The most important new features in my opinion are:
threading support
auto keyword
smart pointers
closures

but unfortunately it also makes the language even more complicated than it is today because of more stuff you just have to know (e.g. decltype (= better typeof), generalized initializers, the syntax of closures etc.)

---

### Post by Compyx on 2010-04-15
Didn't Bjarne Stroustrup say that he didn't expect anyone to understand all of C++? The complexity of C++ is what usually puts me off from picking C++ for a project. I worked my way through 'The C++ Programming Language, 3rd Edition', and in my opinion it's not a good book to learn C++ from. It's a good reference though.

Anyway, thanks for the link. That pdf is now keeping n1256.pdf company, the latest C99 standard draft. ;)

---

### Post by Sockerdrickan on 2010-04-15
Thank's for the heads up

> **Compyx said:**
> Anyway, thanks for the link. That pdf is now keeping n1256.pdf company, the latest C99 standard draft. ;)
you mean C1X?

---

### Post by Compyx on 2010-04-15
No, I meant C99 TC3, the current standard with corrections. I don't have the actual C99 standard, since you need to purchase a copy of that from ISO. I don't know much about the next standard, C1X. If I recall correctly, there's hardly any fully C99 implementation available. GCC has come a long way, but still misses a few bits, last time I looked. I believe Dinkumware has a fully C99-compliant standard library, but since that's proprietary, it doesn't fit my purposes.

Maybe I should follow comp.std.c for a while to see where C1X is headed. But I personally don't even use C99, I stick to C89; code written for C89 is still a lot more portable, especially when considering machines like the Amiga ;)

---

### Post by CptPicard on 2010-04-15
Hmm. The closures are probably just "forward closures" -- that is, you can't actually return the lambda and have the references captured (this requires a garbage collector or some other memory management system).

But, that's great anyway, I hate having to define functors as much as I generally do in C++. At least in C there is the GNU extension of nested functions that behaves much the same -- it's pretty nice to be able to pass a function pointer down the stack that can actually write to the variables that are in the same scope :)

---

### Post by merkour1s on 2010-04-18
[QUOTE=Compyx;9125199]Didn't Bjarne Stroustrup say that he didn't expect anyone to understand all of C++? The complexity of C++ is what usually puts me off from picking C++ for a project. I worked my way through 'The C++ Programming Language, 3rd Edition', and in my opinion it's not a good book to learn C++ from. It's a good reference though./QUOTE]

Hello,

I'm new to the world of programming. Last Summer I started learning C++ through that book (independent study) and got bogged down after about 4 chapters. I subsequently traded in my aging OSX for Ubuntu and have started learning bash and scripting. I intend to revisit C/C++ in July. My goal is to learn enough so that I can become involved in real Ubuntu programming/debugging projects. Can you recommend some books that will take me down that path?

thanking you in advance,

alexandros

---

### Post by Cracauer on 2010-04-18
Oh my.

Does it come with the required brain extension to keep a second 1000+ page language swapped in? :)

---

### Post by asddf on 2010-04-18
I know C++ and honestly yeah it's very hard to learn at first, theres a very steep learning curve and a lot of information to cover.

I knew properly 7 or so scripting/programming languages before starting C++ and I still found it hard.

But...It's difficult for a reason it's very powerful and it's the low level stuff that makes it so fast where as the other 7 or so language couldn't touch C++ for power.

If your new to programming I would strongly advise against doing C++ as a first language, you need to learn a lot before you can do anything.

---

### Post by slooksterpsv on 2010-04-18
> **merkour1s said:**
> [QUOTE=Compyx;9125199]Didn't Bjarne Stroustrup say that he didn't expect anyone to understand all of C++? The complexity of C++ is what usually puts me off from picking C++ for a project. I worked my way through 'The C++ Programming Language, 3rd Edition', and in my opinion it's not a good book to learn C++ from. It's a good reference though./QUOTE]

Hello,

I'm new to the world of programming. Last Summer I started learning C++ through that book (independent study) and got bogged down after about 4 chapters. I subsequently traded in my aging OSX for Ubuntu and have started learning bash and scripting. I intend to revisit C/C++ in July. My goal is to learn enough so that I can become involved in real Ubuntu programming/debugging projects. Can you recommend some books that will take me down that path?

thanking you in advance,

alexandros

C++ for the absolute beginner - its actually a fun book and I read it all the way through... well almost, I did skip one chapter on templates, iterations, and that that the C++ language includes for strings. - Other than that it was fun cause you made a simple text game at the end of each chapter, except the final one you made a DirectX game.

Overall, I love C#, VB.NET, and that. C# - easier memory management, same with VB.NET. - C++ I'll play around with once in a while if I'm really bored.

---

### Post by CptPicard on 2010-04-18
> **asddf said:**
> 
But...It's difficult for a reason it's very powerful and it's the low level stuff that makes it so fast where as the other 7 or so language couldn't touch C++ for power.

Well, this "power" issue is something we've had a lot of talk here over the years. I suppose it's worth bringing up the [megathread]("http://ubuntuforums.org/showthread.php?t=851794") for you new guys. If one equates low-levelness with "power", then one could probably say that C, which is far simpler than C++, is certainly "more powerful".

Language "power" really is a very vague concept. Something may be faster, and some languages may be designed in ways that allow for expression that is more interesting/richer than the low level stuff... 

> 
If your new to programming I would strongly advise against doing C++ as a first language, you need to learn a lot before you can do anything.

This is true... the issue is that a lot of the stuff in C++ is not immediately relevant for someone who needs to actually learn how "solving problems via computation" generally works. There's a lot of gotchas that just slow you down with it.

---

### Post by soltanis on 2010-04-18
I generally equate "power" with clear expressiveness, and functional languages usually win here. Executing individual C statements is fast, but then again, the net expressiveness of one line of C can usually be summed up in one sentence, while a line of LISP can be quite profound (granted, lisp lines do get lengthy).

C++1x makes a bad language worse. The committee should consider removing old parts of the language so that they can clarify exactly where they're going with this language. C++ is just a mess of different constructs at this point.

---

### Post by phrostbyte on 2010-04-18
I like the auto keyword. :)

I wish they would add Properties. Is this part of the new C++?

---

