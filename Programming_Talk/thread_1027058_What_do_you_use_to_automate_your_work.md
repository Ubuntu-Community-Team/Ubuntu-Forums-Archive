---
title: "What do you use to automate your work?"
date: 2008-12-31
forum: Programming Talk
---

### Post by Delever on 2008-12-31
What do you use to automate your work, so you can focus on programming?

It doesn't matter what language you choose, you usually need few more things, like:
- Use existing libraries and code
- Code for different platforms
- Automate some tedious tasks
- Compile, pack, prepare for distribution, create installer

Maybe you have some invaluable scripts for that crafted? Or maybe you use some tools to help you out, and otherwise no customizations, just good knowledge of what to do?

So, how do you do it?

---

### Post by CptPicard on 2008-12-31
This is one of the strong points of working mostly in Java -- Netbeans (or Eclipse) does everything for you, you just write the code. The only thing that is lacking in Java world is a decent deployment mechanism (raw .jars with dependencies are too hard for end user)...

---

### Post by Delever on 2008-12-31
> **CptPicard said:**
> This is one of the strong points of working mostly in Java -- Netbeans (or Eclipse) does everything for you, you just write the code. The only thing that is lacking in Java world is a decent deployment mechanism (raw .jars with dependencies are too hard for end user)...

Yeah, so in that case, how do you solve that? Maybe writing small executable file to run Java environment?

---

### Post by CptPicard on 2008-12-31
> **Delever said:**
> Yeah, so in that case, how do you solve that? Maybe writing small executable file to run Java environment?

On Linux packaging some shell scripts into .debs or whatever is not a huge issue... on Windows, I am afraid my client needs to just whine and finally succumb to hiring a tech support guy who is able to create a few .bats and set the classpath in the system environment ;)

---

### Post by Reiger on 2009-01-01
@Cpt Picard: why? Why not set the classpath in the Manifest file of your JAR?
```

Classpath: <classpath>

```

---

### Post by tinny on 2009-01-01
> **Delever said:**
> Yeah, so in that case, how do you solve that? Maybe writing small executable file to run Java environment?

Java web start helps

[http://java.sun.com/javase/technologies/desktop/javawebstart/index.jsp](http://java.sun.com/javase/technologies/desktop/javawebstart/index.jsp)

Or a nice big fat Java application installer.

[http://nsis.sourceforge.net/Main_Page](http://nsis.sourceforge.net/Main_Page)
[http://www.advancedinstaller.com/java.html](http://www.advancedinstaller.com/java.html)


> **Delever said:**
> What do you use to automate your work, so you can focus on programming?

It doesn't matter what language you choose, you usually need few more things, like:
- Use existing libraries and code
- Code for different platforms
- Automate some tedious tasks
- Compile, pack, prepare for distribution, create installer

Maybe you have some invaluable scripts for that crafted? Or maybe you use some tools to help you out, and otherwise no customizations, just good knowledge of what to do?

So, how do you do it?

Continuous integration can be useful when working in a team environment. Helps aid test driven development.

[http://en.wikipedia.org/wiki/Continuous_integration](http://en.wikipedia.org/wiki/Continuous_integration)

Test automation
Report automation
etc...

---

### Post by jespdj on 2009-01-01
I program in Java (that's my job); we are using Ant for building our software and JUnit for unit testing. Those are two pretty much standard tools in the Java world.

There's also Maven for building and automatically managing dependencies.

---

### Post by Cracauer on 2009-01-01
Many, many years of hacking up elisp code and customizing emacs.

Steal ideas for making things more efficient from everywhere, Lisp machines in particular.

Always write the unit test code or regression tests or whatever right with the main code.

Stop wining, stop hacking up your own thing and use autoconf/automake.  It's the lousiest you can imagine, but it still gets the job done.

Have frontend script for braindead commandline tools.  In particular make/gmake, cvs/svn/git, ploticus, find, OS upgrades, zcat/bzcat/cat.

Don't even try to use gdb for anything more than backtraces and hexdumping.

Forget about X11. Screen is it.

---

### Post by Delever on 2009-01-02
> **Cracauer said:**
> Many, many years of hacking up elisp code and customizing emacs.

Steal ideas for making things more efficient from everywhere, Lisp machines in particular.

Always write the unit test code or regression tests or whatever right with the main code.

Stop wining, stop hacking up your own thing and use autoconf/automake.  It's the lousiest you can imagine, but it still gets the job done.

Have frontend script for braindead commandline tools.  In particular make/gmake, cvs/svn/git, ploticus, find, OS upgrades, zcat/bzcat/cat.

Don't even try to use gdb for anything more than backtraces and hexdumping.

Forget about X11. Screen is it.

Do you use Lisp as main programming language?

---

### Post by Cracauer on 2009-01-02
> **Delever said:**
> Do you use Lisp as main programming language?

Yes, although I try to balance things. I actually enjoy C++ in a puzzle kind of way (as long as I am payed by hour or by line of code, not work accomplished :)). When I work for a company that uses Lisp I tend to pick C++ for my own projects and vice versa.

---

### Post by monkeyking on 2009-01-02
> **Cracauer said:**
> 
Forget about X11. Screen is it.

Yes screen is quite nice.
But I still open my screen in a x11 term.
The copy paste works better.

---

### Post by Cracauer on 2009-01-02
> **monkeyking said:**
> Yes screen is quite nice.
But I still open my screen in a x11 term.
The copy paste works better.

Of course I use xterm, I meant "emacs in X11 mode" versus "emacs in curses mode". Are there any more than these two IDEs?

Anyway, I hacked up my curses emacs to have a hotkey to exchange the emacs selection with the X11 selection, using xclip. Comes in handy to get things with line wraps in and out.

---

### Post by drubin on 2009-01-03
> **CptPicard said:**
> This is one of the strong points of working mostly in Java -- Netbeans (or Eclipse) does everything for you, you just write the code. The only thing that is lacking in Java world is a decent deployment mechanism (raw .jars with dependencies are too hard for end user)...

> **jespdj said:**
> I program in Java (that's my job); we are using Ant for building our software and JUnit for unit testing. Those are two pretty much standard tools in the Java world.

There's also Maven for building and automatically managing dependencies.

Ant build scripts are key. I haven't worked out how to integrate ant into the Eclipse GUI, but it comes standard with Netbeans.

---

