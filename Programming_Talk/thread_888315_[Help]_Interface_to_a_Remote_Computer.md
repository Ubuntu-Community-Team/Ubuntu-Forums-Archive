---
title: "[Help] Interface to a Remote Computer"
date: 2008-08-13
forum: Programming Talk
---

### Post by loganwm on 2008-08-13
Before I actually start work on what I want to do I wanted to lay out the basic theory and see how I can manage it.

Basically I'm doing the following:

-The program is console based entirely.

-An instance of the program should be run on one computer (for all intents and purposes: "HOST")

-An instance of the program should be run on another remote computer (for all intents and purposes: "REMOTE")

-Both instances are the same program, but told to operate in a different manner.

-HOST should operate under the ability to receive and send data outside of the network to the REMOTE.

-REMOTE sends text strings to HOST to be processed as commands and HOST replies with the resulting content.

-There will be two-way communication between the instances of the program.



Just to show the layout of what I'm doing in real application:
Instance "JACK" is HOST.
Instance "JILL" is REMOTE.

JILL>>"access '/home/file.txt'">>JACK

JACK>>contents of the accessed file>>JILL

JILL>>"what time is it?">>JACK

JACK>>current time on JACK's terminal>>JILL


So how do I accomplish sending the string data, as well as data of a larger structure? (ex: a file contents)

I have absolutely no experience in the internals of network interaction in C programming.

It may sound a bit foolish, but I'm doing this mainly for the learning and the utility aspect of it, but also screwing around with the concept of very very simple "AI" communication for funsies.

---

### Post by henchman on 2008-08-13
Hei!

try this socket tutorial, it's a bit long, but after reading it, you know everything:

[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html")

---

### Post by Pyro.699 on 2008-08-13
I too am quite interested in this project, there are some applications avaliable to do this, but few are command line based (putty comes to mind), but having an application that could do this would be quite interesting to see done. May i ask what language your using to write this in?

---

### Post by stevescripts on 2008-08-13
loganwm - for a simple (tcl) example, see the tcler's wiki:

[http://wiki.tcl.tk/15539](http://wiki.tcl.tk/15539)

I am sure that Python and others provide similar simple client/server examples.

The wiki is searchable, and there are other client server examples there also.

Hope this helps a bit.

Steve

---

### Post by loganwm on 2008-08-13
> **Pyro.699 said:**
> I too am quite interested in this project, there are some applications avaliable to do this, but few are command line based (putty comes to mind), but having an application that could do this would be quite interesting to see done. May i ask what language your using to write this in?

I'm writing this in C (and if it becomes a necessity a bit of C++).

Right now I need to plan and design the simple text parser (I might work on something more complex in interpretation later, but I want quick results for now), the basic functions for sending and receiving data between the programs, and I might give the program a "personality"

It's more or less so you can have a "conversation" with a remote computer that can actually perform useful functions with simple instructions.

@Henchman:
Much thanks, I'll begin reading that after I grab a cub of soda and a notepad.

@stevescripts:
I can't imagine myself ever touching a scripting language again after using Lua for so long, you can call it a bias if you'd like, but I have really come to generalize scripting languages as too high level for me, I like the low level freedom of C/C++/Java/etc.

---

### Post by stevescripts on 2008-08-13
> **loganwm said:**
> 

@stevescripts:
I can't imagine myself ever touching a scripting language again after using Lua for so long, you can call it a bias if you'd like, but I have really come to generalize scripting languages as too high level for me, I like the low level freedom of C/C++/Java/etc.

Well, it's your program, so whatever floats your boat ... ;)

Doing this in C (or C++) is of course, a good learning expierence.

At some point, I hope that you will learn that you will usually be a much
more productive programmer using higher level languages (and yes, we all
resort to stuff like C, and even assembly when necessary).

Just my $.02 - have fun!

Steve

---

### Post by loganwm on 2008-08-13
> **henchman said:**
> Hei!

try this socket tutorial, it's a bit long, but after reading it, you know everything:

[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html")

It mentions UNIX quite a bit in the tutorial, using the libraries and techniques mentioned in it, can it be ported to Windows easily?

---

### Post by era86 on 2008-08-13
With winsock, you should be able to implement this in windows fairly easy.  I would look into socket programming in C and try some simple tutorials as suggested before.

If you have trouble, I wrote a similar program I am willing to share.  Just PM me if you are interested and I can walk you through the code.

But do try to learn on your own first ;)

Goodluck

---

### Post by loganwm on 2008-08-14
> **era86 said:**
> With winsock, you should be able to implement this in windows fairly easy.  I would look into socket programming in C and try some simple tutorials as suggested before.

If you have trouble, I wrote a similar program I am willing to share.  Just PM me if you are interested and I can walk you through the code.

But do try to learn on your own first ;)

Goodluck

I PM'd you about the sample program already :)

To anyone else who reads this thread and feels like contributing I'd appreciate it if you could write up a few sample questions like the following to help me develop my text interpreter:

"What is the time?"
"What time is it?"
"Where is the library?"
"What programs are running?"
"Send me the file."
"Open the file."
"Where is the file?"

Anything along the lines of simple questions that I can use to build the word base. (Try different wordings as well if you can, go ahead, think outside the box)

---

### Post by loganwm on 2008-08-14
I've been screwing around with strtok() to split the string and store it in some form. BUT I'm having troubles.

I can't find a way to store the words from the sentence into some sort of array or such?

Help Appreciated..

---

