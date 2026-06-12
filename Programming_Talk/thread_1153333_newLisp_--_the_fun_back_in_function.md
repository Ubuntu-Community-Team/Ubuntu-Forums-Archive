---
title: "newLisp -- the fun back in function?"
date: 2009-05-08
forum: Programming Talk
---

### Post by soltanis on 2009-05-08
I've been recently looking into the newLisp language, a lisp variant not conforming to Scheme or ANSI CL:

[www.newlisp.org](www.newlisp.org)

It's pretty good in some regards, pretty bad in others.
First of all, its got a lighter memory footprint than most Common Lisps; but it isn't minimalistic like Scheme. It can run as a TCP/IP daemon (receiving lisp commands over sockets), as a webserver, as a standalone application, as an interpreter. It has full-fledged macros, first class functions, an OO facility that is in my opinion better than CLOS, and the full run of the lisp favorites (car, cdr, map, apply, funcall..). It has the best FFI I have seen among any Lisp (no need to write any wrappers, can import C libraries straight off), and native sockets facilities. There is a Tk extension as well.

But (here's the downside) in some places its syntax is funny, and it doesn't have support for real closures.

Nonetheless, I would recommend it; it looks like a good language all around, even if it is weak in some places.

---

### Post by Cracauer on 2009-05-08
No closures? Is this some kind of joke?

---

### Post by Reiger on 2009-05-08
> **soltanis said:**
> It has full-fledged macros, first class functions, 
> it doesn't have support for real closures.

Now I don't understand: either you have functions as first-class values or you don't. If you do: then you **automatically** have closures because functions as first-class values requires, to show you in Haskell:
```

foo = (\ x -> x + 5) -- given an x, add 5 to x
bar = map foo [1..5] 
baz f = foo $ (f 5) -- apply foo to f(5), e.g.: baz (*5) = 30
-- above can be rewritten as baz = (\ f -> (\x -> x+ 5) $ (f 5)) 

```

In Haskell every function is either anonimous as a lambda statement (a closure by all means) *or* a "named" lambda statement, because in Haskell you virtually have lambda statements only and everything is defined out of that by induction.

So if you don't have support for closures; how in the world do you have support for _true_ first-class functions? What becomes of functions as first class values during function composition, if you don't have closures (seeing as the result of function composition is nearly always going to end up as a closure) ... ?

... Or am I failing to spot the obvious here?

---

### Post by Cracauer on 2009-05-08
I guess they mean elisp style no access to lexical scope. Kind of takes the fun out of anonymous functions.

---

### Post by ibuclaw on 2009-05-08
> **Cracauer said:**
> I guess they mean elisp style no access to lexical scope. Kind of takes the fun out of anonymous functions.

Looks like newLisp uses variable expansion and namespaces to achieve the same/similar type of closures to Scheme: [http://www.newlisp.org/index.cgi?Closures](http://www.newlisp.org/index.cgi?Closures)

The **context** is lexical, but the **namespace** is dynamic...

But I suppose you'll just have to test it to see if you can achieve the same kind of "anonymous" functionality.

Regards
Iain

---

### Post by CptPicard on 2009-05-08
> **Reiger said:**
> Now I don't understand: either you have functions as first-class values or you don't. If you do: then you **automatically** have closures

To be strict, this is not true. It is a common misconception which I am also personally guilty of to sometimes to talk of lambda expressions/first-class function objects and closures as the same thing. They are not. It's just a convenient shortcut :)

The closure is the "set of bindings visible at the point of definition" of, say, the lambda expression. You can easily have a function object without it having an associated closure -- this would mean it can't access anything outside its own scope. Even C function pointers would pretty much do.

When it comes to actually implementing a programming language, genuine closures really are more tricky than they appear at first sight. You need to be able to retain the context of some definition even after its immediate stack frame is gone... it essentially mandates garbage collection and such.

---

