---
title: "Compiling/Interpreting"
date: 2009-07-23
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-23
Are these 2 only ways of converting program to executables
Why is there no in between method or different approach?

---

### Post by CptPicard on 2009-07-23
Well, it all boils down to the fundamental theoretical exchangeability of Turing-complete languages. You can write an interpreter for any of them in any other, and essentially from the program's point of view, it really does not even matter what it is "running on".

The difference between a compiler and an interpreter is in a lot of ways not all that important... a compiler just transforms one language into the specific representation required by the machine. A "pure" interpreter essentially walks the syntax tree of the language, executing as it goes.

There *are* intermediate forms -- bytecode compilation, after which the bytecode is run through an interpreter, and Just-In-Time compilation, where the bytecode is compiled to native machine code prior to execution.

---

### Post by SunSpyda on 2009-07-23
They both are interpreted. It's just that one's interpreted by the CPU, whilst the other is interpreted by a layer above the CPU.

---

