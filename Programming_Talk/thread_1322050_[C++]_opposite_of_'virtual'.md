---
title: "[C++] opposite of 'virtual'"
date: 2009-11-10
forum: Programming Talk
---

### Post by TheBuzzSaw on 2009-11-10
I use **virtual** when I want to indicate that a particular member function is to be defined in derived classes. Is there a way I can do the opposite? Is there a way I can make a function immune to override/redefinition/etc.? Can I make it throw a compiler error if another class attempts to do that?

---

### Post by CptPicard on 2009-11-10
[http://www.parashift.com/c++-faq-lite/strange-inheritance.html#faq-23.12](http://www.parashift.com/c++-faq-lite/strange-inheritance.html#faq-23.12)

There is no "final" in C++... but, a non-virtual method is about as good.

---

### Post by dwhitney67 on 2009-11-10
There is no such thing.  I'm not sure if you are familiar with Java's "final" statement, but here's a thread of some bloke looking to implement it in C++.

[http://bytes.com/topic/c/answers/60997-how-do-i-implement-final-c](http://bytes.com/topic/c/answers/60997-how-do-i-implement-final-c)

---

### Post by TheBuzzSaw on 2009-11-10
That's what I figured. I am aware of Java's **final** keyword. I was hoping C++ would have a similar mechanic I may have missed.

Thanx.

---

### Post by MadCow108 on 2009-11-10
as said you can't lock a method from being overriden but you can forbid that class derives from another:
[http://www2.research.att.com/~bs/bs_faq2.html#no-derivation](http://www2.research.att.com/~bs/bs_faq2.html#no-derivation)

---

### Post by Fatman_UK on 2009-11-11
Even if/when the "final" keyword gets into C++, it would only be a suggestion to other programmers. There are a dozen theoretical ways to overcome restrictions like that, including obtaining a copy of your source code and compiling it with "final" deleted!

IMO the most effective way currently is this:

```

// NOTE: Warning! Do *not* override or redefine this function!
// You will be fired if you do. No exceptions!

```

---

### Post by TheBuzzSaw on 2009-11-11
Heh... well, yeah, with access to the source code, *anything* is possible (including nuking the entire thing and starting from scratch). I just figured it would be nicer for anyone attempting to override to get a compiler error that makes it abundantly clear that it should not be redefined. I'm not looking to physically restrain people. :P

---

