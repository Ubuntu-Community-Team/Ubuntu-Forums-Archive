---
title: "shell programming book?"
date: 2008-12-31
forum: Programming Talk
---

### Post by abhilashm86 on 2008-12-31
well i am a engineering student,i wanted to learn shell programming in detail,so can anyone suggest a book which is user friendly and has a gud number of programs,then i just know c and c++ programing,now i'm learning python,u can also give lonks to free download of the book.
I also want to know advantages of learning shell programing over others like python,c,etc,java.........

---

### Post by soluphobe on 2008-12-31
*I assume you're talking about bash*

Well, I picked up ["Learning the Bash shell" 3rd Edition]("http://oreilly.com/catalog/9780596009656/index.html").  It's by O'Reilly publishing, which is always good.  It looks at both the shell itself (with lots of focus on built-in methods) and writing scripts, though I didn't look too much at the script part.  I mainly wanted to learn the shell aspect, and I've forgotten much of what I don't use.  I think they have downloads of earlier editions, and I know you can get ebooks if you sign up for their system, but I like the dead tree (plus, LCD is pretty but hard to read for hours).

As to advantages of shell, it depends.  Windows Batch programming is like beating yourself in the head, but Bash is pretty high level.  I don't think it has much features (it has if, while, etc, but no oop, threading, etc), but it's fast, and I ended up using it for a lot.  I wouldn't program an actual application in it (though I hear rumors there are people who write massive simulations and logic routines in it) - It's mainly for doing repetitive things in Linux quickly and without a compiler.

I may be mistaken about features - I didn't look that heavily into the scripting.

---

### Post by stevescripts on 2008-12-31
I like this for an on-line reference: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

In some cases shell scripts can be extremely concise and highly useful (there are many examples in this forum)

Hope this helps a bit.

Steve

---

### Post by NathanB on 2008-12-31
> **abhilashm86 said:**
> well i am a engineering student,i wanted to learn shell programming in detail,so can anyone suggest

Which shell?  At least a half-dozen shell interpreters are available in L'unix land.  Some people have their reasons for preferring the 'csh' shell, for instance.  GNU/Linux installs with 'bash' as the default; you can change this with a minor edit of the '.bashrc' file in your home directory.

>  a book which is user friendly and has a gud number of programs,then i just know c and c++ programing,now i'm learning python,u can also give lonks to free download of the book.

No need for a book when there are plenty of on-line resources:

[http://www.linux.org/docs/ldp/howto/Bash-Prog-Intro-HOWTO.html](http://www.linux.org/docs/ldp/howto/Bash-Prog-Intro-HOWTO.html)
[http://www.linux.org/docs/ldp/howto/Bash-Prompt-HOWTO/index.html](http://www.linux.org/docs/ldp/howto/Bash-Prompt-HOWTO/index.html)
[http://www.linuxjournal.com/article/1299](http://www.linuxjournal.com/article/1299)
[http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity](http://www.linuxjournal.com/content/make-your-scripts-user-friendly-zenity)
[http://www.linuxjournal.com/article/9975](http://www.linuxjournal.com/article/9975)
[http://www.calpoly.edu/~rasplund/script.html](http://www.calpoly.edu/~rasplund/script.html)
[http://www.injunea.demon.co.uk/pages/page203.htm](http://www.injunea.demon.co.uk/pages/page203.htm)
[http://www.dartmouth.edu/~rc/classes/ksh/print_pages.shtml](http://www.dartmouth.edu/~rc/classes/ksh/print_pages.shtml)

> I also want to know advantages of learning shell programing over others like python,c,etc,java.........

Shell scripts are primarily the bailiwick of systems administrators.

One developer-related usage is for writing code-generating and code-testing tools.  However, Python can perform that task just as easily.

---

### Post by aranke on 2009-01-01
I agree with soluphobe.

---

### Post by abhilashm86 on 2009-01-01
yea friends,i'm talking about BASH shell,thanks 4r those stuff,i'll start working on it..........

---

