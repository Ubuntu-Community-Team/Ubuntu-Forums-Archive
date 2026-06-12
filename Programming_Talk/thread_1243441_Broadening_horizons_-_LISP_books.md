---
title: "Broadening horizons - LISP books?"
date: 2009-08-18
forum: Programming Talk
---

### Post by Habbit on 2009-08-18
Hello there, fellow forum dwellers, lurkers and patrollers. I'm trying to broaden my programming horizons, which are pretty limited because I'm mostly a self-teaching nerd who has received nearly zero formal training in algorithms, concurrency, etc. In other words, the kind of programmer that insers a bubble sort in a Java program instead of using Arrays.sort (I only recently straightened that out in [ADSVote]("http://adsvote.sourceforge.net")).

I've been preached the enlightenment and higher-conscience state that my mind shall reach when I "get" LISP, and so I'd like to ask... what resources, either web pages or printed books, could I draw upon in order to learn the Tao of the holy language? Also, resources on algorithms and general programming "theory" would be appreciated. Thank you!

---

### Post by Drone022 on 2009-08-18
I read the first few chapters from [Practical Common Lisp](www.gigamonkeys.com/book/) before I decided I didnt have time to give Lisp a proper go.

---

### Post by nvteighen on 2009-08-18
I'm a happy Lisper :)

Let's see. Lisp is a difficult thing to grasp... To start with, there's no Lisp, but several Lisp **dialects** and each dialect may have several implementations. The most important dialects are Scheme and Common Lisp, and each of both represent one of the two philosophical views on Lisp. 

**Scheme** follows the idea of sticking as most as possible to McCarthy's original Lisp, which was more an algorithmic language than a programming language. Scheme is really simple, minimalistic and tends to favor pure-functional programming.

**Pros:**
1. Being less bloated and simple makes it easier for you to make the step into the Lisp world.
2. Its creators released a book called SICP which is online ([http://mitpress.mit.edu/sicp/](http://mitpress.mit.edu/sicp/)) and which not only teaches you Scheme but also discusses interesting things on programming.
3. Its creators also released a set of very funny (and interesting) videos for that book, which are also legally available at: [http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/](http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/)
4. Being a language that designed for conceptual clearness allows you to have a clearer look on programming in general.

**Cons:**
1. Too many implementations; all of them non-standard. The "original Scheme" is MIT/GNU Scheme, which has great features, but also lots of quirks. The "stablest Scheme" is PLT-Scheme, though it adds too much non-standard extensions that the PLT tutorials teach you as if they were portable.
2. Slow. *Very* slow. Being a academically driven language, its compiler support is very poor.
3. Another bad consequence of being a language more academical than practical is its lack of practical libraries. MIT/GNU Scheme at least has X11 (!), socket and some other bindings included... This problem would be solved if people started to write those libraries... :p
4. Its standard is followed by almost nobody...
5. Executable compiled images are available on some implementations and not quite good and too big (~12 MB for a minimal program).

**Common Lisp** follows the idea of making a practical Lisp for practical projects. That makes it more bloated, complex, somehow deviated from what McCarthy's ideas were for Lisp.

**Pros:**
1. Great implementations; most of them following the ANSI standard. The one I like most is SBCL, which is very popular and supported.
2. Lots of libraries... well, not as much as for the "mainstream" languages, but a good amount of them. There are even CPAN-like systems to grab them.
3. As it's a practical Lisp, the compiler developers are constantly trying to optimize them.
4. A central documentation site at: [http://www.lispworks.com/documentation/HyperSpec/Front/index.htm](http://www.lispworks.com/documentation/HyperSpec/Front/index.htm) 
5. It's possible to create executable compiled images.

**Cons:**
1. It makes access to Lisp a bit more difficult for its multiple features. It clouds the horizon a bit.
2. While compilation is very good, almost C-like in speed, the size of generated executable images is still too big (~20 MB for a minimal program).
3. Only a single decent learning resource (Practical Common Lisp, [http://gigamonkeys.com/book/](http://gigamonkeys.com/book/)) and not as clear as SICP is.

In my honest opinion, I'd start with Scheme to learn the basics of Lisp and then, when you've got it, jump into CL. 

There's another Lisp dialect, somewhat new, called Clojure. It follows Scheme's philosophy (aka "Lisp-1" philosophy), but as it runs on the Java Virtual Machine, it solves some of the "practical" issues of compilation and libraries... Although it's still very immature yet, it's something to keep an eye to.

Note to Lispers: Ok, I haven't discussed the continuations and hygienic macros in Scheme as an advantage over Common Lisp lack of explicit continuations and non-hygienic macros because I doubt someone will use that when starting to learn Lisp :p

---

### Post by hessiess on 2009-08-18
Personally the biggest problem that I have found with Lisp(common lisp) is the lack of decent, up to date libuerys, no standard support for networking and no standardised forin function interface. Clojure solves all these problems because of the JVM.

---

### Post by Habbit on 2009-08-18
Interesting. I had learned a bit of Scheme with the Programming Paradigms (CS107) course of SU. Well, I'll try to widge my way into these dialects with the tools you have shown me. Thank you all.

---

### Post by crush304 on 2009-08-18
[http://www.paulgraham.com/onlisp.html]("http://www.paulgraham.com/onlisp.html")

---

### Post by mmix on 2009-08-18
[http://en.wikipedia.org/wiki/Lisp_in_Small_Pieces](http://en.wikipedia.org/wiki/Lisp_in_Small_Pieces)

---

