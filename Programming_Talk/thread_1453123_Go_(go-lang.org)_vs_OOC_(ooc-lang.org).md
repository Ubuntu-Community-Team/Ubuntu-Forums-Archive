---
title: "Go (go-lang.org) vs OOC (ooc-lang.org)"
date: 2010-04-12
forum: Programming Talk
---

### Post by patrickaupperle on 2010-04-12
What do you all think about Go (the one from google) and OOC? They remind me, for some reason, of each other. Probably because they are both fairly new and compile to machine code. OOC compiles to C then machine code, while, if I am right, Go compiles directly.

Anyway, what is the general opinion? Are either of these two going to become major players? Have any of you tried them? Will any of you try them? 

Personally, I like ooc better than go, but see a better future for go because it is backed by google.

---

### Post by soltanis on 2010-04-13
What is OOC? I've heard of Go; surprisingly the people at Suckless have adopted it.

I actually recognize the canonical successors to C in Go -- Plan 9's Alef programming language, which was never widely popularized, and Limbo, an offspring of that language used in Inferno, a 9p-like OS.

It's too bad that neither never really got popular. Plan 9 is an amazing system, and Alef is a great programming language. There are a few things about Go I don't like, such as the whole deal with semicolons (the compiler restricts you to a certain coding style because it isn't smart enough to insert semicolons in the right places -- personally, I wish it just let you put them in yourself). The concurrent programming is nice though.

---

### Post by nvteighen on 2010-04-13
The issue is we already have languages that fill in to these two's niches.

Go is too similar to Python; ok, it may be faster, but it's too high-level for a speed-critical environment. It's not bringing anything new either, except for the built-in concurrence support (which isn't a new concept either... it's just that you don't need a library for it).

OOC seems a duplication of Objective-C, which is used quite a lot on the Apple-world. The issue is that Objective-C supports generic programming via the "id" data type, selectors and a Smalltalk-like way of things... OOC seems to stick to the static-typed paradigm, like C++'s.

These two languages, in its current fashion, don't seem to be mature enough not to have any distinctive feature that makes me think they could be of any importance. Quite frankly, the most innovative ideas nowadays are on the functional programming side, Clojure (Lisp-on-Java) being possibly the project that's drawing the most attention of all.

Of course, Go seems to have much more future than OOC, considering who's behind that language... :p

---

### Post by patrickaupperle on 2010-04-13
I believe that you can put semicolons at the end of a line in Go. In my simple sample, it worked.

The thing about niches could be true, but Google backing could turn Go into something amazing. There is a slight possibility that it could become as fast as C one of these days. OOC should already be almost as fast as C. It is also easier to write in and provides some interesting new features. I also like the syntax in OOC. 

I see a slight possibility for a future for either of them.

---

