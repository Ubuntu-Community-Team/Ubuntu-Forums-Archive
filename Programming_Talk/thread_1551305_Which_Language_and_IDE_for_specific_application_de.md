---
title: "Which Language and IDE for specific application development?"
date: 2010-08-12
forum: Programming Talk
---

### Post by vfafou on 2010-08-12
Hello!
I'm using Linux (Ubuntu) since 2007. These old times I was using windows, I was writing applications in Visual Studio (VB6).
I'm very confused about Linux Languages and IDE's. I need to write a client-server application with database transactions (MySQL or PostgreSQL), serial RS232 communications and network sockets, but I don't know which is the best tool (IDE environment and Language) to use. Do you have any suggestion about a fast developing IDE with nice User Interface components and a powerful language supporting threads and CPU multicore use?
I don't want to use Java because I don't know what will be at the future. As well as, Swing will not be supported anymore, and as I said above, I want to have nice looking user interface.
I don't want to use Mono too, because it "smells" Microsoft and I don't like this idea!
 
Thank you in advance!

---

### Post by nebu on 2010-08-12
you could probably try eclipse.... it is one of the most extensible ides out there

u might also give thought to using plain old vim or maybe even emacs....
both of these have a bit of learning curve... but once u get to know them well... u would never migrate to anything else!

emacs(especially) and vim have their share of addons.... so once u install them, these mean text editors will probably be the best ides around!

---

### Post by worseisworser on 2010-08-12
> **vfafou said:**
> Hello!
I need to write a client-server application with database transactions (MySQL or PostgreSQL), serial RS232 communications and network sockets, but I don't know which is the best tool (IDE environment

Emacs+Slime ...

> **vfafou said:**
> 
 and Language)


... and Common Lisp.

* Postmodern for dealing with PostgreSQL.
* RS232; depending on what approach would make most sense I'd use CFFI to interface with some C library that handled the boring details here, or I'd use Linux "API" calls/methods directly.
* IOLib for networking, or perhaps just the native SBCL socket API if my needs where simple.


> **vfafou said:**
>  to use. Do you have any suggestion about a fast developing IDE with nice User Interface components

I'd probably create a web-based UI, but if I needed something desktop'y I'd go for Glade for quick layout etc. and I'd take a look at CL-GTK2.

..but really; why even bother; heck I'd even distribute Chrome/Chromium with my software bundle if I had to; that thing is way speedy and agile.


> **vfafou said:**
>  and a powerful language supporting threads and CPU multicore use?

Yeah, SBCL -- a Common Lisp implementation, has nice thread-support with "real" OS-level threads. It uses 1200% CPU on my 12 core machine -- so multicore is no problem; it'll make use of all resources if you need it. :)


> **vfafou said:**
> I don't want to use Java because I don't know what will be at the future.

Oh, I wouldn't worry about that; Java and the JDK is open source now; check out the OpenJDK.


> **vfafou said:**
>  As well as, Swing will not be supported anymore, 

Hm. I haven't heard anything about Swing going away. 

Well, that's it; I can only tell you what I would do or use.

---

### Post by vfafou on 2010-08-13
Thank you all for the answers...
What about Java or Python with GTK+ GUI? How difficult is the manipulation of GTK widgets with these languages and how difficult is e.g. the creation and filling of a datagrid with database data?

---

