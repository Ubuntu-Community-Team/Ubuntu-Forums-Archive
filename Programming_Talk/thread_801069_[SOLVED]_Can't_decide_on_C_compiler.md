---
title: "[SOLVED] Can't decide on C compiler"
date: 2008-05-20
forum: Programming Talk
---

### Post by lrx on 2008-05-20
Hi,
I am new to Ubuntu and want to learn C.

I have installed Anjuta and the necessary libraries except 'glib'. I can't find it on synaptic but have a ftp address. How do I install glib form the ftp address?

What is the most basic way to create c programs (for example gedit)?

Finally, what do I need to use python for creating c program?

Any help will be appreciated.

Thanks

---

### Post by Zugzwang on 2008-05-20
Please see the Stickies, they will guide you through compiling your first C program *and* installing the necessary prerequisites.

EDIT: Oh, by the way, Python is a different programming language, so you can't use Python to create C programs. However, what you can do is to write some parts of your code in C, and some parts in Python. There are ways to let them interact.

---

### Post by lrx on 2008-05-20
Ok, thanks for clearing that issue

---

### Post by stevescripts on 2008-05-20
Also, don't confuse IDE's with compilers ... ;)

Steve
(who suggests starting by writing your code in gedit, and building on the commandline)

---

### Post by lrx on 2008-05-20
Thanks, that make more sense now.

---

### Post by Can+~ on 2008-05-20
Anjuta is not a C compiler.

GCC is a C compiler (GNU C Compiler), Anjuta (or any development enviroment) just calls the compiler. In essence, you could write a source file just with gedit (the default notepad), and compiling via the shell:

```
gcc source.c -o executable
```

And python is a different language, with it's own interpreter.

I now most people confuse both the IDE with the compiler when just starting. Most people who move from Devcpp on windows, think that the IDE is the only one that can compile the file.

Writing a C file is just writing any other text file, only that you follow certain pattern that the compiler can read, so you just hand your C file to the compiler, he reads it, and makes a binary executable file. On the other hand, python is interpreted, meaning that it runs as it reads.

---

### Post by rye_ on 2008-05-20
steve's suggestion on using a text editor and the commandline seams pretty sensible to me.  It's about 3 years since I first dabbled in c/c++ and I think I wasted as much time learning about the IDE as I spent learning/ experimenting with c.  Learning c was very useful as a learning experience as to some of the issues that a programmer is faced with.

Also, I was under the impression for a while that compiled languages were "real", and python etc were toys.  Doing things in c is not quick and easy and for my uses (creating quick solutions to problems, graphing data, file management etc) absolutely useless.  A scripting language (python, ruby, perl) however is excellent for everyday stuff, so after you've learned the basics of c, maybe a dabble in a scripting language is not too bad an idea, depending on your ultimate aim?

Ryan

---

### Post by lrx on 2008-05-20
Thanks guys,
python seems as the best option at the moment.

O and thanks for the gcc code. I will definitely try that out.

---

### Post by stevescripts on 2008-05-20
One last quickie - see my post in this thread:

[http://ubuntuforums.org/showthread.php?t=704404]("http://ubuntuforums.org/showthread.php?t=704404")

This should compile and run at this point.

Steve

---

### Post by lrx on 2008-05-21
Thanks Steve, had some trouble executing it last nite but nou it works perfectly.
Exactly what I needed.

---

