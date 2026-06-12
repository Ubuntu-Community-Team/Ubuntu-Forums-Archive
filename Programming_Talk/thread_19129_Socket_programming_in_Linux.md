---
title: "Socket programming in Linux??"
date: 2005-03-10
forum: Programming Talk
---

### Post by Kimm on 2005-03-10
can anyone provide me with a good tutorial on socket programming in linux?? Perhaps something that could also be compiled under Cygwin (if possible), I need to write some cind of application so that my mom and dad can communicate directly with my computer, like if dinners ready they just open a window and type that, then a little dialog pops upp and tells me dinner is ready...

I tried googeling and I did find one tutorial... it was realy wierd and didnt realy say anything so that didnt work...

Edit: oh, btw, I'm talking socket programming in C/C++ :razz:

---

### Post by cresonic on 2005-03-11
I know you are asking for a C/C++ resource here, but since no answer has been given I thought you might find this one interesting:

[http://carmelo.cs.byu.edu/python/](http://carmelo.cs.byu.edu/python/)

It's python, but IMHO what you need sounds like a python job. (And I don't know anything about C-socketing)

If you don't know python, I think you should take a look anyhow, it's really easy to learn, especially if you already are familiar with C/C++.

---

### Post by Viro on 2005-03-12
[QUOTE=Kimm]can anyone provide me with a good tutorial on socket programming in linux?? Perhaps something that could also be compiled under Cygwin (if possible), I need to write some cind of application so that my mom and dad can communicate directly with my computer, like if dinners ready they just open a window and type that, then a little dialog pops upp and tells me dinner is ready...

I tried googeling and I did find one tutorial... it was realy wierd and didnt realy say anything so that didnt work...

Edit: oh, btw, I'm talking socket programming in C/C++ :razz:[/QUOTE]
 I find it hard to belief that Google didn't turn up any results for socket programming :). In any case, Beej's tutorial is the one that got me started in Unix network programming some years ago. [http://www.ecst.csuchico.edu/~beej/guide/net/html/](http://www.ecst.csuchico.edu/~beej/guide/net/html/)

---

### Post by ynef on 2005-03-12
I came to this thread to suggest Beej's guide as well.

I've also found the [gnet socket programming library](http://www.gnetlibrary.org/) on the internet, and since it's a library it pretty much has to be easier to use than the system calls -- otherwise, there'd be no point to developing it.

The OP might want to give it a try.

---

