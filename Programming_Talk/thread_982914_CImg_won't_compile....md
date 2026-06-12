---
title: "CImg won't compile..."
date: 2008-11-15
forum: Programming Talk
---

### Post by benjorino on 2008-11-15
Hi,

I am new to Ubuntu, C++ and this forum... so please bear with me!

Basically, whenever I include CImg.h into any project, I get loads of errors when I compile, and I am at a loss as to how to resolve this.
I have tried various IDE's (geany, code::blocks, monodevelop, anjuta) to see if that would solve the problem... with no luck. Google searching and searching this forum has not provided me with a solution that worked/ I understood...

On the CImg site, under 'how to compile', I found:

# g++ (Linux version) : Use the following command to compile a CImg-based program with g++, on Linux :

  g++ -o hello_word.exe hello_world.cpp -O2 -L/usr/X11R6/lib -lm -lpthread -lX11

But this makes little sense to me.

Any ideas?
I have only a couple of weeks to familiarise myself with CImg, and I need to work out how to get the damn thing to compile before I can progress!

Thanks for your time,
Ben

---

### Post by WW on 2008-11-15
Hi Benjorino,

I have a couple suggestions:
[list]
[*] Show us the "loads of errors" that you get when you compile.  It might be a lot of stuff, but go ahead, cut-and-paste, and put it in a post.  Without seeing the errors, we can only guess what the problem might be--although some folks here are pretty good at that.  With the errors messages, someone can usually identify the cause of the problem very quickly.
[*] You only mention trying to use IDEs.  Since they are all a little different, it would be easier for us (for me, anyway) to help you if you could debug this problem by first learning how to compile a C++ program at the command line in a terminal.  If you have not done that before, check out this thread: [FAQ: Compiling your first C or C++ programs](http://ubuntuforums.org/showthread.php?t=689635).
With any editor you like, you should be able to create a really simple "Hello, world!" program, and then, in a terminal, use the g++ command to compile it.  Once you are familiar with that, the instructions provided by the CImg site on 'how to compile' will make more sense. The problem will probably turn out to be one of adding the correct options to the g++ command.  Once *that* is figured out, you can go back to your favorite IDE and configure it to set the options.
[/list]

---

### Post by benjorino on 2008-11-16
Thank you! I did exactly as you suggested in the second bullet point, and its compiling all the example code from the CImg site without any errors now.
Thanks again,
Ben

---

