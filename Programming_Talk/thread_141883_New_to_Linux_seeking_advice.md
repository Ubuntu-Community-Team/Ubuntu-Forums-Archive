---
title: "New to Linux seeking advice"
date: 2006-03-09
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-03-09
Hi,

I am completely new to linux Environment. and because i got a Free Ubuntu CD from one of my friend i thought its time that i should give it a try. I am a C,C++(VC++),C# developer on Windows. but i always wanted to learn Linux and Unix. in fact i wanted to start learning C on linux but i never had unix in my college days so i went after windows programming, any ways it is better Late than Never. I just want to know how should i start learning C and C++ on Linux. and which IDE or Editior should i use to work ? Do i need to learn Shell scripts also? what should be my ideal start point.? Please help me. :confused: 

Thanks in advance.

**KSS**

---

### Post by cilynx on 2006-03-09
Just as an FYI, your question is bound to start a flame war.  There aren't really "industry standard" answers, more like religious orders.

It all depends what you want to do.  If you're into graphical programming, check out gtk and glade.  If you want a somewhat hard-core IDE, look into Anjuta.  If you want to join a command-line religious order, look into vi and Emacs.  If you like Java, look into Eclipse.

*Personally...*

I believe that Perl is the most powerful language on the *NIX platform.  This too is a holy war.  Many people like php, some like tcl, some are bash purists.  I use Perl for my daily automation tasks, web automation, database management, small graphical apps, ect..

I think you should know enough Bash scripting to be able to run loops on the command line and understand the files in /etc/init.d/.  Much beyond that, I would refer back to Perl.

As for C, I use vi and the GNU toolchain (gcc, cpp, make, ldd, ect...).  For C#, i use mono, but haven't had a whole lot of experience.  Most of my work there winds up back on a Windows box in VS.

Some good places to start:

Intro to Bash Programming
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

Library for Learning Perl
[http://learn.perl.org/library/](http://learn.perl.org/library/)

Anjuta
[http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)

Eclipse
[http://www.eclipse.org/](http://www.eclipse.org/)

One of the millions of sites comparing vi and emacs
[http://www.io.com/~dierdorf/emacsvi.html](http://www.io.com/~dierdorf/emacsvi.html)

Wikipedia on the GNU Toolchain
[http://en.wikipedia.org/wiki/GNU_toolchain](http://en.wikipedia.org/wiki/GNU_toolchain)

I hope this is enough to get you going...

---

### Post by der_joachim on 2006-03-09
[QUOTE=kolichina_s_s]I am a C,C++(VC++),C# developer on Windows. but i always wanted to learn Linux and Unix. in fact i wanted to start learning C on linux but i never had unix in my college days so i went after windows programming, any ways it is better Late than Never. I just want to know how should i start learning C and C++ on Linux. and which IDE or Editior should i use to work ? Do i need to learn Shell scripts also? what should be my ideal start point.? [/QUOTE]

I never got far with learning C, but I'll try to help you as well as I can. The first two questions are a bit iffy. What did you use when programming for Windows? What did you prefer? I did a bit of C at university and learned using vim as an editor. Nowadays I am a web programmer, and although I have tried numerous editors, I have always returned to vim. YMMV. It's all a matter of taste.

Shell scripts are fun, but not necessary for Linux programming. Bash is the defacto standard for linux shells. A more C-like alternative is tcsh. 
Perl is a nice programming / scripting language which can both be used as a server-side web language and a shell scripting language. It is a bit reminiscent of C (I liked it more, though). 

You mentioned C#. There is a good alternative in Linux. It is called Mono and apparently it is very mature. C and C++ are well supported in Linux. You'll have to install the meta-package build-essential ("sudo apt-get install build-essential" will do the trick) and you're set. I do not know anything about IDEs, so I cannot help you there. 

Have fun. Linux is a very developer-friendly OS. A very helpful command was "kill -9" when I was using C. Now you know why I never got really far. :)

---

### Post by rplantz on 2006-03-09
A lot depends on what you wish to do. I taught computer science at a university for over twenty years so have seen, and used, lots of approaches to learning. And each student has his/her own ideas about what he/she wants to learn.

You may wish to check out the book, "Beginning Linux Programming" by Stones and Matthew. It covers lots of things. Their approach is very "hands on." That is, they give an example, then build on it. I confess that I have not read the entire book, but the code examples I have tried all worked.

As an aside, I've seen lots of programming books. It is amazing how many of them have code examples that do not work. This, of course, hinders the learning process.

---

### Post by psychicdragon on 2006-03-10
C and C++ are still the same languages on linux as they are on WIndows. If you were doing GUI programming in WIndows, you should learn a little about the graphical toolkits available in Linux.

The two most common are GTK+ (Gnome primarily) and QT (KDE).
[http://www.gtk.org/](http://www.gtk.org/)
[http://www.gtkmm.org/](http://www.gtkmm.org/) (C++ bindings for GTK+)
[http://www.trolltech.com/products/qt/index.html](http://www.trolltech.com/products/qt/index.html)

Anyone starting linux development should read The Goat Book, to learn about the build system:
[http://sources.redhat.com/autobook/autobook/autobook_toc.html](http://sources.redhat.com/autobook/autobook/autobook_toc.html)

---

### Post by nrwilk on 2006-03-10
[QUOTE=psychicdragon]Anyone starting linux development should read The Goat Book, to learn about the build system:
[http://sources.redhat.com/autobook/autobook/autobook_toc.html](http://sources.redhat.com/autobook/autobook/autobook_toc.html)[/QUOTE]

I have been looking for something like this!  Thank you!

---

### Post by klahjn on 2006-03-10
I read a few months ago that an instructor is using eclipse for programming.  From what i've been seeing on Eclipse, the plugin system is outrageously cool.  You can pretty much program in any language using Eclipse, and considering that instructors  for college programming are starting to open thier eyes to Eclipse might help you on your path.  I'm not saying definitively that is the option, for there are several options available.  Just an opinion....if i am wrong, please accept my apologies.

---

### Post by nrwilk on 2006-03-10
I wish my java teacher had used eclipse.  I like it a lot. :) 

I will never touch Netbeans again.  It was a traumatizing experience.  :mad:    [-(

---

### Post by David Marrs on 2006-03-11
> **kolichina_s_s]Hi,

I am completely new to linux Environment. and because i got a Free Ubuntu CD from one of my friend i thought its time that i should give it a try. I am a C,C++(VC++),C# developer on Windows. but i always wanted to learn Linux and Unix.[/quote]
If you type 'sudo apt-get install build-essentials' at the shell you will get the Gnu development tools, such as the c and c++ compilers (called gcc & g++ respectively) and you'll also get other apps like make and automake, which will become useful as you develop larger projects. You can also program in C# using the mono c# compiler. I can't remember the name of the package you need, but typing 'apt-cache search mono' will find you the required packages.

You should also get the gnome and/or gtk+ apis as well, if you intend to program graphical interfaces. If you browse through synaptic you will find all the packages you need (or do another apt-cache search). If you see any documentation you should download that as well. The gnome and gtk+ docs are very good and can be found at [www.gnome.org](www.gnome.org) .

> ...and which IDE or Editior should i use to work ?
There are dozens of editors in Linux. Each has its pros and cons. Even the light-weight native editor that ships with gnome (gedit) has cool programming features like code highlighting, so you might as well start with that. The two heavy weights are vim and emacs. Both are very powerful but they also both have a steep learning curve. They were born a long time ago and have strange, old fashioned habits. Personally, I switch between gvim (a graphical  front-end to vim) and bluefish, depending on what I'm coding.
> Do i need to learn Shell scripts also?
No, but they're used extensively in Linux, so I'd certainly get used to reading them. Eventually, you will start programming them yourself said:**
> what should be my ideal start point.?
If I were you, I'd get used to using the shell. Find a good unix shell tutorial if you don't know the basics already (there are loads on google) and practice changing directories, creating, editing and deleting files, piping files through filters like grep, and so on.

When programming, try not to reinvent the wheel. The main practical advantage of unix over Windows (imo) is that your application can use any other app that runs in the shell and accepts an input, so program your apps to run in the shell first, and then extend them to run in a GUI. Many Linux apps are developed this way. Synaptic, for example, is a graphical front-end to apt. In fact, you can write quite sophistocated shell scripts using nothing but other people's programs! :p

---

### Post by nrwilk on 2006-03-11
Here are several tutorials and introductions to bash, the most commonly used shell, and the shell you'll be logging into on ubuntu by default.  Several of these have helped me a lot.

```

http://www.linuxcommand.org
http://www.faqs.org/docs/bashman/bashref.html
http://www.gnu.org/software/bash/manual/bash.html
http://www.hypexr.org/bash_tutorial.php
http://linux.org.mt/article/terminal

```

This is a guide to writing shell scripts aimed towards C/C++ programmers:
```
http://quong.best.vwh.net/shellin20/
```

Here're some scripting tutorial sites:
```
http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html
http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html
http://www.faqs.org/docs/abs/HTML/
```

I'm sure there're many many more.

---

### Post by Ozitraveller on 2006-03-11
Here is some info on Mono I jst added to another thread, which might help:
[http://ubuntuforums.org/showpost.php?p=814396&postcount=67](http://ubuntuforums.org/showpost.php?p=814396&postcount=67)

---

### Post by kolichina_s_s on 2006-03-13
Thanks a lot to all of you.

I thought i will hardly find any reply here, but it was gr8\\:D/ 

i am sorry that i am refering you all by your Email IDS but,

cilynx,
der_joachim,
rplantz,
psychicdragon,
nrwilk, Why Johnny thought  H20 was H2SO4. ;) 
klahjn,
David Marrs,

Though its a bit tuff to learn Linux but i will 

Thanks a lot :-D 
**KSS**

---

