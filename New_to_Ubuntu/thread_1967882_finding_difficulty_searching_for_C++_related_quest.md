---
title: "finding difficulty searching for C++ related questions"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by freefallAddict on 2012-04-28
I'm trying to be a good new user and search for similar posts before I ask a question - but I can't seem to search for the term C++ - it doesn't return any results.

my question is this:
I've got several years of commercial C++ experience on the windows platform.  

I need to learn C++ on the linux platform.  I'm most interested in covering the following areas:

Building on linux - make tools - what is available, what do other people use?

multithreading, locking mechanisms.

networking - client & server applications.  

threadpools.

User interfaces - what are the popular libraries?  I've heard good things and bad things about Qt; is it the best choice?

IDE's.  I hear that linux folks cling religiously to their text editors and balk at people for using a mouse much less an IDE.  Does linux have any decent IDEs that match (or come close to) the functionality of Visual Studio?

What's the best frontend for gdb?

I've used linux in the past as a web development and server platform, so I know my way around the system, but this is the first Are there any other tools I should be aware of??

---

### Post by drdos2006 on 2012-04-28
The search for C++ is far too generic.
Try this link.

[http://ubuntuforums.org/showthread.php?t=1725448&highlight=programming](http://ubuntuforums.org/showthread.php?t=1725448&highlight=programming)

regards

---

### Post by r-senior on 2012-04-28
Welcome :)

The best place to ask your programming questions, even if you are an absolute beginner with Ubuntu, is in the Programming Talk forum:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

I don't do much C++ but I can answer some of your questions:

1. Build tools - GNU autotools (autoconf and automake) are intimidating to begin with but make building projects that can be packaged for Linux much easier once set up. These are pretty standard for Linux applications written in C and C++.

2. User interface - QT is a good cross-platform toolkit but if you want to write native applications for Gnome, consider gtkmm which provides C++ bindings for GTK and the best integration into the Gnome look & feel.

Have a look at [http://www.zetcode.com](http://www.zetcode.com) for examples.

3. IDEs - some people swear by text editors but many Linux developers use IDEs of varying levels of sophistication. Eclipse and Netbeans both run on Windows/Linux/Mac and can be used for C++ development. Code::Blocks is another one. Geany sits somewhere between an IDE and a text editor/terminal combo.

4. Eclipse and Netbeans both have visual debuggers for GDB. Not sure about Code::Blocks but I imagine so. Geany has a plugin for GDB.

5. Valgrind for tracing memory leaks and other errors. Make as a build tool in conjunction with the GNU autotools already mentioned. Distributed VCS, e.g. Bazaar or Git. Launchpad is a great place for code hosting.

Your other questions are beyond my C++ knowledge but there are plenty of C++ experts who browse the Programming Talk forum.

---

### Post by haqking on 2012-04-28
if you go to google and type in the following

```
c++ site:ubuntuforums.org
```

The forum search is not the best, but the above google will link you to all C++ related stuff on the forums.

Peace

---

