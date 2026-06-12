---
title: "Questions about python and Ubuntu :)"
date: 2013-07-08
forum: Programming Talk
---

### Post by gigasea on 2013-07-08
I have a few questions, about Ubuntu and python

1. What parts of Ubuntu are programmed in Python? i know most of it would be written in C(kernel, drivers and low level things) and or C++(GUI?, applications?), but ive noticed that the installer used python scripts to handle parts of the installation process and i have also noticed wubi, which is the windows installer uses python scripts as-well :)
correct me if im wrong :)

2. is it possible to do driver programming in Python with Ubuntu?

3. what are some cool IDES you recommenced

Please note im a newbie at GNU/Linux and Ubuntu in general so no hate alright? i love GNU/Linux because everything works so beautifully and smooth on my intel atom notebook which windowzs runs horrible on lol :)

Thanks
- Gigasea

---

### Post by nvteighen on 2013-07-08
> **gigasea said:**
> I have a few questions, about Ubuntu and python

1. What parts of Ubuntu are programmed in Python? i know most of it would be written in C(kernel, drivers and low level things) and or C++(GUI?, applications?), but ive noticed that the installer used python scripts to handle parts of the installation process and i have also noticed wubi, which is the windows installer uses python scripts as-well :)
correct me if im wrong :)


Well, there are a couple of things that are written in Python: the update-manager, Alacarte, the Bazaar VCS, installation scripts, parts of GIMP, etc. "apt-cache rdepends python" shows a lot of stuff that depends on it; take a look at that list. 

> 
2. is it possible to do driver programming in Python with Ubuntu?


Impossible, regardless of distribution and I'd dare to say no mainstream OS can do that. Python is run on an interpreted shell that is based (and compiled) against the userland C Standard Library. In GNU/Linux the only way to do that is to use something that can be translated into something the kernel can run (ASM, C... not sure about C++: I guess it could be possible, but it isn't done because it's really impractical to do it).

> 
3. what are some cool IDES you recommenced


None. A newbie must know how the tools work and interact with each other in order to understand errors, faulty behavior and also, be able to customize his environment into something that fits his workflow. Also, there are quite a bunch of interesting text editors that have everything you need to do basic development in any language (Geany is a really good one). I myself use Emacs, but I wouldn't recommend it to anyone who's starting to learn how to program.

Also, do not underestimate the power of Python's interactive prompt. It's really good for trying things (or install ipython if you want something a bit more sophisticated).

> 
Please note im a newbie at GNU/Linux and Ubuntu in general so no hate alright? i love GNU/Linux because everything works so beautifully and smooth on my intel atom notebook which windowzs runs horrible on lol :)


Welcome! And don't be ever afraid to ask!

---

### Post by gigasea on 2013-07-08
ah, fair enough, so if i wanted to do driver programming i have to use C or Assembly language? thats cool i know C aswell and i love learning new things about computers, though im guessing that would be a very hard task to? yeah?
never knew the update manager was, thats kinda cool :) probs explains why python comes pre-installed or packaged with ubuntu/ debain based distros
damn, though it would of been cool to do driver programming in python but, hey doesn't really bother me :) 
im guessing if it was possible to do drivers in python it would be very slow yes?
i love python, i don't like vb though ;) i have used it before and dislike it, i love python because its cross platform and requires minor changes for it to run on other operating systems
visual basic though only runs on Microsoft Windows  i have used Geany before and i think its an awesome IDE :) lets yah compile python code too :) into bytecode[COLOR=#000000]
[/COLOR]

---

### Post by MG&amp;TL on 2013-07-08
> ah, fair enough, so if i wanted to do driver programming i have to use C or Assembly language?

Yes. Probably mostly C with a little embedded assembly.

> thats cool i know C aswell and i love learning new things about computers,

Good for you!

> though im guessing that would be a very hard task to? yeah?

Not necessarily. It depends how well you understand hardware and systems programming, and how well you know C. There's some good tutorials around for linux kernel programming.

> damn, though it would of been cool to do driver programming in python but, hey doesn't really bother me :) 

It's not technically impossible. If you were feeling ambitious, you could try writing a module that allowed one to write kernel code in python, probably by embedding an interpreter. That would be *very* tricky to do, however, and I wouldn't recommend doing it, for a variety of reasons

> im guessing if it was possible to do drivers in python it would be very slow yes?

Yes. Python doesn't have anyway near the same performance as C. This doesn't usually matter, but in the kernel it does.

> i love python, i don't like vb though ;) i have used it before and dislike it, 

You might want to check out other languages; there is a wealth of programming languages that are completely different to both python and VB.
> 
i love python because its cross platform and requires minor changes for it to run on other operating systems

See Java, also pretty much every interpreted language ever. If you write a compiled language properly, it's completely possible for it to run on another operating system with only a recompile.

> visual basic though only runs on Microsoft Windows

[Not]("http://gambas.sourceforge.net/en/main.html") [technically true.]("http://www.mono-project.com/VisualBasic.NET_support")

> i have used Geany before and i think its an awesome IDE :) 

Geany is more of a text editor, but has a couple of options for automatically building stuff, so I guess it counts as an IDE.

> lets yah compile python code too :) into bytecode

The python interpreter does that automatically. But if it makes you feel better... ;)

---

### Post by nvteighen on 2013-07-09
> **MG&TL said:**
> 
It's not technically impossible. If you were feeling ambitious, you could try writing a module that allowed one to write kernel code in python, probably by embedding an interpreter. That would be *very* tricky to do, however, and I wouldn't recommend doing it, for a variety of reasons


It's technically impossible if you don't modify the language. Plain vainilla Python wouldn't know anything about memory addresses or embed ASM, even if it ran in kernel space, just because it doesn't have the concept to refer to them. So you would have to create a low-level extension for Python that somehow bypasses the interpreter's restrictions... The whole thing would result in something I wouldn't call that Python any more, but a Python-derivative.

---

### Post by gigasea on 2013-07-09
personally i think it would just be easier to do it in c yeah? writing a module in python for driver programming would be useless and time consuming aye?

---

### Post by kramer65 on 2013-07-09
> **gigasea said:**
> I have a few questions, about Ubuntu and python
3. what are some cool IDES you recommenced


I highly recommend trying [Spyder]("https://code.google.com/p/spyderlib/"). Although it has many many options, I simply use it as a text editor for Python. I really enjoy the highlighting of possible errors, highlighting of equal words/variables in the code and the code completion. Check it out!

---

### Post by gigasea on 2013-07-09
i'll give it a look :) never noticed that in the software center but okay then :)

---

### Post by MG&amp;TL on 2013-07-09
> **nvteighen said:**
> It's technically impossible if you don't modify the language. Plain vainilla Python wouldn't know anything about memory addresses or embed ASM, even if it ran in kernel space, just because it doesn't have the concept to refer to them. So you would have to create a low-level extension for Python that somehow bypasses the interpreter's restrictions... The whole thing would result in something I wouldn't call that Python any more, but a Python-derivative.

Python is a [standard, not an implementation. ]("http://docs.python.org/2/reference/introduction.html#alternate-implementations")Therefore I presume (although I defer to evidence) you can do something internally to allow a default built-in module to allow that kind of thing anyway; something like the existing *__builtins__*.

> **gigasea said:**
> personally i think it would just be easier to do it in c yeah? writing a module in python for driver programming would be useless and time consuming aye?

Yes, it would be almost infinitely easier to do it in C. It was an academic argument I shouldn't have voiced, apologies for any confusion.

---

### Post by nvteighen on 2013-07-09
> **MG&TL said:**
> Python is a [standard, not an implementation. ]("http://docs.python.org/2/reference/introduction.html#alternate-implementations")Therefore I presume (although I defer to evidence) you can do something internally to allow a default built-in module to allow that kind of thing anyway; something like the existing *__builtins__*.

There's a huge difference between Jython, IronPython et al. and our hypothetical kernel space Python. Jython et al. are still running on a high-level space, where the only change from the user's point of view is that you get ways to interface with Java, .NET, etc. natively, but the language is still Python. Those are extensions of Python that adapt the language to a platform different to CPython.

I may be missing a point or two, but in my opinion, our kernel space Python would require a huge amount of modifications that would result in a quite different language with a different programming philosophy. I think you would need to make Python aware of stuff like byte alignment, pointers, embedded ASM, etc. This stuff interacts very badly with the current state of affairs in Python: ASM would require static compilation, pointers would require new syntax and possibly some sort of static typing that could be used to **any** type (in order to declare pointers and not regular reference to an object, for example), you'll need to have some way to control byte alignment in your classes (more new syntax so that the old one is not modified), add ways to manually optimize your code (tweak the interpreter's behavior when compiling)... My impression is that you'd get a convoluted language that mixes levels of abstraction by adding stuff to a simpler previous one (a mess à la C++).

All of this has nothing to do with the implementation, but with the nature of low-level programming. Jython et al. are like adapting the current CPython interpreter to have native access to the kernel API or be run as a kernel module, but leaving the language in a high-level of abstraction (e.g. something like a kernel-space scripting language). We're talking about having Python act like C in kernel space so that you may write a kernel module in any of both languages.

---

### Post by MG&amp;TL on 2013-07-10
> There's a huge difference between Jython, IronPython et al. and our hypothetical kernel space Python. Jython et al. are still running on a high-level space, where the only change from the user's point of view is that you get ways to interface with Java, .NET, etc. natively, but the language is still Python. Those are extensions of Python that adapt the language to a platform different to CPython.


Yep, I understand this.

> I may be missing a point or two, but in my opinion, our kernel space Python would require a huge amount of modifications that would result in a quite different language with a different programming philosophy.

Not necessarily; as long as the runtime is implemented, the actual program logic and grammar would still work the same as far as I know.

 > I think you would need to make Python aware of stuff like byte alignment, pointers, embedded ASM, etc. This stuff interacts very badly with the current state of affairs in Python: ASM would require static compilation, pointers would require new syntax and possibly some sort of static typing that could be used to **any** type (in order to declare pointers and not regular reference to an object, for example), you'll need to have some way to control byte alignment in your classes (more new syntax so that the old one is not modified), add ways to manually optimize your code (tweak the interpreter's behavior when compiling)...

Most of this (with the exception of inline ASM (JIT?)), could be implemented with a separate C library that python can interface with; no modification to the actual syntax.

> My impression is that you'd get a convoluted language that mixes levels of abstraction by adding stuff to a simpler previous one (a mess à la C++).


That's my impression too; I'm not saying it was a good idea, merely that it wasn't impossible.

> All of this has nothing to do with the implementation, but with the nature of low-level programming. Jython et al. are like adapting the current CPython interpreter to have native access to the kernel API or be run as a kernel module, but leaving the language in a high-level of abstraction (e.g. something like a kernel-space scripting language). We're talking about having Python act like C in kernel space so that you may write a kernel module in any of both languages.


I was thinking of it as a kernel-space scripting language (I believe this has been done before; a Forth interpreter, I believe). With suitable libraries and hardware access, I imagine there would be no limit to what it *could* do in kernel-space, only to what you would *want* it to do.

---

