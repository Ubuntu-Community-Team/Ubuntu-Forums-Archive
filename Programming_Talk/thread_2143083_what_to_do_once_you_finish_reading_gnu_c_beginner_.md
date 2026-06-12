---
title: "what to do once you finish reading gnu c beginner book"
date: 2013-05-07
forum: Programming Talk
---

### Post by rawrmonster on 2013-05-07
I am just about to finish my learning gnu c book but it only teaches the basics. My question was where do i go now? To be honest most of the things i wanted to program have to do with interfacing other programs and that is how i would want to proceed, if i am even close to this step. Sorry if this is a dumb question, and thank you for reading in advance. Feel free to ask me anything needed to help make a more correct answer.

---

### Post by trent.josephsen on 2013-05-07
I'd never heard of that book before. Having looked into it, I'd suggest you forget all that nonsense and find a book that teaches C, not "GNU C". The flippant way in which the author dismisses the standardization of C and freely mixes extensions with standard features reminds me of how other books toss about crap like void main() and system("pause"). It is rife with subtle and not-so-subtle errors, bad advice, and truly baffling gems like this one:
[quote=Learning GNU C]9.6. the restrict type qualifier

This is something to do with pointers, I think it tells the compiler that a specific pointer is the only pointer to a section of memory, the compiler can optimise code better with this knowledge. I think.[/quote]

Great. Looks like this author has about the same level of experience with C as Herb Schildt. (Or did, in 2002; based on the 8th grade writing level, perhaps I'll forgive the youthful indiscretion.) Frankly I'm surprised and saddened by the total lack of experience or intelligence applied to creating this tutorial. But I digress...

Your question is not dumb at all. It's a common one, actually, but the answer depends on what your current level of knowledge is and where you want to go.

Is C your first language? If so, perhaps someone else can suggest a good resource for you. I learned from K&R2, and I continue to strongly recommend it, but it's really aimed at programmers wanting to learn C and not people wanting to learn to program with C. There are good online resources, but you have to know what you're looking for and pick a book that's defended by expertise.

What exactly do you mean by "interfacing other programs"? In general, that's something C is not often used for anymore. Shell and Perl would be languages you're more likely to see in the "glue" category. Unless you're thinking of interfacing with a specific program or library that exposes a C API; that's a different story.

---

### Post by diesch on 2013-05-07
Have a look at some real world code. Try to understand it. Play with it. Modify it. Fix some bugs. Add some features.

One of the great things about FLOSS software is that all the source code is available for you. Learn from it. Hack it. Improve it. Make the world a better place.

---

### Post by rawrmonster on 2013-05-08
c is my first language that i have seemed to follow all the way through. I really like that it is a small language so it is easy to learn as a beginner but takes a long time to master. I really want to stick with c just for the reason that most code in linux seems to be in c or some language like python or ruby. Not trying to be hard headed but dont understand why would i not try to learn gnu c, when that is the compiler i will be using?

---

### Post by rawrmonster on 2013-05-08
How about Teach yourself c in 21 days book? it seems pretty in depth.

---

### Post by trent.josephsen on 2013-05-08
> **rawrmonster said:**
> c is my first language that i have seemed to follow all the way through. I really like that it is a small language so it is easy to learn as a beginner but takes a long time to master. I really want to stick with c just for the reason that most code in linux seems to be in c or some language like python or ruby.

C may be a common language of sorts, and one I personally favor, but that doesn't make it particularly good at anything you want to do. C is great for kernels, drivers, and some systems software, but it's not all that well suited for interfacing with other programs, which is why I asked. But I won't tell you your business.

One language that is small, like C, but has a shallower learning curve and is better suited as a glue language is Lua. It has a somewhat sparse aesthetic, which I like, and has been able to displace C in some applications demanding small footprint and short development cycles, as well as being popular as a scripting language for larger programs such as games. If you like C for its size, but don't yet know any other languages, you might look into Lua. I mention this just because I think you might be interested; I'm not saying you should abandon any attempt to learn C.

> Not trying to be hard headed but dont understand why would i not try to learn gnu c, when that is the compiler i will be using?

For starters, compilers don't last forever and you may find several good reasons to switch in the near future. Planning on doing professional development? Better be prepared to use whatever compiler they give you, and possibly switch at the drop of a hat when the requirements change. A hobbyist? You'll find better support in forums like this one if you're using the language everyone knows and not some vendor extension. Furthermore, you can often get more and higher quality warnings from your compiler if you ask it to conform to a particular standard revision. It's also worth noting that while ANSI C can be clearly specified in under a hundred pages, GNU C89 is a different beast entirely.

The choice is ultimately up to you, but even so, I'd steer clear of Learning GNU C, if for no other reason than that it was poorly written and obviously never proofread.

---

### Post by souravc83 on 2013-05-09
I would suggest C++. Its a natural extension of C. You can pick it up easily, and it is THE still the language in a lot of areas.
This is a great go-to resource to start you off.
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

You'll find the first few chapters are very similar to C, and then it goes to OOP, which will be immensely useful.

---

### Post by trent.josephsen on 2013-05-09
Let's not turn this into another "my favorite language" thread. I realize I started it by mentioning Lua, but I just thought OP might be interested based on OP's earlier post. If what rawrmonster likes about C is its size, he or she is probably not interested in C++.

[Here is a book review of Teach Yourself C in 21 days (5th edition)](http://accu.org/index.php?module=bookreviews&func=search&rid=1188). ACCU's book reviews are what I usually turn to when I don't have experience with a book myself. I'd avoid it.

---

