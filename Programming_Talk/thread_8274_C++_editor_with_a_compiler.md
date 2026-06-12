---
title: "C++ editor with a compiler"
date: 2004-12-15
forum: Programming Talk
---

### Post by akamjballar on 2004-12-15
I am looking for the best c++ editor with a compiler. If you guys know some good programs, please tell me.

---

### Post by az on 2004-12-15
g++ and emacs?

Throw in Glade.

---

### Post by jdong on 2004-12-15
gedit is a nice lightweight editor... Unixers love emacs and vim...

Anjuta is a full-scale IDE.

So is eclipse.

I've heard good stuff about JEdit.


Moving you to the right forum...


P.S. g++ is the de facto Linux C++ compiler.

---

### Post by akamjballar on 2004-12-15
Is eclipse only for Java or c++ too?

---

### Post by akamjballar on 2004-12-15
I have installed g++ via Synaptic. But for some reason I can't see it in the programming bar(using gnome). I tried looking for it manually, but I seem to not find it. Can someone tell me what directory it might be installed in.

---

### Post by Hikaru79 on 2004-12-15
[QUOTE=akamjballar]I have installed g++ via Synaptic. But for some reason I can't see it in the programming bar(using gnome). I tried looking for it manually, but I seem to not find it. Can someone tell me what directory it might be installed in.[/QUOTE]

It's not supposed to be there; g++ is a compiler, not a technical "program"... aka, it doesn't have an execution window or anything. To use it, simply write up your .cpp file, and then run g++ on it through the command line. If you want an actual program to write C++, get one of the IDE's listed above.

---

### Post by jdong on 2004-12-15
g++ is more of a command, not a program. You can read **man g++** for more info on how to use it.

Use a full-blown IDE, like **anjuta**, which can be obtained through Synaptic in Universe.

---

### Post by akamjballar on 2004-12-15
Sorry, I thought g++ was an ide. I didn't know it was a compiler. Didn't read the actual description. :oops:

---

### Post by jwenting on 2004-12-16
Borland C++ BuilderX is available for Linux (there's a free version as well as several levels of paid for versions offering more options and features).
Borland makes excellent products, I think you'll like it.

---

### Post by dataw0lf on 2004-12-16
Personally, I think the combination of vim, g++ (well, gcc in my case), and gdb is unbeatable.  But to each their own.  I was extremely unimpressed with Anjuta (I think it still has a ways to go), and Jedit I prefer for higher-level languages, like Python or PHP.  I'm a fan of 'the simpler, the better', I've just never seen the need for 'uber c00l' features in some bloated IDE.  
dataw0lf

---

### Post by jwenting on 2004-12-17
[QUOTE=dataw0lf]Personally, I think the combination of vim, g++ (well, gcc in my case), and gdb is unbeatable.  But to each their own.  I was extremely unimpressed with Anjuta (I think it still has a ways to go), and Jedit I prefer for higher-level languages, like Python or PHP.  I'm a fan of 'the simpler, the better', I've just never seen the need for 'uber c00l' features in some bloated IDE.  
dataw0lf[/QUOTE]
 Think about WHY you use fullfeatured editors for one language and not another.
What's so different in Java that you use those extra features but for C you think them bloat?

---

### Post by drac on 2004-12-20
You could use [Visual SlickEdit](http://www.slickedit.com/). It has a Visual Studio Emulation (vi and emacs too) for those (like me) who come from Visual Studio land...

---

### Post by Quest-Master on 2004-12-20
Too bad both of their products aren't open-source or freeware. :(

---

### Post by bob k on 2004-12-20
I use Eclipse. Once you get two or three levels deep and have a bunch of lib headers std headers and local headers. It's niece to just start your project environment with every thing pre loaded so you don't have to go looking around for the args in a lib routine.

---

### Post by jdong on 2004-12-20
Yeah, though vim and editors work wonderfully for little projects, once you have 50+ source files floating around, keeping track of them by hand -- even with makefiles -- becomes an absolute pain.

---

### Post by nigelng on 2004-12-20
Nano & gcc should be file. There are some C/C++ .nanorc for highlighting

nigel

---

### Post by dataw0lf on 2004-12-20
[QUOTE=jwenting]Think about WHY you use fullfeatured editors for one language and not another.
What's so different in Java that you use those extra features but for C you think them bloat?[/QUOTE]
hmmmm... ok, you got me, why?? ;) Honestly, the current trend seems toward learning specific IDEs rather than the programming languages themselves.   With a basic syntax highlighting editor you get all you need to delve into source code; I haven't ever really needed a 'full featured IDE' since I began programming, with the possible exception of when I was using Borland Builder many years ago for Windows development.  This huge push to grab these enormous IDEs is detracting alot from the community, with few side benefits.
dataw0lf

---

### Post by Enygma on 2004-12-21
I'm of the beleif that someone beginning programming should just grab a simple text editor with syntax highlighting and compile from the command line. You learn more about your environment and get an idea of what's going on beneath the hood.

Besides, programmers that are just beginning won't be writing any huge programs so the features of an IDE would only serve to confuse. 

The IDE is great for the experienced programmer who doesn't want to have to bother with the basics.  For example in Eclipse when I'm writing code and I use a class that I haven't imported it shows up like a spelling error, then I just press Ctrl-Shift-M and it's automatically added to my imports. 

Then you've got features like Refactoring, Unit Testing, Debugging etc all built into the environment. 

I think a push to IDEs means that people are moving on and not concerning themselves with the basic mundane aspects of programming. They allow good programmers do what they do best, write programs.

---

### Post by bob k on 2004-12-21
[QUOTE=Enygma]I'm of the beleif that someone beginning programming should just grab a simple text editor with syntax highlighting and compile from the command line. You learn more about your environment and get an idea of what's going on beneath the hood.

Besides, programmers that are just beginning won't be writing any huge programs so the features of an IDE would only serve to confuse. 

The IDE is great for the experienced programmer who doesn't want to have to bother with the basics.  For example in Eclipse when I'm writing code and I use a class that I haven't imported it shows up like a spelling error, then I just press Ctrl-Shift-M and it's automatically added to my imports. 

Then you've got features like Refactoring, Unit Testing, Debugging etc all built into the environment. 

I think a push to IDEs means that people are moving on and not concerning themselves with the basic mundane aspects of programming. They allow good programmers do what they do best, write programs.[/QUOTE]
 Thats a good point. Even the best have to go back the basics to find a problem. A noob programmer using a gedit, vim, emacs type editor will learn allot more about the envionment than using an eclipse. After a few good sized programs they will have learned the libs, headers, and external linkage to other languages (XML, Glade, Java, Python) and will be able to analyze and code the problem in an efficent manor.

---

### Post by vasiauvi on 2008-03-09
> **bob k said:**
> Thats a good point. Even the best have to go back the basics to find a problem. A noob programmer using a gedit, vim, emacs type editor will learn allot more about the envionment than using an eclipse. After a few good sized programs they will have learned the libs, headers, and external linkage to other languages (XML, Glade, Java, Python) and will be able to analyze and code the problem in an efficent manor.

I am new in Linux and in C programming, but I want to learn.I have installed the Anjuta but how can I compile the program from command line?

---

### Post by Acglaphotis on 2008-03-09
Geany or Vim are great for what you are asking.

---

### Post by vasiauvi on 2008-03-09
> **Acglaphotis said:**
> Geany or Vim are great for what you are asking.

Thank you!
I have managed to do a program and to compile it.I have read this: [http://www.wm.edu/computerscience/computing/gpp.php](http://www.wm.edu/computerscience/computing/gpp.php)
I will also try Geany!:)

---

