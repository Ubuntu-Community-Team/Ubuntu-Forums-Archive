---
title: "[C++] I like my &quot;main&quot; void..."
date: 2008-07-05
forum: Programming Talk
---

### Post by kavon89 on 2008-07-05
but the compiler says "main.cpp:3: error: ‘::main’ must return ‘int’"

While I was playing with methods/functions, my Java senses drew attention to the fact that main is specified to return an int, zero, all over my book. Can I have main return void (nothing) so I avoid useless return 0 statements?

---

### Post by myrtle1908 on 2008-07-05
[http://www.research.att.com/~bs/bs_faq2.html#void-main](http://www.research.att.com/~bs/bs_faq2.html#void-main)

---

### Post by CptPicard on 2008-07-05
Well, it is the process return code that is pretty much expected on Unix/Linux, so you might just as well get used to it. :)

And.. hmm.. I may be wrong because it's been so long since I wrote anything in C or C++, but does the compiler enforce the return statement in main or will it silently add a return 0 if you don't include one? (Not that it would be such great programming, you really should get into the habit of passing an explicit return code)...

---

### Post by kavon89 on 2008-07-05
> **CptPicard said:**
> does the compiler enforce the return statement in main or will it silently add a return 0 if you don't include one?

I just tried it and it's fine without it, the article says it assumes 0 I think. I'll keep writing return 0 for main because I don't want to be "considered ignorant by C and C++ programmers" by skipping it. :D

Thanks for the link myrtle.

---

### Post by lisati on 2008-07-05
It might not matter so much in smaller projects that you'll be using yourself, but having your main() return something is a good way of passing on a note of its success (or otherwise) to calling programs, thus providing the means of an intelligent response by the calling process.

---

