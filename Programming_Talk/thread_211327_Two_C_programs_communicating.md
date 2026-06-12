---
title: "Two C programs communicating"
date: 2006-07-08
forum: Programming Talk
---

### Post by richardhp on 2006-07-08
Ok - I am writing a C program but want the keep the user interface seperate from the main body of the program so that if i choose, i can switch between different GUI's etc.

At the moment I am using SDL to get started and have successfully built the window and have got a loop processing the message queue. I want to include in that message queue something that will handle data from the main program and also something that will send data back to the main program for processing.

I was considering using a socket on both programs and communicating between the two using that. However, when the "recv" method is used it sits and waits for input which would be bad since the UI would hang until some data arrived. Can I set an interrupt so that the recv method will time out after 0.1 seconds or something or can I have the main program pass messages to the SDL interface?

---

### Post by nagilum on 2006-07-08
The standard way of receiving data from sockets etc. is using the select system call. It can either wait indefinitely for data or you can give it a timeout after which it stops blocking. Although directly using such things in the message loop of the GUI is not good, better use threads for this. Putting the recv-part into a threads will make your GUI not block at all and you can get rid of the timeout stuff.

---

### Post by Zdravko on 2006-07-08
I think that using threads here will be a better sollution to the problem.

---

### Post by supirman on 2006-07-08
> **richardhp said:**
> 

I was considering using a socket on both programs and communicating between the two using that. However, when the "recv" method is used it sits and waits for input which would be bad since the UI would hang until some data arrived. Can I set an interrupt so that the recv method will time out after 0.1 seconds or something or can I have the main program pass messages to the SDL interface?

use select().  Here is some good information for you: [http://www.beej.us/guide/bgnet/output/htmlsingle/bgnet.html#blocking](http://www.beej.us/guide/bgnet/output/htmlsingle/bgnet.html#blocking)

---

### Post by LordHunter317 on 2006-07-08
select() won't work here, because you can't make X11 work asynchronously.  You have to use a seperate thread for X11 operations, and you have to write your code such that all GUI operations occur on that thread.

Anyway, this is bad program design.  Unless you want multiple interfaces to connect to your application at the same time (i.e., console and an X11 GUI) there's no need or desire to seperate out the main program into a seperate process.  Even then, you'd want to probably use D-BUS, DCOM, or something similiar instead.

Better is to design your application logic so it is GUI-independent.  Then, just code whatever GUIs you want into the application.

---

### Post by richardhp on 2006-07-08
Ok thanks. I am trying to make it GUI independant but maybe I am going about it the wrong way.

I will look into threads/select and see which works best.

Thanks for the help

---

### Post by thumper on 2006-07-08
It sounds to me like you are over complicating the problem.

You can have GUI independant back end code and have it compiled to a library that is then used by which ever GUI you want.

You even have the choice of using a static library or a shared library.  This is the normal way to break stuff up.

---

