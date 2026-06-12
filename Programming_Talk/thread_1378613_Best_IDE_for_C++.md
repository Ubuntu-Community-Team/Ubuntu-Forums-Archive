---
title: "Best IDE for C++"
date: 2010-01-11
forum: Programming Talk
---

### Post by Namesake on 2010-01-11
Hi all,

I am just getting into programming with C++, and have programmed in JAVA and FORTRAN before. What do you recommend is the most user friendly IDE for C++ on Ubuntu Karmic?


I have already installed C++ and other things with this command line:
sudo apt-get install build-essential

Thanks for the help

---

### Post by Iowan on 2010-01-11
[This]("http://ubuntuforums.org/showthread.php?t=1371120") *might* help - another thing on my To-Do list...

---

### Post by Sef on 2010-01-11
Moved to Programming Talk.

---

### Post by Queue29 on 2010-01-11
Eclipse-cdt or Monodevelop are going to be #'s 1 and 2 for IDE's, but get ready for fanboi responses telling you to use vim and/or emacs.

---

### Post by pbrane on 2010-01-11
You might also take a look at Anjuta.

---

### Post by Firestom on 2010-01-11
I'd reccomend Code::Blocks. The IDE is in Ubuntu's repositories and you can install it by using this command: ```
sudo apt-get install codeblocks
```

---

### Post by not_a_phd on 2010-01-11
If you are leaning toward lightweight - **geany**.
If you like java induced pain but a full featured IDE - **eclipse**. 
If you are looking for an up and comer with some polish - **qtcreator**.

---

### Post by Namesake on 2010-01-12
Thanks for all the suggestions team!

I have decided to go with EclipseIDE. After some research, it seems that many people have trouble getting it too run well. Should I follow the advice of the Ubuntu community given in this link for Karmic:

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by korvirlol on 2010-01-12
the only IDE you need is linux

---

### Post by SunSpyda on 2010-01-12
Minimalism                    = Vim, and the build tools
Similarity with VC++          = MonoDevelop
Tons of clever features       = GNU Emacs and the build tools
Lots of support and popular   = Eclipse
Quite fast, and built for C++ = Code::Blocks

When I say 'and the build tools', what I actually mean is that you will have to become familiar with *cc*, *ld*, and *make*. And maybe even *gdb* and *as*, if you really want to go for it ;)

IDEs really to make the process easier. When done manually, it consists of writing make files, and learning the tools to use within make.

That being said, it's far more portable than depending on a certain IDE to do it for you.

---

### Post by Colonel Kilkenny on 2010-01-12
Qt Creator without a doubt. Small, fast, easy to use and under very active development.

Eclipse is okayish when it works but when something goes wrong (example: it updates itself/plugins and won't start) it can cause a total and utter RAGE, KDevelop is IMHO too KDE-centric, CodeBlocks is just somehow unintuitive and ugly (plus way back when I tried to use it, it had irritating bugs and issues with stability). Vim and Emacs are for nerds with glasses and sweaty armpits ( :) )

---

### Post by caelestis2 on 2010-01-12
KDevelop 4 is easy fast, has simple project folders, uses a universal build system, has all the features. I love it.

---

### Post by schmendrick on 2010-01-13
+1 for qt creator.

best debugger in town  :)


especially if you got lazy by working too much in java.

but its not only about the debugger, IMHO it is best IDE ATM, and is also fast easy and straightforward

---

### Post by Namesake on 2010-01-19
> **Colonel Kilkenny said:**
> Qt Creator without a doubt. Small, fast, easy to use and under very active development.

Eclipse is okayish when it works but when something goes wrong (example: it updates itself/plugins and won't start) it can cause a total and utter RAGE, KDevelop is IMHO too KDE-centric, CodeBlocks is just somehow unintuitive and ugly (plus way back when I tried to use it, it had irritating bugs and issues with stability). Vim and Emacs are for nerds with glasses and sweaty armpits ( :) )


Awesome, thanks for the advice. I have installed it :D

---

### Post by DarkAmbient on 2010-08-14
I know this thread is starting to get old.

Just wanted to add that gedit that comes preinstalled with Ubuntu is really smooth to program in aswell. Got everything you need to code & compile. Just install the essential stuff to be able to compile, then make use of the external tool plugin in gedit. (or compile via the terminal, same same rly)

edit: even though gedit is normally just a texteditor and this is about IDE's. But gedit is damn flexible when it comes to usage. :-)

---

### Post by wkhasintha on 2010-08-14
code::blocks

---

