---
title: "which functional language to learn?"
date: 2010-05-03
forum: Programming Talk
---

### Post by ja660k on 2010-05-03
hey guys, 
after the release of couchDB and its written in erlang. 
I started to get curious... is Erlang a good language to learn? 
or should i learn another functional language...
because functional languages are on the way back in (i've heard) so i may jump on the bandwagon early...
what is a good language to learn?

---

### Post by mmix on 2010-05-03
right tool for the right job.
wayttd? (what are you trying to do?)

each FL has it's own special domain.
you have to define the domain, choose it.

i heard ocaml is used for stock analysis market, 
lisp is used for various areas..
[http://lispjobs.wordpress.com/](http://lispjobs.wordpress.com/)

---

### Post by soltanis on 2010-05-03
Don't jump on it because it's a bandwagon. Functional programming isn't a silver bullet; it's another way of problem solving that tends to be effective and intuitive, so long as you can frame the problem correctly.

That being said, I recommend LISP, especially Common Lisp. If you've ever done programming before, or even if you haven't, it will blow your mind (you're telling me I can write code that writes code that writes code??). Haskell I've been told can be equally mind-blowing, but it's too strict for my tastes.

Really, any functional language is fine. I've found even Python can be used functionally (in an almost lisp-like manner with list comprehensions), with good results.

---

### Post by slavik on 2010-05-03
> **soltanis said:**
> Don't jump on it because it's a bandwagon. Functional programming isn't a silver bullet; it's another way of problem solving that tends to be effective and intuitive, so long as you can frame the problem correctly.

That being said, I recommend LISP, especially Common Lisp. If you've ever done programming before, or even if you haven't, it will blow your mind (you're telling me I can write code that writes code that writes code??). Haskell I've been told can be equally mind-blowing, but it's too strict for my tastes.

Really, any functional language is fine. I've found even Python can be used functionally (in an almost lisp-like manner with list comprehensions), with good results.
C can be functional, too ... it's just very difficult to iterate over a list with C versus a language with lists a native datatype.

that being said ... haskel.

---

### Post by nikstard on 2010-05-03
> **slavik said:**
> C can be functional, too ... it's just very difficult to iterate over a list with C versus a language with lists a native datatype.


C is not a functional language in any relevant sense. For that you'd need lexical closures and garbage collection. Function pointers aren't really enough to write meaningful functional programs. Also, lists need not be a native datatype in any language that supports either defining or structs/classes/records or that has closures.

---

### Post by nikstard on 2010-05-03
Oh, and I recommend Haskell too. It has good implementation (GHC) and is quite popular so you'll find a lot of information about it. It also enforces the functional style, so you can't resort to "writing C" in it. Lisps are good, and I particularly like Common Lisp, but I wouldn't recommend it if you expressly want to explore only functional programming, since Common Lisp really is a multi-paradigm language.

---

### Post by CptPicard on 2010-05-03
Another take would be that because the functional paradigm seems to be a bit "hard" for noobs to it, and because Lisp is very flexible *and* multiparadigm, Lisp would be the preferable language. IMO the interesting stuff is seeing how functional style relates to other solutions, how object-oriented programming can be seen as a consequence of closures, and so on.

Haskell requires quite a bit of understanding its own special things such as the type system... but, of course learning that is good too...

---

### Post by dragos2 on 2010-05-03
Scala, of course :)

---

### Post by Simian Man on 2010-05-03
If you want to learn as much about programming as possible, you really have to learn both Haskell and Common Lisp since both have features that aren't found in any other major programming language.

As for a functional programming language to use practically, I like Ocaml :).

---

### Post by nvteighen on 2010-05-03
Hm... as a starting language, Scheme is nicer than Common Lisp because it introduces the fundamentals of programming and functional programming without all the amount of features CL has. The issue is that CL is much more suited for practical projects than Scheme... not only because of the language but also because of the poor interoperability between implementations.

---

### Post by ja660k on 2010-05-03
Common Lisp it is then.

I already know many other languages. None of them functional, the best i know for that is python.

I think it will be good to add CL to my resume :)
thanks guys.

---

### Post by Lux Perpetua on 2010-05-03
> **slavik said:**
> C can be functional, too ... it's just very difficult to iterate over a list with C versus a language with lists a native datatype.

that being said ... haskel.No, it can't. C can't express most interesting functions whose return type is a function. For example: ```

typedef double (*real_function)(double);

real_function antiderivative(real_function f) {
    /* Can't do it. */
}
```It's because every function has to be compiled statically; one can't construct a function on-the-fly.

---

### Post by batrick on 2010-05-03
Take a look at Lua. It's pretty easy to learn and has everything you need to write a functional program.

---

### Post by ja660k on 2010-05-04
> **batrick said:**
> Take a look at Lua. It's pretty easy to learn and has everything you need to write a functional program.

i dabbled into lua, for my conky :)

---

