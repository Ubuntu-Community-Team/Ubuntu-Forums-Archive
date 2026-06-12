---
title: "programming"
date: 2011-03-04
forum: Programming Talk
---

### Post by pyrofreak99 on 2011-03-04
i have been wanting to get started in programming in linux but im not sure where exactly what program to start in, i was kinda looking for something like visual basic. i was wanting to start out coding my own web browser then going on to making my own linux distro.

---

### Post by mmsmc on 2011-03-04
that will take alot of work, ubuntu is written in C, thats a good language to start in, you should also learn java, it is used in basically every computer program. programming a distro will consist of whatever language you feel comfortable with.

---

### Post by lisati on 2011-03-04
*Thread moved to **Programming Talk**.*

---

### Post by Locke_99GS on 2011-03-04
Two quick things to note: 
1. Web Browsers can get very complicated, very quickly. Look at the size of the WebKit and Gecko projects, and these are just the engines. Now, using one of these engines in a driver application you create would be relatively easy.

2. Typically, no programming skills are required to create a linux distro. Most distro's are just different default packages or preconfiguration. Sometiems, the distro author does program something used in his distro to set it apart (such as the mintMenu and mintUploader in Linux Mint) but doing so is not required.


For programming in Linux, first you decide what language you will program in. If you don't currently know any programming languages, the most common language is C/C++ and I would personally suggest learning it. Not only is it everywhere and useful to know, by its very archaic and abstract nature you will learn a lot about how computer programs actually work. For a high level language, it is very low level. After becoming adept in one language, other languages can be learned very rapidly.

The IDE you choose is mostly personal opinion. Some of the more popular ones are:
Code::Blocks
Anjuta
NetBeans
Geany
Eclipse
MonoDevelop

I use MonoDevlop, personally. It is a great IDE, and supports the few languages I care about. Some people will throw a hissy fit at the mention of Mono, though, so familiarize yourself with the "issue".

Many IDE's will work with multiple languages, including VB, and you don't even need an IDE to write programs. Using your favourite text editor will work just as well, though you'll miss out on a lot of useful bells and whistles.



With all of that in mind, what EXACTLY are you asking?

---

### Post by matthew.ball on 2011-03-04
> **mmsmc said:**
> that will take alot of work, ubuntu is written in C, thats a good language to start in, you should also learn java, it is used in basically every computer program. programming a distro will consist of whatever language you feel comfortable with.
There are plenty of applications written without a hint of Java.

---

### Post by robsoles on 2011-03-05
> **matthew.ball said:**
> there are plenty of applications written without a hint of java.

+20.

---

### Post by foxmuldr on 2011-03-05
> **pyrofreak99 said:**
> i have been wanting to get started in programming in linux but im not sure where exactly what program to start in, i was kinda looking for something like visual basic. i was wanting to start out coding my own web browser then going on to making my own linux distro.

Reads like:
Hi, I have been wanting to get started in the manufacturing industry but I'm not sure where exactly what venue to start in, I was kinda looking for something to do with rolled sheets of steel and mechanical presses. I was wanting to start out doing high-end designer body panels then going on to creating my own car company and making exotic sports cars.

One must learn the fundamentals before moving any further.  As another poster said, go with C and Java. With a base knowledge of C, you'll get into C++, Objective-C, even C# and Java relatively easily, as they are all fairly similar.

C and C++ are used as often as they are to this day for a reason: they do a lot of programming things really well.

- Rick C. Hodgin

---

### Post by slooksterpsv on 2011-03-05
I'd say to learn essentials and get the hang of programming, try Python, it's cross-platform, easy to learn, and helps you to learn other languages as you would have an understanding of how programming works.

There's lots of tutorials out there on the Internet. With Python, where it's easy, it is extensible to be able to create GUI programs (with buttons and graphics) via Qt, GTK+, WX, etc.

---

### Post by nvteighen on 2011-03-05
And again, for the millionth time: someone wants to be a programmer, has a project in mind knowing very little about what it takes, but doesn't know where to start. And the Python or C (or C++) flamewar begins immediately with funny, misleading arguments in favor of any of both.

Programming is about solving computable problems and the means to that is to use a language suitable for programming... but it's the means. Ok, in theory and also in practice, you can learn programming with C, C++, Python or whatever other language. The issue here is a paedagogical one.

C is very "near to the computer" (technically called a "low-level language"), meaning that it makes you think and write stuff thinking on how the computer is implemented. It's not about quantity of features, but about the kind of concepts you are expected to deal with: data sizes, memory management, stack overflows, struct alignement, etc. But these concepts aren't really programming concepts because they don't appear in high-level programming languages (and when they do, it's a bug in the implementation), only just in low-level programming, which is a subset of programming.

So, if you choose a low-level programming language as your first language, you'll be learning general programming concepts along with a lot of concepts specific only to low-level programming.

Python isn't a panacea; it has its quirks and I honestly like it less as time passes. But it's a high-level language, meaning that its concepts depend much less on computer-specific issues and are nearer towards general formal logical concepts. Of course, this means the computer has to automate a lot of things and therefore, you lose control and runtime speed, but those are factors that are important just in resource-consuming projects (games, number crunching) or low-level system programming. There aren't concepts specific only to high-level programming: every concept present in high-level programming can be implemented and used in low-level programming but the opposite isn't true. And this is because high-level programming is actually just that general part of programming, valid in any kind of programming per definition. There will be a couple of Python-specific issues you may have to learn.

It's not about learning the "easier" (high-level) or the "harder" (low-level) first. It's about whether learning the "general" vs. the "particular" first. Obviously, if you're seriously into this, you have to learn C. Low-level being a subset doesn't mean it isn't an important subset!

So, choose your poison.

---

### Post by pyrofreak99 on 2011-03-05
thanks guys, sorry i wasnt very specific in what i was asking. mainly what i was asking was if there was a program in ubuntu that is similar to visual basic  and one of the users answered that without being a smartass. thanks guys for your help :)

---

### Post by directhex on 2011-03-05
> **pyrofreak99 said:**
> mainly what i was asking was if there was a program in ubuntu that is similar to visual basic

You mean you want something with a GUI designer?

Here are a few options:

Gambas: integrated IDE with its own VB-like language. Not used for any serious projects AFAIK

Qt-Designer + language of choice (C++ focus): Designer for Qt applications. Qt is a major GUI framework, and used for KDE. Whilst a few languages can be used with Qt, the standard is C++ and tutorials will reflect that.

Glade + language of choice (C & Python focus): Glade is a GUI designer for the GTK framework, as used by GNOME. You can design a GUI with Glade, then use it in several languages (definitely not limited to those I've mentioned, but most tutorials will use those)

MonoDevelop + C#: MonoDevelop is an IDE with an integrated GUI designer - but the designer can only emit C# code.

---

### Post by shawnhcorey on 2011-03-05
If you don't know anything about programming, then you are better off learning the basics with one of the scripting languages:  Perl, Python, Ruby or PHP.  They all have great on-line resources and tutorials for free.  If you can afford it, they all have great courses and books to help you along.

---

