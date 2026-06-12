---
title: "why is java a platform ?"
date: 2008-06-26
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-26
this sounds like "for dummies" ..but i still dont understand why is java called a platform ..and not just a programming language ...the reason is probably that i dont know exactly how do we define a platform.

---

### Post by CptPicard on 2008-06-26
Because it's not just a language, but a virtual machine plus libraries. In other words, it's a whole package on top of the host platform. From "inside Java", it's very hard to tell where exactly you're being run, and that's the whole point :)

---

### Post by dominiquec on 2008-06-26
Largely because you write programs and compile them for a virtual machine, essentially, your platform.

---

### Post by wdaniels on 2008-06-26
It's only about context, you can refer to the Java programming language or you can refer to the virtual machine (JVM) and/or runtime environment (JRE) which constitute a platform. They are actually separate concepts, for example you can compile Java programs to run on the Mono/.NET platforms (IKVM). Potentially, programs written in some other language could be compiled to run on a Java platform, though I've not heard of this.

---

### Post by CptPicard on 2008-06-26
> **wdaniels said:**
> Potentially, programs written in some other language could be compiled to run on a Java platform, though I've not heard of this.

Groovy, JRuby, Jython, Scala and for a Lisp, Clojure. The VM is not limited to running just bytecode compiled from Java.

(There are many others)

---

### Post by evozniak on 2008-06-26
java is not only a language, is a plataform abstraction layer.

develop for linux plataform, develop for windows plataform, develop for mac plataform
develop for java plataform and forget everything else over there.
compile from one, run in every!

now sound like "for dummies"?

---

### Post by dexter.deepak on 2008-06-26
> **CptPicard said:**
> Because it's not just a language, but a virtual machine plus libraries. 

i think virtual machine is no different than an interpreter.
an IDE like TurboC (on windows) provides an interpreter, and C has also got its libraries. by this definition, isnt C also a platform ?

The VM is not limited to running just bytecode compiled from Java.

this was good ...but induced one more thought, can we simply extend the functionality of JVM/java platform to make "it" an independent OS ?

---

### Post by CptPicard on 2008-06-26
> **dexter.deepak said:**
> i think virtual machine is no different than an interpreter.

An interpreter is a virtual machine, but a virtual machine is not necessarily any more of an interpreter than a normal CPU is an interpreter for machine code. An interpreter is generally something that parses the source, and then evaluates the resulting abstract syntax tree.

The Java VM runs sort of machine code, for a virtual, abstract CPU. That's still the short version, today's JIT compilation does an on the fly compilation to native code for the target CPU from that bytecode.

If this kind of "interpretation" makes Java an interpreter, then you might just as well say that assembly is being interpreted by the processor  -- which it actually is these days, the internal microcode no longer bears much resemblance to the original x86 instruction set which is essentially just being emulated for compatibility reasons.

> an IDE like TurboC (on windows) provides an interpreter, and C has also got its libraries. by this definition, isnt C also a platform ?

IDEs tend to have parsers for the language you're working on, but they don't have interpreters. They do not run the code in any fashion internally, in particular without first running it through the compiler and then running the binary. (Assuming here you're in an IDE for a compiled language of course).

But you are correct in the sense that the underlying OS plus standard library combined to C is another form of "platform". There shouldn't be any kind of a contradiction in terms there.

> 
this was good ...but induced one more thought, can we simply extend the functionality of JVM/java platform to make "it" an independent OS ?

Now, there is nothing to stop you from actually creating hardware that runs Java bytecode.. I think there actually exists such processors. And then you could write an OS in Java... but do bear in mind that OSes do a lot of stuff you'd have to add to the platform (nothing would stop you from doing it though).

---

### Post by dtmilano on 2008-06-26
Check [JavaOS]("http://en.wikipedia.org/wiki/JavaOS"), an OS based on JVM.
Also, Java is sometimes used as a programing language for another platform, not the standard JVM, as is the case of [Android]("http://code.google.com/android/") that uses Dalvik as the VM.

---

### Post by wdaniels on 2008-06-26
> **CptPicard said:**
> Groovy, JRuby, Jython, Scala and for a Lisp, Clojure. The VM is not limited to running just bytecode compiled from Java.

(There are many others)

Wow, I would have guessed that there'd be at least one example somewhere, but I hadn't heard of any of these :D

---

### Post by dexter.deepak on 2008-06-26
thanks a lot for this discussion !!!:guitar:

---

### Post by pmasiar on 2008-06-26
Java is platform (or more exactly JVM is platform) like Windows.NET is a platform. It defines many many APIs for programs which run on this platform. Java is just first (system: most deep) language for JVM, like C# is for .NET

Java was designed to be alternative to Windows and (many incompatible) Unixes, so they reimplemented all that functionality (and this is part of the reason why Java is slower than real "native" OOP code like C++). "Write once run anywhere" is part of the lure, now, when Unix successor is known (Linux), and only 2 major platforms remain standing, Java is the odd third.

Maybe mobile appliances (and new more compact reimplementation as Android) will give Java another chance. If not, Java will become new OOP Cobol: widely used by PHB and often hated. :-)

---

### Post by CptPicard on 2008-06-26
> **pmasiar said:**
>  If not, Java will become new OOP Cobol: widely used by PHB and often hated. :-)

Oh, come on. JVM the platform isn't bad at all -- IMO it has great promise. It is one of the most optimized pieces of software on the planet. The language ... well.. it is boring and insignificant in this context.

Now, if we only had two things I miss... 1) ability to do tailcall optimization (so that we didn't have to have explicit "recur" in otherwise great languages like Clojure) and 2) proper integration into OS so that different VM invocations could share resources such as RAM... that would be perfect.

---

### Post by dexter.deepak on 2008-06-26
> **CptPicard said:**
>  1) ability to do tailcall optimization (so that we didn't have to have explicit "recur" in otherwise great languages like Clojure) 

that was totally over the head !!:confused::confused:

---

### Post by Quikee on 2008-06-26
> **CptPicard said:**
> 
Now, if we only had two things I miss... 1) ability to do tailcall optimization (so that we didn't have to have explicit "recur" in otherwise great languages like Clojure) and 2) proper integration into OS so that different VM invocations could share resources such as RAM... that would be perfect.

Optimizations and customizations of the JVM are being done in the [Da Vinci Machine Project]("http://openjdk.java.net/projects/mlvm/") which is a "playground" for new ideas that could be integrated in a future JVM release. What they are working on is stated [here]("http://openjdk.java.net/projects/mlvm/subprojects.html") - one of the things mentioned are tail calls.

---

