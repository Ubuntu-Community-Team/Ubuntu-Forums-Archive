---
title: "c++ helps. sockets"
date: 2007-07-26
forum: Programming Talk
---

### Post by t3hi3x on 2007-07-26
i'm racking my brain here. 

i'm an old vb programmer and i'm learning c++ in linux.

i have a program that is written in vb (server and client). i am using winsock in the vb program to communicate between the two programs. and i want to port the client to linux and leave the server running in windows. basically i need to uses a sockets library to communicate with it. i have a basic amount of c++ programming down. this is a completely command line driven program so that it can be easily ported to another archetecture than x86.

basically all the stuff i am finding online is useless,and i wanted to know if anyone knew where  some decent sockets tutorials for linux. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
t3hi3x - alex
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
We must be the change we wish to see - Ghandi

---

### Post by Geekkit on 2007-07-26
Uhhh, you want to port the client in VB to Linux? Your post does not make clear what exactly you are trying to build - too vague. From what I understand it doesn't sound like you can do what you're proposing. From a broader perspective I would highly recommend that you allow the doctors to pull the plug and let VB give up the ghost - it's not coming out of the coma, sorry. M$ has of course replaced VB with C# and/or .NET. The good news is that C# is supported in the Linux world via the Mono project:

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

They have this spiffy environment which looks suspiciously like VS.NET so transition is quite painless:

[http://www.monodevelop.com/Main_Page](http://www.monodevelop.com/Main_Page)

IMHO will be more employable by jumping into C# instead of using VB. This statement holds whether you're in Linux or Windows - VB has simply passed away no matter what world you live in. Further more, C# has some incredibly convenient calls for IO/Networking and all that. Not only that but C# syntax is a lot more similar to C++ than VB is to C++ so your learning curve shouldn't be that steep.


> **t3hi3x said:**
> i'm racking my brain here. 

i'm an old vb programmer and i'm learning c++ in linux.

i have a program that is written in vb (server and client). i am using winsock in the vb program to communicate between the two programs. and i want to port the client to linux and leave the server running in windows. basically i need to uses a sockets library to communicate with it. i have a basic amount of c++ programming down. this is a completely command line driven program so that it can be easily ported to another archetecture than x86.

basically all the stuff i am finding online is useless,and i wanted to know if anyone knew where  some decent sockets tutorials for linux. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
t3hi3x - alex
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
We must be the change we wish to see - Ghandi

---

### Post by slavik on 2007-07-27
find a book written in C for Linux/Unix programming. :) (I doubt there will be a C++ version)

---

### Post by Ansible on 2007-07-27
The basic sockets interface is a set of C functions, rather than C++ classes.  There are lots of object oriented wrappers out there for sockets; wxWidgets has one I know.  I'd look for some code that already uses sockets, rolling your own could take some time.  If you download the wxWidgets source there is a sockets sample program there.  

Searching google revealed this sockets tutorial - I only scanned through it so I dont know if its any good:

[http://www.cs.rpi.edu/courses/sysprog/sockets/sock.html](http://www.cs.rpi.edu/courses/sysprog/sockets/sock.html)

The client that you speak of; is this a GUI program?  What GUI toolkit are you planning on using?  Perhaps it has some sockets stuff in it already that you can use.

---

### Post by the_unforgiven on 2007-07-27
The ubiquitous [Beej's Guide to network programming]("http://beej.us/guide/bgnet/") is really good - small, concise and effective ;)
However, that explains the socket API in C.
I found these interesting links for C++:
[http://www.cs.wustl.edu/~schmidt/ACE.html](http://www.cs.wustl.edu/~schmidt/ACE.html) - The ACE toolkit
[http://linuxgazette.net/issue74/tougher.html](http://linuxgazette.net/issue74/tougher.html) - simple server/client implementation by writing wrapper classes on top of the C sockets API (filelist in Section 4.1)
[http://www.alhem.net/Sockets/](http://www.alhem.net/Sockets/) - Another GPLed Sockets library in C++.

HTH ;)

---

### Post by t3hi3x on 2007-07-27
thanks a lot for all the responses. to answer a few questions: 

1. by porting i meant reprogramming. i know it would be [impossible] to port a program from VB to linux. 

2. it's not a complicated client. it simply communicates with a server then connects to a music stream

3. i thought about running mono and c#, however, i feel it would be better suited to learn C/C++ so that it can be easily compiled in other architectures like a more embedded applications. we plan to move to a cheaper platform than x86.

4. i know i need to do some hardcore research i was mainly asking for some sites/book, etc. that you would recommend, that you have found useful. it appears what has been provided will furthur my c++ venture. i greatly appreciate it

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
t3hi3x - alex
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
We must be the change we wish to see - Ghandi

---

### Post by t3hi3x on 2007-07-28
> **Ansible said:**
> 

The client that you speak of; is this a GUI program?  What GUI toolkit are you planning on using?  Perhaps it has some sockets stuff in it already that you can use.

it is currently a gui program (it's vb lol), but it can run, and i would prefer to run all in command. this allows a light version to run, and i want to run it on a box that doesnt have an xserver.


this c++ thing is tough for me. i have a decent understand of the workings of a programming, but going from vb to a decent leveled language is tough. i am learning though, and it's mainly a deal with advanced programming. the biggest being me using ocx type things in vb. i know this is done by classes and headers in c++, but i guess its all learning.

---

### Post by the_unforgiven on 2007-07-28
> **t3hi3x said:**
> it is currently a gui program (it's vb lol), but it can run, and i would prefer to run all in command. this allows a light version to run, and i want to run it on a box that doesnt have an xserver.


this c++ thing is tough for me. i have a decent understand of the workings of a programming, but going from vb to a decent leveled language is tough. i am learning though, and it's mainly a deal with advanced programming. the biggest being me using ocx type things in vb. i know this is done by classes and headers in c++, but i guess its all learning.
Take it slowly, C++ can be tough even for the experienced programmers ;)

---

### Post by t3hi3x on 2007-07-29
cool. i am actually sending tcp packets from c++ linux to a vb server in windows, and it is working decently well. need to figure out why its doing this though:

```
...      std::string tosendbefore;
      std::string tosendnow;
      try
	{
	  std::cin >> tosendbefore;
	  tosendnow = tosendbefore;
	  std::cout << tosendnow << " \n";
	  client_socket << tosendnow;...
```

when i type more than one worth of string it returns only the first word. this is even if itype the "" in there. i dont understand...is there something i dont understand about cin?

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
t3hi3x - alex
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
We must be the change we wish to see - Ghandi

---

### Post by Ansible on 2007-07-29
When you use the '>>' operator with a std::string it reads until it hits whitespace, then stops.  So you only get the first word.  That works well if you want to read the input in word-by-word.  operator>> is overloaded for doubles and ints also, so if there was a series of numbers you could read them in individually.  

In your case you may want to read until you hit '\n' and then send a line of input at once, or if its a file you might want to send the whole thing.  Here's a web page I found that might be helpful:

[http://www.cplusplus.com/reference/iostream/istream/get.html](http://www.cplusplus.com/reference/iostream/istream/get.html)

---

