---
title: "Genie is not Python but is very close to it and the best way to write apps."
date: 2010-04-04
forum: Programming Talk
---

### Post by michaelmartin007 on 2010-04-04
I have writen and idea in Brainstorm.

[http://brainstorm.ubuntu.com/idea/24110/](http://brainstorm.ubuntu.com/idea/24110/)

You know about Acire, this is an app that run and show python snippets. I find it great and very useful for learning pygtk, pygobject, pycairo...

The idea I wrote is to add genie snippets to acire. If you can, please, enter in brainstorm and vote for the idea. I think that genie and vala are goods programming languages for the future of gnome, both perform as gtk or qt.

Genie is a programming language that make you think that you are coding python but no. Genie is compiled to C and then to binary and perform as good as C.

[http://live.gnome.org/Genie](http://live.gnome.org/Genie)

All of you know how python has a strong community behind it. You can imaging Genie as a dialect (I know it isn't). I thing if you know only python, then, learning pygtk or genie take more o less the same time. Genie perform as vala and both as gtk.

---

### Post by nvteighen on 2010-04-04
*sigh* another OOP imperative-based programming language that doesn't bring anything really new; it looks almost like Javascript with indentation instead of braces and native compilation... the issue is that code written in a dynamic language that's afterwards natively compiled either is very slow even slower than interpreting it or compiles into very big executables because of embedding the interpreter.

I'd like to know what this language defines as different to Python. Python did a really good job becoming a language on its own and with its own particular characteristics, even though it isn't that new and original either.

I'd really like to see new languages that actually bring in totally new challenging concepts.

---

### Post by km0r3 on 2010-04-04
I think Acire should have solely Python snippets. Why don't put some Java, C++, [X] snippets, too? I don't like that idea.

Now, you could write something similar to Acire for Genie. I would like to see that :) , but let Acire do one thing, and do it well.

So, not meaning to be rude, I think this not a good idea, though I'll listen to the others' opinions.

---

### Post by wmcbrine on 2010-04-04
> **michaelmartin007 said:**
> [http://live.gnome.org/Genie](http://live.gnome.org/Genie)I haven't used Genie, but based on what I just read at that site, it seems only very superficially similar to Python. Far from a dialect. Another no vote from me.

---

### Post by CptPicard on 2010-04-04
> **nvteighen said:**
> 
I'd really like to see new languages that actually bring in totally new challenging concepts.

Unfortunately, I don't think you'll get to see a language like that after Lisp, because by then you're already exposed to most everything that is important, doable and general enough to be in a language, even in higher level languages... I guess the only thing that one may see that is new in the future are integrated concurrency primitives; think Google go's channels. But even those are barely just syntactic sugar for thread-run functions and blocking queues or other messaging systems. Essentially "library calls", not core language operations.

---

### Post by nvteighen on 2010-04-05
> **CptPicard said:**
> Unfortunately, I don't think you'll get to see a language like that after Lisp, because by then you're already exposed to most everything that is important, doable and general enough to be in a language, even in higher level languages... I guess the only thing that one may see that is new in the future are integrated concurrency primitives; think Google go's channels. But even those are barely just syntactic sugar for thread-run functions and blocking queues or other messaging systems. Essentially "library calls", not core language operations.

:(

---

### Post by Wybiral on 2010-04-05
> **wmcbrine said:**
> I haven't used Genie, but based on what I just read at that site, it seems only very superficially similar to Python. Far from a dialect. Another no vote from me.

I agree. Pythons strength isn't in the use of whitespace... It's in the libraries and the dynamicness.

---

### Post by pabstsmear on 2010-09-27
I personally think genie is pretty cool.  I wish it had better documentation.  Its also got some clear syntax differences to python, but I think it would get easier over time.  I personally can't jump into it without the libraries that make it possible to do most of what I would use it for.  I think its very promising, but not quite mature.

---

### Post by thirdspace on 2011-03-29
I looked at Genie. It is best understood as an alternative, less verbose input syntax for the Vala compiler. It looks a little like Python, sort of the way C# looks a little like Objective-C. It is a nice idea, but it seems like the language is failing to catch on, probably because the documentation is very bad. Perhaps also because Python is not really as slow and bloated as some people say it is -- at least, not in a way that matters to most people.

---

### Post by juancarlospaco on 2011-03-30
You can compile python to binary too...

---

### Post by Queue29 on 2011-03-30
> **juancarlospaco said:**
> You can compile python to binary too...

In fact, there's a GSOC project to bring a python compiler to the GCC.

[http://gcc.gnu.org/wiki/PythonFrontEnd](http://gcc.gnu.org/wiki/PythonFrontEnd)

---

### Post by MadCow108 on 2011-03-30
> **Queue29 said:**
> In fact, there's a GSOC project to bring a python compiler to the GCC.

[http://gcc.gnu.org/wiki/PythonFrontEnd](http://gcc.gnu.org/wiki/PythonFrontEnd)

urgh adding python to gcc, that can not end well ^^
compiling with the far more modern llvm already ended due to lack of interest and success (unladen swallow project).
doing the same in the outdated codebase of gcc just smells waste of time.

projects like pypy will probably be far more useful.

---

### Post by slavik on 2011-03-30
> **Wybiral said:**
> I agree. Pythons strength isn't in the use of whitespace... It's in the libraries and the dynamicness.
You mean the areas where Perl beats it? :P

---

