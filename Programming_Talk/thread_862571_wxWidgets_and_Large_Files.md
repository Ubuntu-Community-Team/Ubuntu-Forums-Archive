---
title: "wxWidgets and Large Files"
date: 2008-07-17
forum: Programming Talk
---

### Post by era86 on 2008-07-17
Greetings!

I want to open a large file (>2g) and print it out in a text control, but the program hangs, then seg faults.  I'm thinking this is a memory issue...

Is there any solution to this?  Should I break up the file?  Would streams make this work?

Thanks in advance!

---

### Post by kknd on 2008-07-17
You can't print it all. Not all at the same time, unless you have lots of RAM.
To be show in the viewer, all the data must be in RAM, unless you reimplement it to lazy-load the data as you scroll on it.

Whats the purpose of showing 2gb of data at the same time?

---

### Post by Claus7 on 2008-07-17
Hello,

in case it is a memory issue you can find out easily by going to System->Administration->System Monitor and see what is going on with the memory while you are trying to open the file.

Now, (because I think that it has to do with memory issue) it's diffucult to avoid it. I tried, not once, to open a file far less the size of yours, yet big enough, and it took ages to my computer to open it. 

In case you want to see something in the beggining or in the end of a file, the head and tail commands should help you. As far as the wxWidgets is concerned I have no experience, yet if less and vi have such a problem I think that a graphic ennironment should have even more. 

What streams are I have no idea. You could break the file for example with awk. You could make a script and there put ifs so as to break the file to multiple ones depending on the line they have. For example form line 1 to 100 one file e.t.c.. Yet, these files are huge enough and I do not know how this will help you. I use less and have patience in order to see the contents of a huge file.

Regards!

---

### Post by era86 on 2008-07-17
> **kknd said:**
> You can't print it all. Not all at the same time, unless you have lots of RAM.
To be show in the viewer, all the data must be in RAM, unless you reimplement it to lazy-load the data as you scroll on it.

Whats the purpose of showing 2gb of data at the same time?

I was thinking of using threads to write the data out, but I'm guessing it still won't work due to memory issues.  I'll just have to see if I can do something different.

What is lazy-load?

I'm sorry I cannot disclose why I am doing this.  Just know that it involves a lot of data that many rely on ;)

Thank you for the response.

> **Claus7 said:**
> Hello,

in case it is a memory issue you can find out easily by going to System->Administration->System Monitor and see what is going on with the memory while you are trying to open the file.

Now, (because I think that it has to do with memory issue) it's diffucult to avoid it. I tried, not once, to open a file far less the size of yours, yet big enough, and it took ages to my computer to open it. 

In case you want to see something in the beggining or in the end of a file, the head and tail commands should help you. As far as the wxWidgets is concerned I have no experience, yet if less and vi have such a problem I think that a graphic ennironment should have even more. 

What streams are I have no idea. You could break the file for example with awk. You could make a script and there put ifs so as to break the file to multiple ones depending on the line they have. For example form line 1 to 100 one file e.t.c.. Yet, these files are huge enough and I do not know how this will help you. I use less and have patience in order to see the contents of a huge file.

Regards!

Thanks for the prompt response.  I am guessing this will not work since the machine I am using has 2g memory max.  Even if there was more, it would take way too long for my purposes.  I'll just have to find another solution.

---

### Post by cdekter on 2008-07-20
> **era86 said:**
> 
Thanks for the prompt response.  I am guessing this will not work since the machine I am using has 2g memory max.  Even if there was more, it would take way too long for my purposes.  I'll just have to find another solution.

Text controls such as the ones in wxWidgets have a limit on the amount of data they can contain, usually just a couple of megabytes. Special techniques are required for large files, and I doubt even professional text editors would be able to readily handle a file of the size you are talking about. In other words... it would be more trouble than it's worth.

---

### Post by Zugzwang on 2008-07-20
[LIST=1]
[*]If your program hangs and then segfaults when you open such a large file, it is likely that you don't check for error values/message/throw away exceptions/whatever. Fix this!
[*]Lazy loading is (part of) the way to go! There's a Wikipedia article on this: [http://en.wikipedia.org/wiki/Lazy_loading]("http://en.wikipedia.org/wiki/Lazy_loading"). It isn't helpful, however. The basic idea is as follows and is for example implemented i a lot of "large file hex editor":

At the start-up of the program you just check how large your data set is and then create a view onto the data with the respective scrolling bar. However, you only load the data that is currently visible on your (relatively) small view. Whenever the user scrolls, you again load the data in the viewport from the disk. Changes to the input are put into some buffer and applied when moving your view or at the point of closing the file.

This of course might cause some problems. If you are dealing with text files, then you don't know how long each line is, so you would have to create another temporary file telling your where each line starts (as example).

Basically, you are implementing the [Model-view-controller]("http://en.wikipedia.org/wiki/Model-view-controller") paradigm to give the impression to the user to be able to handle such big files.

Note that the whole thing is quite non-trivial and may cause some trouble even to experienced programmers. If each data line you are displaying has a fixed size, this is however not too hard. For Java, for example, there is a library to support/make easier such operations: [http://joafip.sourceforge.net/]("http://joafip.sourceforge.net/")

[/LIST]

---

