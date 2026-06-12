---
title: "What is the difference between a Programming Language and a Scripting Language?"
date: 2010-01-16
forum: Programming Talk
---

### Post by Burky on 2010-01-16
At risk of sounding stupid, in which I could care less. What is the difference between a programming language and a scripting language?

---

### Post by FreshP on 2010-01-16
First, a scripting language IS a programming language.  Anyway, a scripting language uses an interpreter, a non-scripting (compiled) language uses a compiler. You can look around to see what an interpreter and a compiler is.

---

### Post by mobilediesel on 2010-01-16
> **Burky said:**
> At risk of sounding stupid, in which I could care less. What is the difference between a programming language and a scripting language?

A scripting language is a programming language.

From [Wikipedia]("http://en.wikipedia.org/wiki/Scripting_Language"):
> A scripting language, script language or extension language is a programming language that allows control of one or more software applications. "Scripts" are distinct from the core code of the application, which is usually written in a different language, and are often created or at least modified by the end-user.

---

### Post by Burky on 2010-01-16
Thanks guys. This helps.

---

### Post by Simian Man on 2010-01-16
Originally a scripting language was interpreted while a programming language was compiled.  Nowadays, that isn't really a useful division because most languages nowadays use a hybrid of the two and others can be compiled or interpreted.

What people really mean when they differentiate between scripts and programs is that programs are generally large, taking up thousands of lines of code and split up into dozens of files.  Scripts, on the other hand are usually quite small and are written in one file.  They also are often called by another program; javascript in a web browser or game mods for example.

So a programming language is generally a language used to write (large) programs, while a scripting language is used to write short scripts.  Any language can really be used for both, but few people would choose to write scripts in C or programs in lua.  Some languages, like Python, work well for both.

---

### Post by SunSpyda on 2010-01-16
The difference is *very* hazy. Use a range of high-level languages, and work out your own definition.

---

### Post by CptPicard on 2010-01-16
While recognizing that scripting languages are a subset of programming languages, IMO the distinctive feature of scripting languages really is the existence of an additional piece of software that executes the program.

Of course, it should be remembered that even native-compiled languages rely on a lot of other software... standard library, other libraries, operating system...

---

### Post by denarced on 2010-01-16
> **CptPicard said:**
> While recognizing that scripting languages are a subset of programming languages, IMO the distinctive feature of scripting languages really is the existence of an additional piece of software that executes the program.

Of course, it should be remembered that even native-compiled languages rely on a lot of other software... standard library, other libraries, operating system...

I agree to a large degree on what you're saying. The definition would be pretty simple if it went this: "scripting runs on another software and not on OS and script isn't compiled". A lot of languages fit into this definition but the first that comes to my mind that doesn't, is java. In a way it's compiled(sort of) but the execution isn't on OS.. So no clear-cut definition :|

---

### Post by Reiger on 2010-01-16
That is not what CptPicard meant, I think.

What he refers to if I understand him correctly, is that the difference between a scripting language and a (general) programming language is that a scripting language runs in what amounts to a domain-specific interpreter. E.g. GIMP includes a scheme interpreter to manipulate images with -- and that is &#8216;all&#8217; it does. It's not a general interpreter for arbitrary scheme code; it is a special interpreter for manipulating the internals of GIMP and it does just that, and only that. IOW: you won't get to write database tools on top of that.

In that sense, scripting languages can be defined as a programming language (both) restricted to and augmented with symbols for a domain specific subset or problem field if you will.

---

### Post by CptPicard on 2010-01-16
No, that quite specifically was not a way I would like to be interpreted :) I guess my usage of "subset of programming languages" was a slightly dangerous wording, it can be read wrong... I just meant that scripting languages quite simply are programming languages.

Scripting languages can be specialized, but in that case they run the risk of actually becoming so domain-specific that they are no longer Turing-complete -- that is, they are no longer general-purpose programming tools in the sense that you can take "any problem" and tackle it just as well as some "any other problem". Even when they maintain Turing-completeness it can be so obscure that you won't be using the language for general programming (think XSLT).

Of course, though, a typical place where you will find a scripting language is as an extension point to some other application.

---

### Post by nvteighen on 2010-01-17
IMO, "scripting language" is one of the most confusing concepts in the programming world. If you define scripting language as "language that uses an interpeter", then you'd have to say Perl, Python, awk, Lisp, Ruby, etc. are scripting languages as opposed to Java, C#, C, C++, Assembly, Objective-C...  Such a definition would immediately fall down when applied to FASL Lisp compiled code, Lisp images, Python .pyc's and even Javascript, as the V8 engine (Chromium/Google Chrome) precompiles it... even Perl is precompiled, though you don't get the compiled file. 

So? If you then try the "scripting" = "language used in an interactive environment", you end up without awk and sed which some consider to be "scripting languages"... and having Forth (a low-level language) as one... :P

The confusion, IMO, comes from the fact that that concept is referring to a certain use of certain programming languages and wrongly promoted into a "programming language type". There are some programming activities called "scripting" and some languages are usually very suited and used for those tasks, but without a clear common factor I can think of for create a new abstraction layer like "scripting language".

---

### Post by grayrainbow on 2010-01-17
> Of course, it should be remembered that even native-compiled languages rely on a lot of other software... standard library, other libraries, operating system...
Is this mean that those 'other software' come from...magic? :o But they surely rely on compiler :)

In the past I would say that programming language is something that one could use to create OS and basic libraries, and everything else is script in some form. Nowadays with merge of parts of C++ with parts of Lisp(result is java&C# basiclly) the border is quite fuzzy, and the size of programs you write with some language become more as a factor. But maybe the biggest difference today is that scripts are run from interpreter and other languages compile to machine code(virtual machine included). If one is too pedantic, the difference between VM and interpreter could also be quite fuzzy.
Also C++ template metaprogramming and Lisp macros could be somehow define as scripts inside the language itself(alto Lisp is script by itself).

---

### Post by MadMan2k on 2010-01-17
scripting languages are programming languages and any language can be compiled and interpreted.
And any difference is neglectible anyway as there is no clear border between a compiler and an interpreter [SIZE="7"].[/SIZE]

---

### Post by The Cog on 2010-01-18
A difference I saw once that really chimed with me is that a scripting language is one that is primarily designed for automating other processes, whereas a programming language is primarily intended to solve problems itself.

Using this distinction, bash, DOS batch files and the like are scripting languages that largely emulate and automate what a user would do, launching grep, sed, rsync etc. to do the real work. Java, C, python etc, are programming languages that remain mainly within that language to solve whatever the problem is. 

Of course, scripting languages can solve some problems without resorting to launching sub-processes, and C programs can launch other processes to achieve their objectives. But I do feel that the languages do mostly fall into one of these two camps, and it seems a good description of a scripting language to me. I really don't know which camp I would place perl in, but the fact that python has to use library calls to launch sub-processes (popen or os.system) screams to me that it is not primarily aimed at automating sub-processes.

---

### Post by slavik on 2010-01-19
let's not confuse "programming vs. scripting" with "compiled vs. interpreted".

scripting languages can be compiled (see UnrealScript), and programming languages can be interpreted (BASIC).

a way differentiate a compiled language from an interpreted language (I found this to be a decent guide, not that it at all matters) is that in a compiled language, the compilation step is explicit, whereas in an interpreted language it is not.

---

