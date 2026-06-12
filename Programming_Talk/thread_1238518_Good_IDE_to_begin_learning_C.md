---
title: "Good IDE to begin learning C"
date: 2009-08-12
forum: Programming Talk
---

### Post by jac0117 on 2009-08-12
I'm about to start learning C. I've only programmed in Java in the past and use Eclipse.

What would you guys recommend for an IDE to start learning C?

---

### Post by Mad Hacker on 2009-08-12
[http://projects.gnome.org/anjuta/index.shtml](http://projects.gnome.org/anjuta/index.shtml)
[http://www.geany.org/](http://www.geany.org/)
[http://www.codeblocks.org/](http://www.codeblocks.org/)

---

### Post by nvteighen on 2009-08-12
None... :p

Use an editor and learn how to compile at hand... and also, Makefiles. otherwise, when your IDE fails, you won't be able to fix it (and from the ratio of "<some IDE> doesn't compile" threads, that seems to happen a lot). Learning C or C++ implies learning the compilation process, as it defines how some stuff will behaive on your code (specially in C).

---

### Post by Can+~ on 2009-08-12
Geany is pretty straightforward. Click compile, then run and that would be it.

My stand on "how-to-learn C" goes like:

[list=1]
[*]Learn basic C with a totally straightforward IDE.
[*]Once basic C is learnt (there isn't much depth, really) learn how to compile by hand, and crate makefiles.
[*]That being covered, either use a big IDE (Eclipse, Netbeans) or single-editting tools (Vim, Emacs, even geany)
[*]Increase your C knowledge with other things (Function pointers, casting into other types, etc)
[/list]

The reason behind learning how to compile "by hand" before using a big IDE is that, it usually requires knowledge on how linking and compiling works before starting to code big projects. 

(Weird.. I suddenly have 5 cups of coffee?)

---

### Post by phrostbyte on 2009-08-12
[URL="apt://geany"]Geany
[/URL]

It's simple and effective.

And I second learning how to use a Makefile. It's very easy.

That way when you compile you can just type "make" instead of gcc + bunch of crazy parameters. Geany has a button that auto make and runs your project. It also makes compiles faster.

---

### Post by msvolenski on 2009-08-13
I have installed NetBeans IDE 6.7.1 yesterday, I'm starting on learning C++.
What do you think about this IDE? It's good? Should I change to one of these you listed?

Thanks in advance!

---

### Post by Mirge on 2009-08-13
If you like it, use it.

---

### Post by zipperback on 2009-08-13
Nano or VIM work really well for writing code actually.

If you want something that is more GUI then just click:
Applications -> Accessories -> Text Editor

That will launch Gedit for you.

It supports formatting for numerous programming languages.
See the attached image.

You don't need a fancy IDE to write good code, however as everyone has different tastes as to what they like in an editor, my suggestion it to try different ones out until you find one that works best for you, and then go for it. 

- zipperback
:popcorn:

---

### Post by Krupski on 2009-08-13
> **jac0117 said:**
> I'm about to start learning C. I've only programmed in Java in the past and use Eclipse.

What would you guys recommend for an IDE to start learning C?

I am not a "programmer" and I'm certainly no expert, but I have found that using a simple text editor (nano) to write code and then just command line compiling it works best for me.

I write little utilities... usually only a few pages of source and 10K or so of executable. Really tiny stuff!  :)

The only "automation" I use is a small script to call the compiler so that I don't have to type all the option switches over and over again.

Hope this helps.

-- Roger

---

### Post by msvolenski on 2009-08-13
Well, zipperback, you  convinced me!

> **zipperback said:**
> Nano or VIM work really well for writing code actually.

If you want something that is more GUI then just click:
Applications -> Accessories -> Text Editor

That will launch Gedit for you.

It supports formatting for numerous programming languages.
See the attached image.

I opened the "HelloWorld.cpp" at Gedit and it was good to see, maybe later I'll catch an IDE to use, but now I liked this simple way. I think I'll try Nano and Vim, like you said, at least to see how they looks like.

Thank you for help me!

---

### Post by Sockerdrickan on 2009-08-13
+1 gedit

---

### Post by nvteighen on 2009-08-13
+1 Gedit

It's annoying how people seem to underestimate it... ok, it's not Emacs or Vim, but for one's programming first steps is just what you need... Check out the plugins!

---

### Post by msvolenski on 2009-08-13
I think it's really simple to use Gedit, I'm sure it's all I need, at least for now.

But, I took a look at Vim on the web, it seems to be a little complicated, it has a lot of shortcuts to edit the document. Why Vim is better?

---

### Post by Cyanidepoison on 2009-08-13
Vim is powerful because of all those complicated options.

When you save a file and quit Vim, you use the command ":wq<Enter>", where <Enter> is your enter or return key.  W stands for write, q stands for quit.  Things like that happen all over Vim, you combine multiple commands and options together.  

You also never have to use your mouse or arrow keys to navigate a document.  Your hands should almost never have to leave the home row on your keyboard when you navigate.  Everything is just right there.

---

### Post by colau on 2009-08-17
Netbeans 6.7

---

