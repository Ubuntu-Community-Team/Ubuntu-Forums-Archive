---
title: "C++ Jaunty -&gt; Windows"
date: 2009-06-19
forum: Programming Talk
---

### Post by mynameinc on 2009-06-19
If I write a C++ code in Jaunty, can I run it in Windows XP?  Or vice versa?  If not, what needs to be done for a proper Jaunty->Windows XP conversion?  Thanks in advance, mynameinc.

(Normally, I avoid Windows at all costs, but an exclusive XP user asked me to write an app.)

---

### Post by SledgeHammer_999 on 2009-06-19
If the code you use is cross-platform then you can compile it in Windows and it will work.

---

### Post by mynameinc on 2009-06-19
> **SledgeHammer_999 said:**
> If the code you use is cross-platform then you can compile it in Windows and it will work.
How do I know what code is cross-platform?

---

### Post by Mirge on 2009-06-19
If you write ANSI C++ code, it'll compile on any platform with an ANSI C++ compiler.

If you're talking about GUI applications, you'll need to invest time in learning a cross-platform GUI framework, like Qt 4 (C++), or GTK (C).. GTK also has GTKmm (C++) binding.

Qt4 is said to be better documented, and "easier", but take it with a grain of salt. I'm just starting Qt4 myself.

---

### Post by curvedinfinity on 2009-06-19
Libraries are what will be cross platform or not. Most Linux libraries are cross platform, no Microsoft libraries are.

As long as you use cross platform libraries, the most complex part of compiling linux code on windows will be getting a development environment running in Windows. I use msys, which mostly duplicates the normal linux command line tools for windows (including g++). I generally just use a shell script that has the compile and linking steps run manually (no makefile). I make one "compile.sh" for each platform. Doing it that way keeps the number of dependencies for your toolchain small, which means there is less stuff to install and less stuff to break.

Hope that helps. :)

---

### Post by mynameinc on 2009-06-19
I know almost nothing about C++, until now I have programmed (for fun, only) in Python, TI-BASIC, and Perl.

Sorry if this is a stupid question, but is the code in emacs cross-platform?

---

### Post by curvedinfinity on 2009-06-19
Its not guaranteed to look right in some windows text editors, but all of the compilers will compile it just fine.

---

### Post by mynameinc on 2009-06-19
So, if I write a program in emacs, and compile it, said program will run in Windows?

Sorry, n00b at C++.

---

### Post by curvedinfinity on 2009-06-19
You have to move all of the source over to Windows and compile it using a compiler running in Windows. You technically can "cross-compile" a Windows binary in Linux, but its a pain in the butt -- its way easier just to have another partition (or virtual machine) for a Windows toolchain. :)

---

### Post by Idefix82 on 2009-06-19
> **mynameinc said:**
> So, if I write a program in emacs, and compile it, said program will run in Windows?


You need to compile it under Windows using a windows compiler.

---

### Post by JordyD on 2009-06-19
> **Idefix82 said:**
> You need to compile it under Windows using a windows compiler.

Like MinGW/Cygwin and g++.

---

### Post by mynameinc on 2009-06-19
Could somebody give a link that will teach me how to set up a Virtual Machine?

---

### Post by Mirge on 2009-06-19
[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

---

### Post by mynameinc on 2009-06-19
Is it possible to download a Windows compiler and run it in Wine, or to move the source code to a Windows computer via USB drive?

---

### Post by curvedinfinity on 2009-06-19
> Is it possible to download a Windows compiler and run it in Wine, or to move the source code to a Windows computer via USB drive?

(easy answers: )
No. Yes -- this is the easiest option of them all.

---

### Post by mynameinc on 2009-06-19
No to Wine, and Yes to USB?

---

### Post by curvedinfinity on 2009-06-19
correct :)

---

### Post by mynameinc on 2009-06-19
So, I write the code in emacs, save it to a USB drive, and compile it on a Windows machine?  Thanks for the help, mynameinc.

---

### Post by twright on 2009-06-19
if you have use python before that would probably be easier as you do not need to compile it for multiple platforms, as long as python is installed it will just run.

---

### Post by mynameinc on 2009-06-19
Right.  But Python needs to be installed before the program will run, and my friend wants to share this program with friends, who will share it with friends, and so on, and most of these friends don't have Python installed.

---

### Post by Mirge on 2009-06-19
[http://www.py2exe.org/](http://www.py2exe.org/)

---

### Post by mynameinc on 2009-06-19
Thanks!  That will make my life a lot easier.

---

### Post by Mirge on 2009-06-19
Dang lol are you like hitting Refresh non-stop? lol

---

### Post by mynameinc on 2009-06-19
No... I just check it every few seconds... my "occupation" allows me to do that during summer...

---

### Post by rbprogrammer on 2009-06-19
If it is absolutely necessary, I use Dev-C++ in windows for making windows executables.  It's rather easy to install if you have not checked it out already.

The homepage is here: [http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)
The download page is here: [http://www.bloodshed.net/dev/devcpp.html](http://www.bloodshed.net/dev/devcpp.html) choose the "Dev-C++ 5.0 beta 9.2 (4.9.9.2) (9.0 MB) with Mingw/GCC 3.4.2" option.

---

### Post by Mirge on 2009-06-19
> **mynameinc said:**
> No... I just check it every few seconds... my "occupation" allows me to do that during summer...

Hehe I was just teasing

---

### Post by mynameinc on 2009-06-19
Can I run Python 2 .exe in Linux?

---

### Post by Mirge on 2009-06-19
I don't mind helping, but you should show some effort on your part too.

Google is a great search engine... Py2exe has a FAQ.. both are useful.

[http://www.google.com/search?hl=en&q=py2exe+linux&aq=f&oq=&aqi=g1](http://www.google.com/search?hl=en&q=py2exe+linux&aq=f&oq=&aqi=g1)

---

### Post by mynameinc on 2009-06-19
> **Mirge said:**
> I don't mind helping, but you should show some effort on your part too.

Google is a great search engine... Py2exe has a FAQ.. both are useful.

[http://www.google.com/search?hl=en&q=py2exe+linux&aq=f&oq=&aqi=g1](http://www.google.com/search?hl=en&q=py2exe+linux&aq=f&oq=&aqi=g1)

Sorry, I searched Py2Exe's website thoroughly, yielding nothing.  I forgot about Google. ](*,)

---

### Post by curvedinfinity on 2009-06-19
With Linux, just make a very simple installer package that links Python as a dependency. In this forum, there is a sticky thread that I wrote which describes how to make a Debian package. It should take about 2 minutes to make your first one.

---

### Post by mynameinc on 2009-06-19
Thanks, but I'll probably stick with C++ (my favorite language, not the one I'm most familiar with) and compile on a Windows machine.

---

### Post by twright on 2009-06-19
> **mynameinc said:**
> Thanks, but I'll probably stick with C++ (my favorite language, not the one I'm most familiar with) and compile on a Windows machine.
Right, if you are writing a windows application you might have to actually run it on windows :-) (shudders)

---

