---
title: "Command Line + OpenGL/SDL (C++)"
date: 2006-12-26
forum: Programming Talk
---

### Post by Verminox on 2006-12-26
I'm making a C++ program using OpenGL for 3D graphics, but I want to be able to interact with the user using a command line interface. 

I don't know if this is what is meant by Multi-Threading, because I havn't read much about it, but basically I want there to be two windows open at once:
1. The terminal window from where the app was started that will ask for inputs and output results/messages/exceptions.
2. The OpenGL/SDL window that displays the GFX.

Note that I must be able to communicate between the two processes. A user input in the terminal should be processed by the program, and effectively modify the GFX display. Similarly, any OpenGL/SDL exceptions, etc. should be reported back via the terminal.

How would I go around doing this?

---

### Post by slavik on 2006-12-26
umm, #include <iostream>

just make sure to check for input in the main loop ...

---

### Post by Verminox on 2006-12-26
That won't help. For example, if I am waiting for input at a certain stage, the program will pause till the input is obtained, and the OpenGL window will also freeze. I want both processes running simultaneously but at the same time sending signals from one process to the other and vice versa.

---

### Post by Zdravko on 2006-12-26
I think that you need threads. One thread will run the main (OpenGl) routine, and the other one - will wait for input at the console.
I am interested how will this look like in pthreads!

---

### Post by Verminox on 2006-12-26
That's exactly what I'm asking. How do I make a multi-threaded program in C++ without much of a hassle? I don't need a fancy API that uses multi-threading to optimize CPU cycles (or something like that I read)... I just need a quick way to manage two threads from one program....

What is pthreads?

---

### Post by hod139 on 2006-12-26
SDL_events can be multithreaded.  When you call SDL_Init, also add the flag SDL_INIT_EVENTTHREAD 
```

SDL_Init( SDL_FLAGS | SDL_INIT_EVENTTHREAD )

```
where SDL_FLAGS are whatever other flags you want.

You can then use the same event monitoring techniques found in ubuntu-gamedev examples.  [http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

---

### Post by slavik on 2006-12-26
yeah, then you want to use SDL threads and also, use events to communicate between the both threads

---

### Post by lnostdal on 2006-12-26
> **Verminox said:**
> That's exactly what I'm asking. How do I make a multi-threaded program in C++ without much of a hassle? I don't need a fancy API that uses multi-threading to optimize CPU cycles (or something like that I read)... I just need a quick way to manage two threads from one program....

What is pthreads?

[http://ubuntuforums.org/showthread.php?p=977932](http://ubuntuforums.org/showthread.php?p=977932)

edit: note the stuff i mention about how one compile/link code that uses pthreads ..

---

### Post by Verminox on 2006-12-27
lnostdal: Thanks, I'll look into pthreads...

hod139/slavik: SDL threads will allow me to make two SDL screens and run them simultaneously... what I want is one SDL screen at the side running along with the main app in the terminal that works with stdout and stdin (by default, SDL makes the std output write to a text file stdout.txt and similarly stderr.txt which I don't want)

---

### Post by slavik on 2006-12-27
you start the second thread for drawing and keep main for output ...

make sure to have a global 'bool done' variable.

---

