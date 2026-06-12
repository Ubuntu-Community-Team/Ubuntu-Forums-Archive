---
title: "Python and Go and the Binary"
date: 2014-07-09
forum: Programming Talk
---

### Post by Sir_Sword on 2014-07-09
Right now it would seem that Python is one of the most popular and most widely supported of the newer progamming languages.  Go is another newer programming language which Google is trying to gain more support for.  Python is an interpreted language while Go compiles to machine code.

I've heard it said before that Go has the easiness and flexibility of Python while having the speed of a compiled language.  If the only benefit that really seperates Go from Python is the fact that it's compiled to machine code, do you think there's a chance the Python group might eventually release a compiler to compile Python to machine code as well?

---

### Post by ian-weisser on 2014-07-09
Python already compiles...if you ask the interpreter to do so. Look for .pyc files

---

### Post by Sir_Sword on 2014-07-10
The .pyc files are python code compiled into bytecode for the Python virtual machine so while it is faster than purely interpreted Python, it's still not actual machine code like Go is compiled to.  So I'm wondering if in an attempt to compete with languages like Go, or just to increase performance in general, the Python community will ever create a compiler that compiles directly to machine code.

---

### Post by ian-weisser on 2014-07-10
I've seen it discussed at Python.org, but generally that community seems insufficiently interested to pursue the idea anytime soon.

I find interpreted Python to be pretty fast for most purposes...if the program is structured properly.

I also find that Go (and Vala and others) appeal to a very different market than Python (and Perl and others). Each is appropriate in different circumstances.

---

### Post by michael171 on 2014-07-10
Is creating a frozen binary the same as compiling to machine code?  Interesting though, ill have to investigate this go lanaguage as I love learning new languages but will have to be cautious not to tray from my python learning path.

---

### Post by trent.josephsen on 2014-07-10
Go doesn't exactly compile to binary in the same sense as C.

[quote=http://golang.org/doc/faq] Why is my trivial program such a large binary?

The linkers in the gc tool chain (5l, 6l, and 8l) do static linking. All **Go binaries therefore include the Go run-time**, along with the run-time type information necessary to support dynamic type checks, reflection, and even panic-time stack traces.

A simple C "hello, world" program compiled and linked statically using gcc on Linux is around 750 kB, including an implementation of printf. An equivalent Go program using fmt.Printf is around 1.2 MB, but that includes more powerful run-time support.[/quote]

In other words, Go is "compiled" in a manner somewhat analogous to how py2exe and freeze work. This is basically the only way to support dynamic dispatch in a compiled language. I assume Go code isn't embedded in the binary as text, but either as some kind of AST or actually compiled to calls into the Go runtime. Nevertheless, your method calls (the dynamic ones at least) certainly aren't being pre-compiled to machine code.

You could write Go code that avoids dynamic dispatch, and can therefore be compiled statically without linking the Go runtime. I don't know if anybody does that for Go, [but they certainly do for Python](https://www.google.com/search?q=rpython). But as the RPython folks say,
[quote=https://rpython.readthedocs.org/en/improve-docs/faq.html]Yes, it is possible with enough effort to compile small self-contained pieces of RPython code doing a few performance-sensitive things. But this case is not interesting for us. **If you needed to rewrite the code in RPython, you could as well have rewritten it in C or C++ or Java** for example. These are much more supported, much more documented languages :-)[/quote]

To make a long story still longer, there are differences between Go and Python that would make you want to choose one over the other, but "compiled vs. interpreted" probably isn't the top of the list. If I were doing a project for which both were options, I'd be more concerned about the other differences -- Unicode, exceptions, concurrency, inheritance, etc. But that's probably fairly rare. Here's a short Python 3 program that will tell you whether you should use Go:
```
works_for_google = 'y' in input("Are you working for Google? ").lower()
if not works_for_google:
    works_for_google = ('y' in input("Do your technical challenges and corporate strategy align with Google's? ").lower()
        and 'y' not in input("Do you work for Microsoft? "))
if works_for_google:
    print("You should use Go.")
else:
    print("There are plenty of other languages out there.")
```

---

### Post by The Cog on 2014-07-10
I think you are mistaken there. I think "All Go binaries therefore include the Go run-time..." means that they include the statically linked libraries instead of requiring .so shared objects. That is quite different to including an interpreter, which is what a frozen python executable contains.

However, last time I compared a small program written in both go and python, the python version was significantly faster. I think that being a high level language, python tends to spend a lot of its time inside interpreter calls that are written in C anyway. But that will depend quite a lot on what the program is doing, and my program was almost exclusively manipulating large dicts/maps.

---

### Post by ofnuts on 2014-07-10
> **trent.josephsen said:**
> To make a long story still longer, there are differences between Go and Python that would make you want to choose one over the other, but "compiled vs. interpreted" probably isn't the top of the list. If I were doing a project for which both were options, I'd be more concerned about the other differences -- Unicode, exceptions, concurrency, inheritance, etc. But that's probably fairly rare. Here's a short Python 3 program that will tell you whether you should use Go:
```
works_for_google = 'y' in input("Are you working for Google? ").lower()
if not works_for_google:
    works_for_google = ('y' in input("Do your technical challenges and corporate strategy align with Google's? ").lower()
        and 'y' not in input("Do you work for Microsoft? "))
if works_for_google:
    print("You should use Go.")
else:
    print("There are plenty of other languages out there.")
```

Obvious bug here: A positive answer to "Do you work for Microsoft? " elicits "There are plenty of other languages out there.". This C#an't be C#orreC#t.

---

### Post by trent.josephsen on 2014-07-10
> **The Cog said:**
> I think you are mistaken there. I think "All Go binaries therefore include the Go run-time..." means that they include the statically linked libraries instead of requiring .so shared objects. That is quite different to including an interpreter, which is what a frozen python executable contains.
Yes, I'm sure you're right about that. The comparison to freeze was inappropriate. (There's a reason I don't normally post before noon.) But what I should have said was that Go "binaries" still have to do all the hard work of dynamic dispatch, which is the potentially slowest part of running a program in any language that provides it. Therefore, any non-marginal performance advantage Go has over Python is likely to be a QoI issue, not a language issue.

---

### Post by Sir_Sword on 2014-07-10
> **ian-weisser said:**
> I also find that Go (and Vala and others) appeal to a very different market than Python (and Perl and others). Each is appropriate in different circumstances.

The reason I'm comparing Python and Go is because I've heard people say that Go is just as easy and fun as Python but has the speed advantage of a truly compiled language, so I was curious as to Python's take on this.  It sounds like however much of a speed increase Go does or doesn't have over Python, Python is content to stay an interpreted language.

> **The Cog said:**
> I think you are mistaken there. I think "All Go binaries therefore include the Go run-time..." means that they include the statically linked libraries instead of requiring .so shared objects. That is quite different to including an interpreter, which is what a frozen python executable contains.

If the default behavior of Go compilation is to statically link all libraries, and that's the known default behavior, that brings up the interesting point that anyone that makes libraries for Go will have to give them a license friendly to that behavior.  That's really a different topic entirely, but still interesting.

---

### Post by xb12x2 on 2014-07-10
> **Sir_Sword said:**
>  If the only benefit that really seperates Go from Python is the fact that it's compiled to machine code, do you think there's a chance the Python group might eventually release a compiler to compile Python to machine code as well?

I've read some real experts' opinions on developing a compiled version of Python (compiler writers, language researchers, etc). Most agree that  not all the features that make Python so popular could be duplicated in a compiled version. 

As much as I like Python, interpreted languages have one major disadvantage: 

You cannot count on all users in your target group having the exact version of the interpreter required (or having an interpreter at all). And you cannot count on them having the permissions and expertise required to install the correct interpreter and change their runtime environment accordingly.

 Yes, you can bundle your Python application with the correct version of the interpreter using a utility like Freeze, etc, but that's not always straight forward and can be very time-consuming just getting it to bundle. And your customers can still have runtime problems that never happened on your development system, because of all the unforseen differences in environments, etc.

So unless you're targeting an absolutely known, locked-down environment that you can recreate on your own system, it's better in many cases to use a compiled language and tools (static libs) that create native binaries.

---

### Post by Sir_Sword on 2014-07-11
> **xb12x2 said:**
> You cannot count on all users in your target group having the exact version of the interpreter required (or having an interpreter at all). And you cannot count on them having the permissions and expertise required to install the correct interpreter and change their runtime environment accordingly.

Java has this same issue and with Java if you're going to distribute a program with the official JRE you have to distribute the whole JRE, not just the parts your program needs, which means even a simple program will be 100+ megs.  But I do think that packaged JREs seem to run better on unknown systems than packaged Python VMs.  Then there are other options of third-party Java VMs which you can package a Java program with instead which claim to make smaller, faster Java packages.

I'm really interested in Go, but even though the language has been around for a while now it still seems like library support for it isn't very well developed yet.

---

