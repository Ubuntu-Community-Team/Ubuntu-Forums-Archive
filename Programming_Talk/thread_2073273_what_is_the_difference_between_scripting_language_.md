---
title: "what is the difference between scripting language and interpreted language ???"
date: 2012-10-19
forum: Programming Talk
---

### Post by vikkyhacks on 2012-10-19
This question is driving me mad ... please help me with simple answers

---

### Post by AlexDudko on 2012-10-19
They are the same. Every script needs an interpreter to be run.

---

### Post by MadCow108 on 2012-10-19
technically none, both are interpreted
scripting languages are interpreted languages focused on scripts. Get stuff done quickly by calling existing applications. E.g. Shell scripts with their native forking and piping.

a non-scripting interpreted languages focuses more on completeness of the language and syntax at expense of needing to write more code to do some stuff.

---

### Post by vikkyhacks on 2012-10-19
> **MadCow108 said:**
> a non-scripting interpreted languages focuses more on completeness of the language and syntax at expense of needing to write more code to do some stuff.

Any examples to support this idea ???

Cos from your answer i get that bash is a scripting language and languages like PHP are non-scripting interpreted languages ... 

But according to wiki  "PHP is a general-purpose server-side scripting language originally designed for Web development to produce dynamic Web pages."

---

### Post by AlexDudko on 2012-10-19
PHP, JavaScript and many others are scripting languages, they are just text file and require an interpreter to be executed. Java is compiled to bytecode but also needs an interpreter to be executed. Programmes written in these languages need an interpreter, they can't be compiled to a binary executable.
So, the answer to you question should be: Every scripting language needs an interpreter to be executed, but mind that not only scripting languages need an interpreter (Java). Interpreted language is a bit wider notion which comprises all languages that need an interpreter, not only scripting ones.

---

### Post by trent.josephsen on 2012-10-19
Interpreted languages are languages that use an interpreter. Scripting languages are languages that interpret a script.

Many scripting languages these days do not use what a purist would call an "interpreter". Those languages, including Python and Perl, are not interpreted directly, but instead compile to bytecode, which is interpreted in a virtual machine. To the programmer, though, the difference is transparent, and they are usually still considered interpreted languages.

Furthermore, any language can conceivably be used for writing scripts, and languages that are traditionally used for scripting can also be used for programs that aren't scripts, which makes the term "scripting language" also somewhat ambiguous. It's all semantics.

Practically, the terms are synonymous. I might use "interpreted" as the opposite of "compiled" to distinguish languages that have separate compilation and run phases (which is a technical point). On the other hand, if I contrast scripting languages with compiled languages, I'm probably thinking about the kinds of programs written in them (which is more subjective).

---

### Post by vikkyhacks on 2012-10-19
> **AlexDudko said:**
>  Interpreted language is a bit wider notion which comprises all languages that need an interpreter, not only scripting ones.

This makes it very clear of what interpreted languages are ... But how will you make a clear note of **what Scripting languages are ???**

---

### Post by MG&amp;TL on 2012-10-19
> **vikkyhacks said:**
> This makes it very clear of what interpreted languages are ... But how will you make a clear note of **what Scripting languages are ???**

Suggestion: do a little bash (scripting), then a little python (interpreted), then you might understand the (small) difference a bit better. 

Or just take them as the same thing. :)

---

### Post by vikkyhacks on 2012-10-19
> **MG&TL said:**
> Suggestion: do a little bash (scripting), then a little python (interpreted), then you might understand the (small) difference a bit better. 
:)

thanks for the suggestion ... I actually have done a bit of it before, If it was that way then I would call 
scripting language as the **ordered execution of some precompiled programs/commands/**(or what ever you call ls, ps, pwd .... as) which is mostly OS dependent like bash for Linux and batch for Windows
(forgive my noobness, if this perception is noobish)
**interpreted language as the interpretation of each and every line by the interpreter to the machine level language.** It mostly does not depend on the platform cos different interpreter exists for every OS to do the same task in various environment ...

this is the my current understanding of interpreted language and scripting language. But according to this perception PHP should be interpreted not scripted, but I am wrong(cos wiki says PHP is scripted) therefore my understanding is wrong. 

1. What is scripting language ??? 
2. How do I differentiate a script from a program ???

---

### Post by trent.josephsen on 2012-10-19
It just depends on context. If you're looking for a rule like "Programs shorter than N lines are scripts" or "programs written in any of these 12 languages are scripts" you're not going to find one. I've written a bunch of programs that I would call scripts; they're short, mostly in Python or Perl, and mostly do simple automation tasks. I've also written programs that I wouldn't call scripts, like a GUI Battleship game in Java. But you can do simple automation tasks in C and write fancy GUI programs in Python. Which ones are scripts? It's just not clear.

Scripts are generally understood to be short, which is subjective; used for automation, which is also subjective; and interpreted, which is almost meaningless. There's no hard-and-fast rule.

---

### Post by AlexDudko on 2012-10-19
> **vikkyhacks said:**
> With all the replies I get it clear of what Interpreted languages are ... But 
1. What are scripting languages ??? 
2. How can i differentiate a script from a program ???

A script is usually a text file, it consists of a command or a set of commands entered from keyboard and can be read and executed by an interpreter. One can edit it, make any changes to it. And it will be executed as it is. There's no need to do anything else with scripts.
There are some languages which need two stages: programme creation as a text file with a set of commands and compilation to a form which can be read and executed by an interpreter.

Script is a programme if you mean a computing term.

---

