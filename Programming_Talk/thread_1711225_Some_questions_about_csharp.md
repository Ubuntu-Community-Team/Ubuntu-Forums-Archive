---
title: "Some questions about csharp"
date: 2011-03-21
forum: Programming Talk
---

### Post by robro on 2011-03-21
Hello community,
I am in the middle of learning Python and C++, and am looking into csharp and I have some questions about it:

1. I have heard its it's especially good at creating gui's, is this true?

2. It was originally created for windows, how compatible is it with Ubuntu/Linux?

3. I don't know if this is true but I have heard that is also good at game making, is this also true?

4. Is it based on C++/C or created from scratch?

Thanks for your help :)

---

### Post by PaulM1985 on 2011-03-21
1. I have heard its it's especially good at creating gui's, is this true?

I use C# regularly for work. I have found that it is quite good for creating gui's but that is using Visual Studio.  I have not had much experience of the designer in MonoDevelop.

2. It was originally created for windows, how compatible is it with Ubuntu/Linux?

I haven't really had any experience of cross compatibility.  Small test projects I make seem to work ok. I have had some issues running other peoples stuff but that is because they are dependent on platform specific compiled libs.

3. I don't know if this is true but I have heard that is also good at game making, is this also true?

Don't know.  SDL sounds familiar.  I had trouble setting this up.

4. Is it based on C++/C or created from scratch?

I would say it is more like Java than C++/C.

Paul

---

### Post by might and power on 2011-03-21
I use c# professionally too. Overall, id say that it is an excellent language with excellent tools to go with it but on linux you will find it not nearly as productive, though still good. 

 On linux its all done through the mono platform which is a port of Microsoft's .Net runtime. Mono is a litte behind .Net which is to be expected. 

As for what language it is like, it was originally a combination of of c++ and java but has evolved into it's own unique language.
 
It's a very "big" language and takes a long while to master, but it's definitely worth it. 

For games, yes id say it pretty good. For performance reasons, most commercial games are written in native code (asm, c, c++) but this is starting to change. XNA is the c# game framework. On windows its excellent but you should research how well its supported on linux and understand from the start that it's a windows language so you will have less support than you would on windows. However one good thing about that is your games will be cross platform.

---

### Post by robro on 2011-03-21
Thanks for the replies, cross platform is very important to me so even though its a little behind thats fine :)
I'm pleased to here thats good for creating gui's and games as thats probably gonna be the main use.

So now that I got the info I need, does anyone have a good (preferably free) tutorial/ebook to recommend?

Also 2 more question, compared to C++ how hard is C# too learn? and will it be better to make games with C# than C++?

Thanks you very much for the help :)

---

### Post by might and power on 2011-03-21
Speaking for myself, i estimate that c# is a lot easier to learn than c++. But it's kinda hard to say cause i learnt how hard to program years ago. c++ is thought of as a "hard" language because of the "combo" of pointers, object orientation and strange looking syntax. There are no pointers in c# and the syntax is cleaner, so understanding OO programming is the only barrier (apart from understanding basic syntax) to being productive in c#. 

Once you get into the language a bit there are numerous difficult concepts to understand (with more being added all the time) but, like i said, its a *very* rich language and you dont have to understand it all. Developers where i work are constantly being being taught about the latest innovations in the language by outside consultants.

the official msdn documentation is very thorough: [http://msdn.microsoft.com/en-us/library/aa288436(v=vs.71).aspx](http://msdn.microsoft.com/en-us/library/aa288436(v=vs.71).aspx)
c# station is rather popular too. [http://www.csharp-station.com/Tutorial.aspx](http://www.csharp-station.com/Tutorial.aspx)

---

### Post by directhex on 2011-03-21
> **robro said:**
> 1. I have heard its it's especially good at creating gui's, is this true?

Within the Ubuntu ecosystem, the GUI designer built into MonoDevelop, which only works for making C# apps, is nicer than the standalone Glade designer which works with everything. Beyond that, the language doesn't matter much if you use a designer.

> 2. It was originally created for windows, how compatible is it with Ubuntu/Linux?

There's not much that's language-specific in the libraries you'd ever use for a GUI app. Most cross-platform questions are already handled in the language - e.g. using System.IO.Path.Combine("a","b") rather than "a/b" or "a\b" which are both platform-specific

> 3. I don't know if this is true but I have heard that is also good at game making, is this also true?

Most commercial games are made with multiple languages - a 3D engine written in a high-performance language like C, and a scripting engine for design (usually Python or Lua). Mono's been used in a few million installs for the latter part (The Sims 3 includes Mono for this, as do many iPhone games). Technically you could use it for the former, via assorted swappers to OpenGL or similar, but it's a path less travelled.

> 4. Is it based on C++/C or created from scratch?

The language is more like Java in style than anything else. There are a few nods to C++, but generally it avoids much of the low-level work which typifies C++ development. The Mono C# compiler itself is written in C#. The Mono runtime is C.

---

### Post by stchman on 2011-03-22
I would go with Java over C#.

There are excellent FREE tools for Java development like Netbeans, Eclipse, IntelliJ, the Java SDK is FREE and currently works on all three major platforms (Windows, Linux, OS X).

Java is excellent at creating GUIs using the IDE and those GUIs will run on multiple platforms.

---

### Post by directhex on 2011-03-22
> **stchman said:**
> I would go with Java over C#.

There are excellent FREE tools for Java development like Netbeans, Eclipse, IntelliJ, the Java SDK is FREE and currently works on all three major platforms (Windows, Linux, OS X).

Java is excellent at creating GUIs using the IDE and those GUIs will run on multiple platforms.

All of these apply equally to a GTK# app, except MonoDevelop is actually usable, whereas Eclipse is a complete mess.

---

