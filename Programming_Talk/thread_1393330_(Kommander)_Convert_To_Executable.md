---
title: "(Kommander) Convert To Executable"
date: 2010-01-29
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-01-29
What's Up?

OK, So I'm about 98% new to Kommander, Where new to it yesterday but I've learnt a bit since then so I'm only 98% new to it now, :p Anyway, The thing that I'm making is some software, And of course I don't want them having to download Kommander and run it that way, Is it possible to convert it to an binary executable?

Thanks Bye.

---

### Post by nvteighen on 2010-01-29
> **Chamillionaire2 said:**
> What's Up?

OK, So I'm about 98% new to Kommander, Where new to it yesterday but I've learnt a bit since then so I'm only 98% new to it now, :p Anyway, The thing that I'm making is some software, And of course I don't want them having to download Kommander and run it that way, Is it possible to convert it to an binary executable?

Thanks Bye.

Depends on what language you're coding in... probably Kommander is already creating the executable for you if it's a compiled language.

---

### Post by Chamillionaire2 on 2010-01-29
> Depends on what language you're coding in... probably Kommander is already creating the executable for you if it's a compiled language.
It's saving it into a project file (.kmdr) Which you can easily open with text editor.

---

### Post by Chamillionaire2 on 2010-01-29
Bumpers! Come on you know you want to help me, Dont be shy :-)

---

### Post by nvteighen on 2010-01-30
This is the issue with IDEs; they just confuse beginners with intermediate steps like "project files" that are only useful to people that know how to take advantage of that if needed.

I want to know what programming language you're using. Could you please post your code? (please, use the [ CODE] [ /CODE] tags... without spaces).

But anyway, what you need for programming is just a text editor and the compiler or interpreter for the language you're using. I'm not sure what you've got in KDE and whether Kate is useful for this, but in GNOME Gedit or Geany are good options for beginners. Or you could try using Emacs or vi... but that could be even more confusing.

---

### Post by nvteighen on 2010-01-30
**Answering a PM from the OP**

[QUOTE=Chamillionaire2]What's Up?

Thanks for helping, The language of the .kmdr file is xml.[u]
[http://pastebin.com/m3c1e6b27](http://pastebin.com/m3c1e6b27)[/u]

Thanks Bye.[/QUOTE]

Ok, sorry to disappoint you but you haven't written any program. That's just a GUI but won't work because there's no actual working code in it.

You better refer to the Programming Talk's stickies to get plenty of resources about how to start programming. Anyway, I'll tell you it approximately goes.

You write code in a text file; you can do it in any text editor, but of course there are specialized ones that make it easier. The code is just an ASCII plain text file written in a programming language... but understand that "programming languages" are more a human thing, a convention on how we decide to express some knowledge in a formal-logical language that, with the aid of some computer programs, we can turn into something a computer can understand and run for us.

Then, it depends on the language. There are several classifications according to different aspects of programming, but I'll focus on compiled vs. interpreted. Compiled languages need a compiler, which takes the source code files and translate them into a native machine-readable file... The most important ones are C and C++. The Linux kernel and GNOME's core are written in C. KDE and Firefox are written in C++. There are other ones, less popular, like Objective-C, which is what Apple uses. Interpreted languages, instead, need an intermediate program to run the code. Examples are Java, Javascript, Perl, Python, Lisp, C#, etc. This means that to run your program, you'll need to run it from the interpreter.

The details are a bit more complex than how I'm presenting them here. For example, Python and Java are somehow a compiled/interpreted hybrid. The main idea is that you use compiled languages like C and C++ for system programming or stuff that needs to have access to the most internal (and frustrating) details of a computer, while interpreted ones are usually designed for hiding those details you don't need.

In my opinion, the best is to start with Python, as it is a quite flexible and amazingly easy platform. But again, the stickies will help you... and all of us, of course :D

---

### Post by Chamillionaire2 on 2010-01-30
So your saying I need to compile the file? I tried to compile it into C ```
gcc -o file name.kmdr
```

```
/usr/bin/ld:name.kmdr: file format not recognized; treating as linker script
/usr/bin/ld:name.kmdr:1: syntax error
collect2: ld returned 1 exit status

```

---

### Post by Some Penguin on 2010-01-31
No, they're saying that if you expect to be able to produce an executable, you should write an actual program in an actual language that works with a compiler.  Why would you expect a file written specifically for 'Kommander' to be useful for as an entirely different purpose and language?

---

### Post by Chamillionaire2 on 2010-01-31
> **Some Penguin said:**
> No, they're saying that if you expect to be able to produce an executable, you should write an actual program in an actual language that works with a compiler.  Why would you expect a file written specifically for 'Kommander' to be useful for as an entirely different purpose and language?

So I have to learn a new language and write the entire script all over again, What a Bitch! I think I'm going to do it In VB, Would I  be able to convert that script into a binary executable?

---

### Post by Hellkeepa on 2010-01-31
HELLo!

Not on anything but Windows, no. VB is MS only, after all.
You've been recommended to have a look at Python above, which is probably the simplest language that'll allow you to do what you want.

Happy codin'!

---

