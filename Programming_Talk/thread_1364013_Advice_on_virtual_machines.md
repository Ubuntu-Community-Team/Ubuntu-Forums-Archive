---
title: "Advice on virtual machines?"
date: 2009-12-25
forum: Programming Talk
---

### Post by maximinus_uk on 2009-12-25
I'm looking to implement a computer language using a virtual machine. I've already 'tested' the language by implementing using python. Now I'd like to transfer to using a virtual machine.

I first looked at Parrot, but the docs don't seem up to much. Now I'm looking at LLVM and the JVM. What I'm lacking is any advice from any other soul who has ventured before me.

Anybody?

---

### Post by CptPicard on 2009-12-25
Why are you not just implementing it on top of Common Lisp? SBCL is an excellent implementation :)

I do hear that all the buzz is around Parrot when it comes to dynamically typed languages. JVM is very optimized and mature but is, unfortunately, designed a bit too much around Java.

What kind of a language are you thinking of that is not already covered by Lisp?

---

### Post by maximinus_uk on 2009-12-25
My language is similar to Lisp already, and I'm doing it to learn more about the process of implementing a lisp-type language, otherwise I'd just use SBCL and have it done in a day or 2 :)

Also, the idea of using libs from other languages (like Clojure does) is a big plus point.

---

### Post by CptPicard on 2009-12-25
> **maximinus_uk said:**
> My language is similar to Lisp already, and I'm doing it to learn more about the process of implementing a lisp-type language

Just write a cons-manager, eval/apply and macro handling, and you're done. In a lot of ways, becoming a Lisper takes a lot of mystique out of programming language design and implementation as the general framework of Lisp is so damn strong :) 

I have actually toyed with the idea myself though -- I'm fascinated in particular by the way how in a Lisp system you can first write a rudimentary evaluator and compiler, and then just replace parts piecemeal as you go with better implementations written in your own Lisp and compiled by its own (hopefully ocnstantly better and better) compiler... targeting something like Parrot with that would be interesting. But it's perhaps a bit too much work and I'm sure someone is hacking away at it already :p

---

