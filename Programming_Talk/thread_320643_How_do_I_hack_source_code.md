---
title: "How do I hack source code?"
date: 2006-12-17
forum: Programming Talk
---

### Post by geek_Man on 2006-12-17
Okay, so let's say I want to go program hacking (don't worry, on my computer ;) ). How would I edit the source code to the program I feel like tweaking? Or would I have to download new source code and edit that before I compiled it?

---

### Post by Wybiral on 2006-12-17
Well, you have to specify which language it was written in. If it is open source, you don't have to do anything... If it is compiled, you will either need a disassembler/decompiler or a hex editor... And I warn you, it will NOT be pretty and it will NOT be the exact source code. One way to get a hex dump of a program is with objdump, try this in the command line...

```

objdump py2d.so -s

```

The lowercase s will give you all of the hex bytes in the file. Not a whole lot of help unless you understand the working and structure of the program to begin with. You can also view the ASM representation of the file, but this isn't spot-on and will not be very pretty...

```

objdump py2d.so -S

```

The capital S is for the assembly dump.

Unfortunately, there aren't disassembly programs that can completely recover the source, so you can really only use this to find small routines, and even then they have been optimized by the compiler and wont be much help.

But, if you're luck your program will be in python or something, or it will be open source. Otherwise, you'd be better off rewriting the program to suite your needs!

Oh yeah, if you need a good hex editor, GHex is for gnome and it works great! Open up the program with GHex and see if anything looks familiar, depending on what you want to change, this can often be an easy way to do so. Be careful though, you are messing with the machine code of the program!

---

### Post by geek_Man on 2006-12-17
It would be Open Source. I wouldn't bother with compiled stuff (sorry, I guess you don't compile Open Source programs).

---

### Post by engla on 2006-12-17
you can get the source of any package in the repositories (except the non-free ones!) with "apt-get source packagename"

(you have to have enabled source repositories though, that's the deb-src lines in the config file. But you can also use the Software Properties/Repositories preferences to change this)

---

### Post by Wybiral on 2006-12-17
Oh, well if it's open source, just download the source, learn the programming language it's in, learn how to compile it... Then change away!

---

### Post by geek_Man on 2006-12-17
Oh, so you *do* compile it... right?

---

### Post by 23meg on 2006-12-17
If it's written in a compiled language, of course.

---

### Post by geek_Man on 2006-12-17
So what about programs written in Python?

---

### Post by pmasiar on 2006-12-17
> **geek_Man said:**
> Okay, so let's say I want to go program hacking

[Hacker]("http://en.wikipedia.org/wiki/Hacker") is  firstly a competent programmer (before clueless journalists added hype to sell books) who deeply understands his system and is able to quickly solve hard problems, often in area of computer security. To become competent programmer, you will need to learn couple of languages, used in system and applications you plan to use. Hackers are also able to learn quick and don't ask stupid questions (because google, mailing lists and wikipedia have most of answers).

From what you said it looks like you have some learning to do before you become expert programmer. Warning: it is not easy, may take you 10 years - but it is very satisfying and a lot of fun.

Best start will be to figure out which area is most interesting to you, so you are willing to put lots of hours to learn everything there is to know about it (to become expert "hacker"). And you will need to learn couple languages anyway. 

Good first language to learn (by opinion of many but not all) is python. You will need to learn bash shell. Kernel and drivers are in C. Most GUI apps are in C++. Java is universe by itself - mostly for "enterprise level" apps, whatever it is :-), Ruby and PHP are popular for web apps (python, java and perl too). Many people store data in databases, and SQL comes also in couple flavors and database engines. 

You can look up couple of threads in last week with discussions of merits of different languages. I did not added links - as a future hacker, you can find it by yourself. :-) Wikipedia and C2.com is packed with good information.

So, welcome, learn more and have fun!

---

### Post by Wybiral on 2006-12-17
No, unless they use a lot of compiled modules, then you do not have to compile python source.

---

### Post by 23meg on 2006-12-17
You just run them after modifying the .py file. Python is an interpreted language.

---

### Post by geek_Man on 2006-12-17
I think I know what "hacker" means, thank you very much. I'm a perfectly competent programmer too, just green, that's all.

---

### Post by pmasiar on 2006-12-17
> **geek_Man said:**
> So what about programs written in Python?

You can start using first draft beta version of ...

(background music introducing learnPYdia coming to the center of the stage)

[http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/) :-P

While you will be reading "how to start", I will add more content.

---

### Post by geek_Man on 2006-12-17
> **23meg said:**
> You just run them after modifying the .py file. Python is an interpreted language.

Okay, that answers my question.

I'm learning Perl right now and I've been looking around and it seems that Python is pretty snazzy. What are some features in Python that would be useful (for anything)?

---

### Post by Wybiral on 2006-12-17
Python really is a beautiful language... Some of the features I like about it are:

[LIST]
[*]Dynamic variable allocation, you don't need to declare any variables.
[*]List's... I love list's. Dynamically sizable and typed arrays, very useful
[*]Nice format, very readable
[*]You can write your own modules for it using C/C++
[*]Classes and operator overloads
[*]Dictionaries are a very handy object to use (they are a python object, not REAL dictionaries)
[*]I've speed tested programs next to C++, and a number of times it was almost equal
[/LIST]

And those are just some of the things I could think of...

---

### Post by geek_Man on 2006-12-17
Does it have suppot for GUI?

---

### Post by Tomosaur on 2006-12-17
Yes, it does, once you install one of the GUI toolkits :)

---

### Post by geek_Man on 2006-12-17
That's neat. Where would I find a Python repository?

---

### Post by Wybiral on 2006-12-17
Well, python should be installed in ubuntu. And I believe tKinter comes pre installed with python (it is a GUI toolkit). So, go look for a tkinter example and try it out. Just save it as a .py and run it from the command line with "python myprogram.py"

---

