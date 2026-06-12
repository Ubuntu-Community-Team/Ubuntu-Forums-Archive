---
title: "Code blocks won't open!"
date: 2016-12-02
forum: New to Ubuntu
---

### Post by nantia on 2016-12-02
Hello!
Yesterday i installed code blocks and it worked fine. Today i tried to open it and it was not responding at all.
(I clicked on it and nothing happened).
 So i deinstalled and installed code blocks again but it still won't open..
What is wrong with my system ?

---

### Post by TheFu on 2016-12-03
Have you tried running it from a terminal to see any error messages output?

---

### Post by nantia on 2016-12-03
i am not sure how to do that!
if i type in terminal : "codeblocks"
the output is "Starting Code::Blocks Release 16.01  rev 10760 Feb  2 2016, 03:15:41 - wx2.8.12 (Linux, unicode) - 64 bit"

---

### Post by TheFu on 2016-12-03
Is there a debug output option?  I've never used codeblocks. Learned how to code using Turbo C and gcc. ;)
They frown upon people providing answers that a google search would find here.  [http://www.codeblocks.org/docs/main_codeblocks_en.html](http://www.codeblocks.org/docs/main_codeblocks_en.html) says to use **/d** as an option.  We need more output to see the problem, right?

If you are going to code on a Linux/Unix system, you'll need to know more about the OS and get more comfortable with the shell. Spend an hr quickly reading the links from [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) in the order provided. Once you get to the PDF book, grab that. It teaches beginning to intermediate Unix commands in the correct order they should be learned.  My only issue with the book is the way they teach file/directory permissions.   "World" is not correct, "other" is for reasons that become clear eventually.

---

### Post by nantia on 2016-12-03
Hey!
i started yesterday night using gcc, since i couldn't use my codeblocks to write the things i had to, for my c++ class ;-)
I am using my linux system about a year, i know the very basics about the shell and i am constantly learning more...
thank you very much for the link, i am sure going to find some time to read it!

Have i understood right, that you prefer to code by the terminal (gcc) ? Do you think it is better for me to do the same, instead of using f.e code blocks?

---

### Post by TheFu on 2016-12-03
There are trade-offs with any type of coding.  I haven't used an IDE for Linux programming .. er ... ever.  The OS is the IDE.  Is that better? Idunno. It is the way all the experts do it and did it when I was learning 20+ yrs ago.  Basically, i use a different terminal for each different aspect of coding - call it an IDE, if you like.  [https://sanctum.geek.nz/arabesque/series/unix-as-ide/](https://sanctum.geek.nz/arabesque/series/unix-as-ide/) explains that method (I suppose. I didn't read it).  It is just that Unix as an OS was designed to deal with and process text files. It is brilliant at that, beyond what any other OS does, by far.

Give me an editor and a few xterms, and I'm happy.  I never have to spend time trying to find a setting buried in some IDE that is breaking my code/built/project.  Plus, I can use 5 systems to build my code faster - parsing out different parts to each system. This is a custom Makefile thing, beyond the typical -j5 option.

For building only that which needs building, I use Makefiles. I think the kids are using CMake these days, but I still use gmake. Around 2002, I did have to change how my dependencies where built - gcc can do dependency creation rather than the old school makedepends tool.

I suspect Turbo C is similar to Code Blocks and I used it only during my first C class. The compiler and all help files fit onto a single 1.44 MB floppy. ;)  Learned C++ using Turbo C++, which also fit onto a single 1.44 MB floppy - the help files didn't fit. It was a different time. Those are MS-Dos programs, BTW. This was before Windows and before I'd ever touched a Unix system and before Linux was started. ;)

---

