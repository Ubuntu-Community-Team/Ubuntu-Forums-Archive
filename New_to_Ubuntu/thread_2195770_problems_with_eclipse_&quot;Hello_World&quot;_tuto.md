---
title: "problems with eclipse &quot;Hello World&quot; tutorial"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by jjclonker on 2013-12-26
I installed eclipse for C/C++ programers so that I could learn C++ programing.

I started with the Eclipse "Hello World" tutorial. Everything was doing great untill I tried to run the "Hello World" program.

I got the following error:

```
Error starting process.
Exec_tty error:Cannot run program "/home/jj/workspace/Hello World/src/Hello World.cpp": Unknown reason
Exec_tty error:Cannot run program "/home/jj/workspace/Hello World/src/Hello World.cpp": Unknown reason
Exec_tty error:Cannot run program "/home/jj/workspace/Hello World/src/Hello World.cpp": Unknown reason
```

Sory for the pore disciption of the problem, but I had no idea where to start. :/

---

### Post by kajoky on 2013-12-26
It looks like you are trying to execute the source file, Hello World.cpp
You need to compile and link the source to get an executable Hello World
If you did the build all to compile and link, then the executable may be in
/home/jj/workspace/Hello World/bin/

---

### Post by jjclonker on 2013-12-27
I bet that I got in to big of a hury, Eclipse is a very complex program and I may have to install some dependencies for this to work I will study the Eclipse tutorial more thoughly and try again, if I run into the same or more problems then I will post them here.;)

---

### Post by squakie on 2013-12-27
kajorky is correct - notice the error messages all show it trying to execute the .cpp file - this is source code.  I think most of the tools out there are still using gcc (g++) for the actual compilation.  The default from that compile is normally a.out (if I remember correctly) unless you specify a name.  So, if you have actually run the compile, then look for a file called a.out in the appropriate folder.  Also, you normally have to change the file permissions to be executable - along the lines of chmod +x <filename>.

---

### Post by squakie on 2013-12-27
For some reason right now I can't get Eclipse to install via synaptic - it appears my ISP is having some sort of DNS problems.  At any rate, I wanted to show you what I was saying above actualling in action.  I first created the source using just the simple editor, then compiled it, then made it executable, then executed it:
```
dave@davePC:~$ cat helloworld.c
#include<stdio.h>

main()
{
    printf("\n\nHello World\n\n");


}

dave@davePC:~$ gcc helloworld.c
dave@davePC:~$ ls
a.out      Downloads          helloworld.c   OpenELEC  sues-media-center  VirtualBox VMs
Desktop    examples.desktop   helloworld.c~  Pictures  Templates          xbmc_crashlog-20131224_050538.log
Documents  for-media-centers  Music          Public    Videos             xbmc_crashlog-20131226_011945.log
dave@davePC:~$ chmod +x a.out
dave@davePC:~$ ./a.out


Hello World

dave@davePC:~$ 
```

You should be able to something similar.

Also, as long as you installed eclipse via apt-get or via synatpic package manager you should not have any dependency problems.  The program is so simple you should not have any path problems either I woouldn't think.

BTW - if you don't have synaptic package manager installed you should install it via sudo apt-get install synaptoc

---

### Post by squakie on 2013-12-28
I finally got Eclipse installed tonight.  After checlking it out, I personally wil stay with what works for me: CodeBlocks.  It is an IDE with the things I like best in an IDE - and I personally (it's just my opinion) can say I much prefer it over Eclipse - just my opinion only.

My personal suggestion, and others will have theirs as well, is to install codeblocks via synaptic package manager and try it - you may have better result and like it.  What ever you use, remember you must select the tools option to build or compile the code before trying to execute it.  Some IDEs will automatically do a build when you select run from the IDE - for what I've done in the past and for what I'm doing now I manage that on my own as my projects are just a bit larger than helloworld.

Just my opinion, just something you may want to try.

---

### Post by jjclonker on 2014-01-03
Thanks squakie I swiched to Code::Blocks it is way simpler (I like simple), but it is having problems building too LOL (just my luck).

Oh by the way is there a way to mark a tread closed instead of solved?

---

### Post by QIII on 2014-01-03
Yes, there is.  But only staff can do it.  ;)


Please just mark it solved.  Thanks.

---

### Post by jjclonker on 2014-01-03
Thanks QIII. :KS

---

