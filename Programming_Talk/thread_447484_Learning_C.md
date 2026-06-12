---
title: "Learning C"
date: 2007-05-18
forum: Programming Talk
---

### Post by ceeg on 2007-05-18
I've read my way mostly through K&R and will continue until I finish it. What is reccomended reading for someone who has finished K&R?

I'd like to get a bit into writing apps that communicate over TCP sockets, following that book, so reccomend me a lightweight book on sockets programming. (on linux)

---

### Post by moma on 2007-05-18
Visit my [COLOR="SeaGreen"]opportunities[/COLOR] page: [http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)
and follow the link to "**[COLOR="DarkOrchid"]Beej's guides...[/COLOR]**".  There you will find a good manual of network programming.

// moma

---

### Post by gradedcheese on 2007-05-18
truly light weight reference: :)

```

sudo apt-get install manpages-dev manpages-posix manpages-posix-dev

man socket
man setsockopt
man select
man poll

```

(and so on for open(), close(), read(), write() ...)

---

### Post by slavik on 2007-05-18
Understanding Unix/Linux System Programming by Bruce Molay. :)

---

### Post by RedSquirrel on 2007-05-18
> **moma said:**
> Visit my [COLOR=SeaGreen]opportunities[/COLOR] page: [http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)
and follow the link to "**[COLOR=DarkOrchid]Beej's guides...[/COLOR]**".  There you will find a good manual of network programming.

// moma


++

Beej's guide is good and free.

[http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/)

EDIT:

Here is the intended audience for that document:

> **1.1. Audience**

   This document has been written as a tutorial, not a reference.  It is probably at its best when read by individuals who are just starting out with socket programming and are looking for a foothold.  It is certainly not the *complete* guide to sockets programming, by any means.
  Hopefully, though, it'll be just enough for those man pages to start making sense... :-)


---

### Post by seamless on 2007-05-18
It's not exactly light weight but [Unix Network Programming]("http://www.amazon.com/Unix-Network-Programming-Vol-Networking/dp/0131411551/ref=pd_bbs_sr_1/102-8708861-5773727?ie=UTF8&s=books&qid=1179541767&sr=8-1") by the illustrious Stevens.

---

### Post by ricrac on 2007-05-18
Any and all by Richard Stevens

All sorts of tutorials and books on the web, check safari free oreilly books online.  Here's a quick link found...
[http://www.uwo.ca/its/doc/courses/notes/socket/](http://www.uwo.ca/its/doc/courses/notes/socket/)

My recommendation is to write an Apache Module.  This will introduce you to many advanced concepts with working examples.  Web servers serving static content are fairly simple to understand.  Once you have a module now write a simple web server.  It's easier than you'd think, can be done during a one hour class.  
After this you'll have a useful module for Apache and a simple framework to compare against the "real deal".  

The Apache Modules Book by Nick Kew

Once you get the hang of it you can look at lighttpd, thttpd, boa and other "smaller" web servers to compare programming methods,  forked processes, threads, shared memory, locks, etc.

It's much easier to have a working example codebase to start from when you're learning. Web servers have had lot's of peer review so you'll be less apt to find "bad" programming practices. 
Web servers have public pressure to perform well, so you will also tend to get "efficient" code.

And the knowledge will be useful.  Knowing the internals of Apache will be useful, even if you never code for Apache again.

---

### Post by rplantz on 2007-05-19
I'm not very familiar with their treatment of sockets, but i like "Beginning Linux Programming" by Stones, Matthew, and Cox. And when I was still teaching, my students also liked it. Lots of practical examples.

---

