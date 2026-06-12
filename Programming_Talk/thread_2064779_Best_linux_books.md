---
title: "Best linux books"
date: 2012-09-30
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-30
Hey,
I have been searching over the net for some good Linux books, and have got a few names.
Please can we pass pdf's/soft copies of some good Linux books here. 

I'm interested mainly in :
1)Linux File System
2)Bash
3)Programming in Linux
4)System calls
5)Signals, Interrupts
6)Something from an OS approach
7)For the dummies kind of approach
8 )Processes,Threads

No interested(yet) in :
1)Kernel
2)Shell scripting
3)Linux Commands
4)Device Drivers
5)System Administration
6)Linux hacks
7)Network Programming
8 )Socket Programming

Thanks. :)
PS : Would be great if you could post soft copies/links to soft copies here. If not, please post names of good books for beginners.

---

### Post by Majorix on 2012-09-30
I don't think it is legal passing pdf's of copyrighted material, unless the author himself released it for free.

---

### Post by Lars Noodén on 2012-09-30
What kind of programming?  It's a broad topic.  There are a lot of tools that are written in perl, so that would be one guess.  Here is one book on perl:
[http://onyxneon.com/books/modern_perl/](http://onyxneon.com/books/modern_perl/)

---

### Post by IAMTubby on 2012-09-30
> **Lars Noodén said:**
> What kind of programming?  It's a broad topic.  There are a lot of tools that are written in perl, so that would be one guess.  Here is one book on perl:
[http://onyxneon.com/books/modern_perl/](http://onyxneon.com/books/modern_perl/)
Thanks Lars, I'll put it to use ?
How about something in C ?

---

### Post by Lars Noodén on 2012-09-30
There's a rather good wikibook on C, if you need it at the beginning level:
[https://en.wikibooks.org/wiki/C_Programming](https://en.wikibooks.org/wiki/C_Programming)

C is out of my league so I'm not sure of the advanced resources.  However, it is what you need if you intend to work with drivers, the kernel, networking or filesystems.

---

### Post by IAMTubby on 2012-09-30
Guys, please keep the posts coming. 
But here is some useful info from my side

[http://ubuntuforums.org/showthread.php?t=1956546&highlight=linux+books](http://ubuntuforums.org/showthread.php?t=1956546&highlight=linux+books)

Let's make this thread into a one-stop shop for other newbies if possible.

I shall post more links if I find any.

Thanks.

---

### Post by Bachstelze on 2012-09-30
It sounds like you are really confused and what you need is a general book on operating systems. Look at Tanenbaum and/or Silberschatz et al.

---

### Post by IAMTubby on 2012-09-30
Bachstelze,
:). Yes, I am confused. But I want a book on Linux OS, not a general book on OS concepts.
I think I'll pick one of the books from the links mentioned above.

But do tell me your pick, shall give special preferance to it when I decide what to buy.

Thanks.

---

### Post by Lars Noodén on 2012-09-30
I'd recommend borrowing the OS books from the local college library instead.  They're not exactly inexpensive.

---

### Post by ofnuts on 2012-09-30
> **IAMTubby said:**
> 
I'm interested mainly in :
2)Bash

No interested(yet) in :
2)Shell scripting
3)Linux Commands


:confused::confused::confused:

---

### Post by IAMTubby on 2012-09-30
> **ofnuts said:**
> :confused::confused::confused:
ofnuts :)
I meant, getting to know how the bash works. 
Since, we have touched the topic, can I ask something related.

Is it possible to write something which sits over the bash/ monitoring the bash. Eg, Say the Bash-monitoring program should have some logic like,

```

if(I enter gedot in bash)
 execve(gedit);

```

Or should this logic be added to the bash code ?

Thanks.

---

### Post by trent.josephsen on 2012-09-30
Everything is possible, but not everything is beneficial.

Edit -- on re-reading in the morning, this sounds a bit... pretentious. Sorry if it came across that way. I wasn't trying to say anything deep and profound, just observe that while you can conceptually do anything you can precisely describe, not everything you can do is a good idea. I should have said something more like, "You could do it either way, but there's probably some way of achieving your real goal that doesn't ruin user expectations."

I already said something to this effect in your other thread, but you still haven't described what the problem is you're trying to solve.

---

### Post by lisati on 2012-10-01
What would a thread about Linux books be on Ubuntu forums without mention of [Ubuntu Unleashed]("http://ubuntuunleashed.com/")?

---

### Post by IAMTubby on 2012-10-01
> **trent.josephsen said:**
> Everything is possible, but not everything is beneficial.
Sir, but would you be able to tell me how to go about it ?
Maybe not for the benefit part, but I would like to learn. 
My teacher says that bash is a very important part of Linux and understanding it is a good first step.

Thanks.

---

### Post by Lars Noodén on 2012-10-01
But inherent in bash are 2)Shell scripting and 3)Linux Commands because if you are using bash, you are definitely using linux's programs and in effect writing one-line shells scripts.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

For basic bash and shell scripting you only need to know about a few programs and how to pipe and redirect.

```

dpkg -l > /tmp/packages.txt; # redirect
less /tmp/packages.txt

apt-cache search lib | sort | less;  # pipe

```

---

### Post by trent.josephsen on 2012-10-01
> **IAMTubby said:**
> Sir, but would you be able to tell me how to go about it ?
Maybe not for the benefit part, but I would like to learn. 
My teacher says that bash is a very important part of Linux and understanding it is a good first step.

Thanks.
See my edit.

If the idea is to add a feature to the shell, you should probably write a patch for the shell. It would be a bit challenging.

---

### Post by IAMTubby on 2012-10-01
> **trent.josephsen said:**
> See my edit.

If the idea is to add a feature to the shell, you should probably write a patch for the shell. It would be a bit challenging.
Just to get an overview, so where do I start from ? The bash code found in [http://ftp.gnu.org/gnu/bash/]("http://ftp.gnu.org/gnu/bash/")? or is there another way to write patches for the shell ? (Like to write a mobile application, you don't use the phone's firmware code, You have other ways of writing an application)

Thanks.

---

### Post by trent.josephsen on 2012-10-01
Yes, pretty much. The code is the bottom line, if you want to patch it to add a feature you're going to need to edit it directly.

I wouldn't start with bash, though. I'd try one of the less featureful shells and see if I could make it happen with one of those first. Maybe dash or busybox.

---

### Post by Stovey on 2012-10-01
> **lisati said:**
> What would a thread about Linux books be on Ubuntu forums without mention of [Ubuntu Unleashed]("http://ubuntuunleashed.com/")?

Hi.  I own this book and I didn't really like it.  I would've preferred something that gave a broad introduction to the operating system in perhaps 400 pages or less.  I found this book to be far too long, and covered way more ground that I was interested in.  The style doesn't really suit my style of learning - it is quite "dry".  Many of the examples or screen shots were outdated or no longer applicable.

For BASH, I found O'Reillly's "Learning the BASH Shell" to be pretty good.  Though for someone just wanting to learn the CLI it's probably a little too in depth.

---

### Post by IAMTubby on 2012-10-01
> **Stovey said:**
> 
For BASH, I found O'Reillly's "Learning the BASH Shell" to be pretty good.  Though for someone just wanting to learn the CLI it's probably a little too in depth.
Stovey, O'Reillly's "Learning the BASH Shell". Briefly, what are it's contents ?
Does it talk about how the bash is implemented ?

I want a book that says how the bash is implemented, something which I can read and be in a position to write some changes to the bash/write my own shell.

Thanks.

---

### Post by IAMTubby on 2012-10-01
> **Stovey said:**
> 
For BASH, I found O'Reillly's "Learning the BASH Shell" to be pretty good.  Though for someone just wanting to learn the CLI it's probably a little too in depth.
Hope the book's good, just ordered it on amazon :p :)

---

### Post by Stovey on 2012-10-01
> **IAMTubby said:**
> Stovey, O'Reillly's "Learning the BASH Shell". Briefly, what are it's contents ?
Does it talk about how the bash is implemented ?

I want a book that says how the bash is implemented, something which I can read and be in a position to write some changes to the bash/write my own shell.

Thanks.

It is mostly about BASH scripting.  It starts off by explaining the concept of a shell, then it walks you through the syntax of the language.  It gives example scripts, and is somewhat progressive, building on earlier concepts.

I don't remember anything about how it is implemented, or if it will help write a shell.  I hope you enjoy it anyhow.

---

### Post by 1clue on 2012-10-01
My personal experience is years out of date.

Back when I learned this, (in the late 80's and early 90's for UNIX) the books were the only way.  For years after that, books ruled.  As of 15 years ago, the O'Reilly publisher was outstanding for its usefulness and was the only publisher I could send somebody out to buy a book about some UNIX or networking topic and expect universally good results when they came back.  Every other publisher I needed to spend time thumbing through the book before buying it.

Today I'm not so sure I'd rely so much on the books.  I have literal bookshelves full of reference books, sometimes in multiple revisions.  I still use them every now and then, but more and more the relevant information is more easily found on the net.

I know O'Reilly is still around, and I know that some of their books are freely available as PDFs right from the publisher.

I think you should consider online sources for your research.  GNU has some excellent online reference.  If you see a lot of references to a book, then consider buying the book.  For recommendations you should pay attention to recommendations from forum or mailing list members rather than a sales guy.

You're asking for general reference, if you have something specific to ask for then you'll get some specific suggestions.

Good luck and have fun.

---

### Post by IAMTubby on 2012-10-01
> **1clue said:**
> My personal experience is years out of date.

Back when I learned this, (in the late 80's and early 90's for UNIX) the books were the only way.  For years after that, books ruled.  As of 15 years ago, the O'Reilly publisher was outstanding for its usefulness and was the only publisher I could send somebody out to buy a book about some UNIX or networking topic and expect universally good results when they came back.  Every other publisher I needed to spend time thumbing through the book before buying it.

Today I'm not so sure I'd rely so much on the books.  I have literal bookshelves full of reference books, sometimes in multiple revisions.  I still use them every now and then, but more and more the relevant information is more easily found on the net.

I know O'Reilly is still around, and I know that some of their books are freely available as PDFs right from the publisher.

I think you should consider online sources for your research.  GNU has some excellent online reference.  If you see a lot of references to a book, then consider buying the book.  For recommendations you should pay attention to recommendations from forum or mailing list members rather than a sales guy.

You're asking for general reference, if you have something specific to ask for then you'll get some specific suggestions.

Good luck and have fun.
Thanks a lot Sir for sharing your experience. Specifically, right now, I would like to know how the bash works, how it is implemented. 
Not so much about working on the bash, but I want to read some material that would help me write my own shell. Any suggestions for that ?

---

### Post by IAMTubby on 2012-10-02
> **trent.josephsen said:**
> Everything is possible, but not everything is beneficial.

Edit -- on re-reading in the morning, this sounds a bit... pretentious. Sorry if it came across that way. I wasn't trying to say anything deep and profound, just observe that while you can conceptually do anything you can precisely describe, not everything you can do is a good idea. I should have said something more like, "You could do it either way, but there's probably some way of achieving your real goal that doesn't ruin user expectations."
Hey, trent :). Just read the edit now. No, makes pefect sense.

> 
I already said something to this effect in your other thread, but you still haven't described what the problem is you're trying to solve.
**I actually have an application, for which I want to give argument from the bash, but I don't want to type out the entire argument, but type a few letters and then tab it out.** And then my application should take whatever few letters typed as argv[1] and then find out the other files starting with it. I have written the logic and it works well in a standalone application, because the whole tab key detection is done by my application(within/inside my application). But now I want to run each iteration of the program from the shell and want the bash to detect that I have pressed a tab, and pass control to my application with the few letters typed as argument. **I guess this needs some know-how, because unless you press the <Enter> key, the bash doesn't pass control/execve to my application, right ?**
This is what I'm trying to solve. As I mentioned, just read the edit now.

**So my question is, how do I get the bash to give control to my application, even if only <tab> is pressed and not <enter>**

Thanks.

---

### Post by 1clue on 2012-10-02
Or, alternately, have bash handle the tab completion and give your shell the entire finished product.

Bash handles tab completion by looking on the execution path.  3 letters + tab + tab gives you all the possible solutions beginning with those three letters.

FWIW you could have one main script which has multiple symbolic links to it (the different command names).  $0 is the name of the script the user typed.  So if you have foo as a main script, and bar as a symbolic link to it, your foo script can detect the $0 value (either 'foo' or 'bar') and handle things differently based on that.

---

### Post by ofnuts on 2012-10-02
> **IAMTubby said:**
> **I actually have an application, for which I want to give argument from the bash, but I don't want to type out the entire argument, but type a few letters and then tab it out.** And then my application should take whatever few letters typed as argv[1] and then find out the other files starting with it. If you replace [tab] by "*[enter]" this is how the shell works (it will find the files for you). You can replace the [tab] by a plain [enter] and have the logic in your code to find the matching files. Both solution remain coherent with current CLI usage.

Of course you can design your own interaction rules, but that will make you the sole user of the program because your program is going to be unusable by the rest of the world who learned other  keyboard conventions. And sooner or later you'll find it conflicts with the rest of your Linux usage, too.

---

### Post by IAMTubby on 2012-10-02
> **ofnuts said:**
> If you replace [tab] by "*[enter]" this is how the shell works (it will find the files for you). You can replace the [tab] by a plain [enter] and have the logic in your code to find the matching files. Both solution remain coherent with current CLI usage.

ofnuts, How do I replace the <tab> with <Enter>.
Is there some script for that ? And where do I add that code ?

Thanks.

---

### Post by ofnuts on 2012-10-04
> **IAMTubby said:**
> ofnuts, How do I replace the <tab> with <Enter>.
Is there some script for that ? And where do I add that code ?

Thanks.With you hand... it's the key at the other hand of the keyboard.

No Linux users expects [tab] to start execution in the command line. [tab] is a way to look at a list of files and think. For instance, if with a directory containing:

```

thefileIwanttoprocess1
thefileIwanttoprocess2
thefileIwanttoprocess3
thefileIwanttoleavealone1
thefileIwanttoleavealone2
thefileIwanttoleavealone3

```
A typical CLI user will do:

[LIST]
[*]"t[tab]" (file name is completed up to "thefileIwantto")
[*]"p[tab]" (file name is completed up to "thefileIwanttoprocess")
[*]"*[enter] (application processes 3 files)
[/LIST]
With your interaction model, you will take the person by surprise and start processing all the files beginning with "t".

---

