---
title: "Do you use an IDE?"
date: 2010-04-01
forum: Programming Talk
---

### Post by KdotJ on 2010-04-01
For all those that program, from those of you who write simple programs to those of you who develop large projects. Do you use an IDE?

I wanted to know, as with the majority of programs nowadays having a rich GUI at the front end, who of you code these components and layouts just purely in a text editor? or who drag and drops the components onto a visual representation of the form in an IDE? Even the most hardcore programmers, who know through and through how to design and program the GUI, do you just save time and use an IDE?

just curious...

---

### Post by Simian Man on 2010-04-01
Are you asking if we design a GUI with a visual design tool, or if we develop an application using an IDE?  Because those are two different questions.

I use an IDE for projects where it makes sense to do so.  Ie if the code is self-contained and there is a decent IDE in the language I'm using.  But I *never* create a GUI using a GUI builder - except as a mockup.

---

### Post by CptPicard on 2010-04-01
Depends on the language. In Java, Netbeans really is indispensable with its refactorings, and in web/J2EE projects even more so... in Python, I rarely bother, as the language is too dynamic for static code analysis anyway.

---

### Post by KdotJ on 2010-04-01
[QUOTE=Simian Man;9061545]Are you asking if we design a GUI with a visual design tool, or if we develop an application using an IDE?  Because those are two different questions./QUOTE]

apologies, I should have been more specific. I meant in general, whether its for code-completion or GUI building. I was just using GUI as an example. 

I occasionally use an IDE for the one click compile button that will show me any errors, rather then having to keep switching back to the terminal every time.

---

### Post by km0r3 on 2010-04-01
I'd say it depends.

If I program in Python 95% of the time I use Vim. It can be a pretty attractive IDE with a little work, too; otherwise I use WingIDE.
In case of Vim, I use code folding, NerdTree, OmniComplete, RopeVim and SnippetsEmu; I miss almost nothing with those plug-ins.
Maybe code completion in WingIDE is faster and better, but I rarely use that. I'd rather look up the Python module reference by pressing a key in Vim :) .

If I do Java or C++ I'd rather go with Eclipse. Those languages are nasty. :)

I just feel more comfortable in a Terminal using Vim, but that's personal preference.

---

### Post by MattBD on 2010-04-01
I admit I don't do a huge amount of coding at the moment as I'm currently working my way through a web development course and it's rare I actually get to sit down and write code, but when I do I use Vim exclusively. I used it to mark up all the HTML, CSS and JavaScript for my website, and I've used it for a fair amount of Python and some C programming too.

---

### Post by diesch on 2010-04-01
I'm using Emacs for coding and sometimes Glade as GUI builder

---

### Post by wmcbrine on 2010-04-01
The last time I used an IDE was with Borland Pascal 7. I tried switching to Qedit + command-line BPC, found that a much better experience, and haven't looked back. Although sometimes I wonder what I'm missing...

It wasn't perfect, of course -- some operations that were automated in the IDE became manual. But the trade-off was that I got to use a much better editor, and that hasn't changed. When I picked up Python, I tried IDLE for about five minutes, and couldn't stand it.

---

### Post by matthew.ball on 2010-04-01
> **diesch said:**
> I'm using Emacs for coding and sometimes Glade as GUI builder
Yep, I use emacs for coding and wxFormBuilder to create forms.

---

### Post by KdotJ on 2010-04-01
At my university we covered an OOP module and used a java IDE named BlueJ (if any one has ever heard of it?) It didnt have code completion, it was basically a text editor with a compile button.  But it graphically showed you the classes and their relationships, not exactly in UML notation but still.

---

### Post by sujoy on 2010-04-01
I code exclusively in emacs (except java for which I use netbeans).
I can compile from the same environment I code in, and jump to errors too. What else could I ask for? Debugging maybe. However, gdb has been more than enough for me so far. :)

---

### Post by hessiess on 2010-04-02
Just Vim.

---

### Post by Some Penguin on 2010-04-02
> **KdotJ said:**
> For all those that program, from those of you who write simple programs to those of you who develop large projects. Do you use an IDE?

I wanted to know, as with the majority of programs nowadays having a rich GUI at the front end, who of you code these components and layouts just purely in a text editor? or who drag and drops the components onto a visual representation of the form in an IDE? Even the most hardcore programmers, who know through and through how to design and program the GUI, do you just save time and use an IDE?

just curious...

When you're working on a project that takes multiple people multiple months to year+ to implement, to design a complex system that is meant to maintain near-100% availability and scale to many, many users interacting with minimal latency, and whose design will require many servers with several different roles -- you should probably be coding using something more than a text editor, your memory, and a version control system. 

Speaking as somebody who's been programming since about 1984 or so (Cartridge BASIC on the Jr, hah!), I've done probably more than my share of text-editor-based coding (having predated the development of modern IDEs) and have no problems using them for scripting or for modest programs -- algorithmic experiments, in particular.   I once developed a set of modules with 24,000+ of lines of somewhat math-dense Perl (mostly related to statistics) using XEmacs, which was a suboptimal process on my part.  *shrug*

I also have seen Eclipse crash or otherwise fail horribly far too often for me to be remotely fond of it.  However, the more complex the system (and one note to keep in mind is that in reality, you have to be careful assuming that third-party dependencies actually work properly -- to have an understanding of your own project, you not only need to understand your own design but also the quirks and outright failures of anything you're relying on, and blatant standards violations are not exactly unheard of), the more difficult it'll be to fully understand it and to therefore develop or debug it.  If you have a possible resource leak or deadlock showing up somewhere in a PostgreSQL + Tomcat  combination, you'll likely find it much faster using decent profiling tools that let you easily inspect stacks and memory snapshots than you would just being, say, a fanatical logger.  A decent IDE should let you run unit tests, show you dependencies, refactor code without having to write scripts to do the refactoring to update all the references, let you easily see which files differ versus the last time you committed changes, highlight potential coding issues, and so forth.

---

### Post by wmcbrine on 2010-04-02
> **Some Penguin said:**
> you should probably be coding using something more than a text editor, your memory, and a version control system.Yep -- you also need grep! :D

---

### Post by johnl on 2010-04-02
> **sujoy said:**
> I code exclusively in emacs (except java for which I use netbeans).
I can compile from the same environment I code in, and jump to errors too. What else could I ask for? Debugging maybe. However, gdb has been more than enough for me so far. :)

Check out this article: [Emacs Mode for GDB](http://www.linuxjournal.com/article/7876).  I also use Emacs and I've found that the GDB integration is actually pretty good :)

> **Some Penguin said:**
> When you're working on a project that takes multiple people multiple months to year+ to implement, to design a complex system that is meant to maintain near-100% availability and scale to many, many users interacting with minimal latency, and whose design will require many servers with several different roles -- you should probably be coding using something more than a text editor, your memory, and a version control system. 

That's funny, I work on just such a project (11-year-old codebase, >4 Million LOC) and almost every developer uses vi or emacs. There are some that use visual slickedit.

---

