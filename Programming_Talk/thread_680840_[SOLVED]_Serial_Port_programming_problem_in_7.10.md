---
title: "[SOLVED] Serial Port programming problem in 7.10"
date: 2008-01-28
forum: Programming Talk
---

### Post by kherrera on 2008-01-28
Hello this is the problem:

I have to program something on C/C++ that sends a message from CPU A to CPU B on the serial RS-232 port. I want to say that I'm not a complete newbie, I have about one and a half year on Linux, and about 3 months on Ubuntu. On the past, I've achieved this goal, I used a library that follows the posix standards. 

My programs worked on SuSE 9.2, 9.3, 10 Enterprise, OpenSUSE 10.2 and debian, they even past versions of ubuntu, like Fiesty Fawn, on 32 and 64 architectures (x86-32, X86-64 and ARM9). The cables are also the same, and I'm sure that they still work because when I use minicom on Gutsy Gibbon they do it fine. 

The problem is that in Gutsy I can't make them work. To be more accurate, the problem is on the read function, because I can easily open the ports, when I pretend to receive a message, the program is abruptly terminated and a weird message appears:

Probably I/O

final notes:

YES, I'VE TRIED IT AS ROOT!.

THE CABLES ARE FINE

THE FORMAT IS ALSO ALIKE (JUST IN THE CASE IS 8N1 AT 9600)

A FRIEND OF MINE TRIED TO RE-READ THE POSIX STANDARD AND DID ANOTHER LIBRARY AND THE PROBLEM KEPT THE SAME! 

I TRIED ON DIFFERENT MACHINES WITH 7.10 AND THE PROBLEM PERSISTED TOO!

I don't know if the standards changed or what...
Can someone help me?

                                                                                Kevin H.

---

### Post by LaRoza on 2008-01-28
[color="red"]Moved to Programming Talk[/color]

---

### Post by stroyan on 2008-01-28
Use the strace command on your program to get a clearer indication of what system calls are being made and what results they return.

---

### Post by kherrera on 2008-01-29
Ok, the system call that seems to be the problem is when I try to use the read function, the way its implemented is like this:

**read( int fd, char* buf, int n);**

 where fd, is the file descriptor, buf is the buffer where I put the things that were transmited and n is the maximum size of the message. By the way  the exact phrase it prints out is 

**I/O Possible**

after that message the program ends abbruptly :confused:

everything before seems to do fine

---

### Post by PaulFr on 2008-01-30
Congratulations ! Your program has now received a SIGIO signal :-)
> SIGIO 	23,29,22 	Term 	I/O now possible (4.2BSD)Handle it appropriately.

---

### Post by kherrera on 2008-01-31
I don't get the last message, What does that mean?

---

### Post by foxylad on 2008-01-31
It means a SIGIO interrupt has been raised, and you need to provide a handler. Serial communications is asynchronous, and the best way of handling this is to use interrupts. So when data has arrived an interrupt is raised, and you attach a function to the interrupt to read teh data and do something with it. (Sorry if you know all this, I'm assumming you don't because you don't know what a signal (same as an interrupt) is.)

Your library may be doing all this for you, in which case it should be handling the SIGIO interrupt too. You'll need to read teh docs about interrupts and see what tehy say.

---

### Post by PaulFr on 2008-02-01
Apologies for my poor attempt at humor.

If you are using asynchronous serial I/O file descriptors (using fcntl), then SIGIO is the Linux way of letting you know (this is not in POSIX, but comes from BSD) that the file descriptor is ready for reading or writing. See **[http://www.gnu.org/software/libc/manual/html_node/Asynchronous-I_002fO-Signals.html](http://www.gnu.org/software/libc/manual/html_node/Asynchronous-I_002fO-Signals.html)** for a description.

See **[http://tldp.org/HOWTO/Serial-Programming-HOWTO/x115.html#AEN144](http://tldp.org/HOWTO/Serial-Programming-HOWTO/x115.html#AEN144)** for sample code for SIGIO handling.

Hope this helps.

---

### Post by kherrera on 2008-02-01
Thank you a lot, (both of the last messages), I can now solve this.

:guitar:

---

