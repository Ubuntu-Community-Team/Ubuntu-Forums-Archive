---
title: "A few questions about clojure"
date: 2008-08-19
forum: Programming Talk
---

### Post by Tim Sharitt on 2008-08-19
I've been exploring a few different programming languages lately and was intrigued by clojure (I like the idea of the JVM, just not the java language.) I've been doing some reading but some of the information I've found seems conflicting.
First, does code written in clojure compile into java byte code or does the clojure interpreter simply run on top of the JVM?
Second, is it possible to use java libraries (like the swing gui for example) in clojure programs?
I don't have a lot of experience with the java platform, other than reading an introductory java programming book, so please forgive me if I'm a little confused on how the VM actually works.

---

### Post by CptPicard on 2008-08-19
> **Tim Sharitt said:**
> 
First, does code written in clojure compile into java byte code or does the clojure interpreter simply run on top of the JVM?

The clojure source compiles the source into Java bytecode which is then executed, so the source itself is not interpreted. However, doing a lisp on top of JVM means that all sorts of runtime bytecode hacks are needed AFAIK so that you are not getting actual .class files from the compiler -- all the compilation and bytecode-mangling is done straight in RAM.


> Second, is it possible to use java libraries (like the swing gui for example) in clojure programs?

Yes, and very easily too. This is one of Clojure's huge strong points.

---

### Post by Tim Sharitt on 2008-08-20
> **CptPicard said:**
> The clojure source compiles the source into Java bytecode which is then executed, so the source itself is not interpreted. However, doing a lisp on top of JVM means that all sorts of runtime bytecode hacks are needed AFAIK so that you are not getting actual .class files from the compiler -- all the compilation and bytecode-mangling is done straight in RAM.


I'm not totally sure I understand what you're saying about not getting an actual class so let me ask a more specific question. If write program in clojure and send it to a friend, what would he need to run the program, assuming he already has the basic jre installed?

---

### Post by CptPicard on 2008-08-20
Source and the clojure jar so that he can load source into the repl, which compiles it into Java bytecode and runs it. :)

Lisp in general is the whole environment so this is actually pretty much how it's done elsewhere too, it's just that there is no way to dump .classes out of Clojure in the sense you can dump .fasl out of SBCL...

---

### Post by Tim Sharitt on 2008-08-20
That's what I thought. I reading a tutorial that metioned compiling the source to java byte code, but it wasn't clear on if it was done at run time or a .class file. Thanks for the clarification.

---

### Post by CptPicard on 2008-08-20
Admittedly I would strongly prefer having .classes to distribute even if there was a clojure.jar dependency, but apparently there is some pretty deep technical and "lispy" reason why you can't do static compilation like that.

Clojure still is my favourite lisp at the moment though, and you can't ignore the huge benefit of having the entire Java stack at your disposal... now if only the Enclojure plugin for Netbeans actually started working for me, I'd be 150% sold.

---

### Post by dribeas on 2008-08-20
> **CptPicard said:**
> Admittedly I would strongly prefer having .classes to distribute even if there was a clojure.jar dependency, but apparently there is some pretty deep technical and "lispy" reason why you can't do static compilation like that.

The reason is that lisp is a more powerful language than java. Now, for the definition of power with programming languages it boils down to a phrase:

A language is more powerful than another if the only way of implementing some operations in the less powerful language is by creating an interpreter of the more powerful language (or some equivalent).

I don't know lisp, and I favor C++, so don't take this as a flame war on what is better, just that some of the things that lisp does can only be expressed in Java with an interpreter. That is what clojure is about.

I wish I had time to learn lisp or scheme...

---

### Post by CptPicard on 2008-08-20
> **dribeas said:**
> 
A language is more powerful than another if the only way of implementing some operations in the less powerful language is by creating an interpreter of the more powerful language (or some equivalent).

Please read some of the "language flamewar" threads and you will discover I am the last person on the forum you need to actually tell this -- could have come straight from one of my posts ;)

Of course the overall reason is exactly this, it's just that there is an even more specific reason that I read and subsequently forgot -- as I said above, SBCL (which is Common Lisp environment) does compile .fasl which are bytecode. Can't do the same on JVM :)

> I don't know lisp, and I favor C++, so don't take this as a flame war on what is better

Lisp is. Dump C++. ;)

Oh yeah, you seem to be on the Light Side of The Force. Welcome to the High-Level Language crowd.

---

