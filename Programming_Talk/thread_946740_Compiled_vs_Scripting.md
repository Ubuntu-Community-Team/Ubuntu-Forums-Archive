---
title: "Compiled vs Scripting"
date: 2008-10-13
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-13
What do you like more and tend to use more for your personal projects...a compiled language (like C) or a scripting (interprited) one (like python, ruby, or perl)?

---

### Post by scragar on 2008-10-13
Well I'm very impatient, so interprited(scripting) languages are my preference, makes it easier to share the source as well.

---

### Post by nvteighen on 2008-10-13
It depends. I currently use interpreted languages as I have discovered their value quite late. 

For example, my FreeTruco project (see sig) is written "on" Scheme, with the principle of creating some sort of "interpreter" capable of understanding the commands of the Truco card game... But I "cheat" a bit by just creating a "programming language" embedded in Scheme (read "Lisp") and therefore, any Scheme-interpreter should be able to work as a FreeTruco-interpreter. Such things are impossible in compiled languages, but only in interpreted ones... try it in Python and it should work too.

That's just a little feature that I like of interpreted languages: the ability to create a code that uses the very same interpreter as interface. 

But also, if they have an interpreter shell, well the fun you get of breaking things and knowing you're actually not breaking anything is great! (and you learn a lot...). And the quickening of development is really impressive (and it's not just Python, try some Scheme... or just any other interpreted language w/shell).

BTW, if you wonder, I consider Java to be a compiled language, even tough it compiles to Java bytecode, as the development cycle is the same as C's. Python is also compiled, but the point of being "interpreted", in my honest opinion, is in that you can rely on an interpreter you have user-access to... not a virtual machine, which at the end acts exactly the same as the machine when using a native-compiled C program... or maybe I'm confusing interpreted with scripting?? :p

---

### Post by jimi_hendrix on 2008-10-13
> **nvteighen said:**
> 
BTW, if you wonder, I consider Java to be a compiled language, even tough it compiles to Java bytecode

[wikipedia]("http://en.wikipedia.org/wiki/Categorical_list_of_programming_languages") does too

---

### Post by OutOfReach on 2008-10-13
I don't use compiled languages (I will soon enough). But I have compiled before, and I as a Python programmer get in the habit of running my program every so often after a change or addition to make sure that it runs well. I do that a lot, so I can't imagine compiling every single time (with a compiled languages), with rather large applications.

---

### Post by MusicMastaMike on 2008-10-13
I definitely prefer scripting languages.  Compiled languages like C and Java require too much work for me, when I can usually do the same amount of work with a scripting language in about 1/4 of the lines.

---

### Post by lisati on 2008-10-13
My preferences fall into the "it depends" categeory. Roughly speaking, they're something along the lines of interpreted for debugging, compiled when it's ready, and scripted when it's a movie  or a TV show.

---

### Post by kknd on 2008-10-13
Depends, but my bigger projects are made using C and Lua.

---

### Post by MusicMastaMike on 2008-10-13
> **kknd said:**
> Depends, but my bigger projects are made using C and Lua.

Hooray for Lua!!

---

### Post by jimi_hendrix on 2008-10-13
> **musicmastamike said:**
> hooray for lua!!

+1

---

### Post by pmasiar on 2008-10-13
> **nvteighen said:**
> Python is also compiled, but the point of being "interpreted", in my honest opinion, is in that you can rely on an interpreter you have user-access to

The concept in play is [http://en.wikipedia.org/wiki/Name_binding](http://en.wikipedia.org/wiki/Name_binding) - Python and Lisp use late (runtime) binding, Java and C use early binding. So all power of the Python language is available at runtime, and it's trivial to put together a string containig valid code, including references to variables, and execute it at runtime - because name is bound to code at runtime. Same with Lisp, and Lisp can be compiled, too. There was also [http://en.wikipedia.org/wiki/Symbolics](http://en.wikipedia.org/wiki/Symbolics) - computer with CPU optimized to execute Lisp.

When we talk about differences between languages, there is whole stack of concepts in play beyond syntax: parsing/compiling (vs. line-by-line parsing), virtual machine, early/late binding, static/dynamic typing, strong/weak typing, etc.

People who know only C, C++ and Java, mistakenly believe that they "know" different languages, even if those three are almost identical.  So Python is strongly, but dynamically typed, with late binding, and compilig code to be executed by virtual machine. If you ask me, Guido found perfect balance between power and flexibility 8-)

---

### Post by Sinkingships7 on 2008-10-13
> **pmasiar said:**
> 
people who know only c, c++ and java, mistakenly believe that they "know" different languages, even if those three are almost identical.  

+1

---

### Post by jimi_hendrix on 2008-10-13
> **pmasiar said:**
> people who know only c, c++ and java, mistakenly believe that they "know" different languages, even if those three are almost identical.

+2

---

### Post by paris_alex on 2008-10-15
definitely scripting if u 1 2 hack things out quickly... ;-) this development style is called 'as long as it works' methodology. LOL!

---

### Post by stevescripts on 2008-10-15
Scripting - for both personal and paywork, whenever possible ;) ...

C when necessary.

My personal language preference should be obvious. :biggrin:

Steve

---

### Post by jimi_hendrix on 2008-10-15
> **stevescripts said:**
> Scripting - for both personal and paywork, whenever possible ;) ...

C when necessary.

My personal language preference should be obvious. :biggrin:

Steve

i noticed you absolutly hate tcl...

---

