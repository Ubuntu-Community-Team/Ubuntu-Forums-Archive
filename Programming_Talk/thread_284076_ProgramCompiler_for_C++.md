---
title: "Program/Compiler for C++"
date: 2006-10-25
forum: Programming Talk
---

### Post by Sarah13 on 2006-10-25
Hello, this is my first programming related post. I just made the big switch over to Ubuntu, and I'm wondering about what the most highly recommended program/compiler is for Visual C++. I'm just learning C++, and before now I have been using MS Visual Studio 2005 and was wondering about a Linux replacement for that program.

Microsoft being Microsoft, if I make a solution/program file in Linux, can I save it in the correct format so that it will be the same as one created in Visual Studio?

Thanks.

---

### Post by po0f on 2006-10-25
Sarah13,

You will at least need build-essential.  Install it via Synaptic/aptitude.  As for an IDE (which is what Visual Studio is), I myself haven't used Visual Studio, but a couple that come to mind are: KDevelop (for KDE), Anjuta (for GNOME), and [Code::Blocks](http://www.codeblocks.org/) (which is cross-platform).  I've only used C::B on Linux, but you could try it out on Windows to get used to it, convert your projets over to it, and then use it on Linux.

If you do go the C::B route, use one of the nightly builds, as the 1.0RC2 release is broken.

---

### Post by UpsideDownFace on 2006-10-25
If you want to learn C seriously, then buy "The C Programming Language" by B.W.Kernigan and D.M.Ritchie and work through some of the examples.
Use the Terminal; mkdir programs; cd programs; type in the code for hello.c; gcc hello.c -o hello; ./hello will give "Hello, World"

---

### Post by UpsideDownFace on 2006-10-25
Sorry I replied about C, for C++ it should be "The C++ Programming Language" by Bjarne Stroustrup; and "g++ hello.cpp -o hello"

---

### Post by darth_vector on 2006-10-26
I agree, an IDE is not the way to go if you really want to learn a language. IDE's tend to hide things from you. The tools provided in build-essential, namely **make** and **gcc** should be more than sufficient for your needs.

the stroustrup book is a great reference, but keep in mind that the guy is a programmer, not a writter. there are some laughs to be had with his grammar and spelling... and mine for that matter.

as a text editor i would recommend vim :d

---

### Post by amo-ej1 on 2006-10-26
in my time i learned to fiddle around with 'practical c++ programming' which covers the environment great but isn't that strong when it comes to STL and such.

But when learning, you will create small applications which you can write in any tekst editor. When you applications grow larger, you should migrate to some tool that can easily work with a lot of files, and things like kdevelop, anjuta, eclipse & cdt, code::blocks become handy ... (no real order there). 

The only thing that isn't mature is code completion, but code completion isn't a real requirement .... it shouldn't be anyhow ;)

---

