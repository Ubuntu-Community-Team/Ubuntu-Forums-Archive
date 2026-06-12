---
title: "Help with remote debugging gdb/ddd"
date: 2011-04-26
forum: Programming Talk
---

### Post by BkkBonanza on 2011-04-26
I'm trying to setup for remote debugging and need some input from somebody more experienced with doing this as I'm getting confusing results.

I have a program I want to run in a Ubuntu VBox guest and I want to debug it from the host. I have been able to do the basic steps of running the program under gdbserver on the guest and connect to it to debug from the host. eg.

(guest) gdbserver 192.168.56.3:9999 test
(host) gdb test

I have compiled the test program on both systems and have the source on both. When I start gdb I can debug the local program with no problems. When I try to debug the remote one with "target remote 192.168.56.3:9999 test" it does connect and work as well.

However, when I set a breakpoint it will never stop for it. eg. my test program is extremely simple, just a loop of output a string and input a char. I set a "break 10" to stop in the loop. But when I switch to the guest and enter a char it works as usual and never breaks. When debugged locally it does break of course.

If I use an "until 10" command it will run until I enter a char and then break. But it breaks at a weird address and seems to not know where it is. The "info source" command states that my test.cpp source is loaded but the debugger appears not to know where it has stopped. It cannot see local vars. and eg. I get this response to a step:

(gdb) step
Cannot find bounds of current function

Any ideas? I thought maybe there was differences in library versions linked against but ldd shows same version, though at different paths. The systems are slightly different Ubuntu versions lucid vs. maverick.

I can't really continue in setting up for a more complex situation until I van get basic break functionality in this simple case.

(yes, program is compiled with -g debug symbols on host)

---

### Post by dwhitney67 on 2011-04-26
The steps involved are:

On remote server (guest):
```

gdbserver addr:port ./app

```

On local server (host):
```

gdb ./app

gdb> target remote addr:port

gdb> break main

gdb> **continue**

gdb> next

...

```
Happy debugging!


P.S.  It should be noted that when you attach to the debugged process on the remote server, the process is suspended; hence the need to issue the command "continue".

---

### Post by BkkBonanza on 2011-04-26
Yes, I'm doing all that. 
But the problem is that any breakpoint is never stopped at. It is just ignored.

I can debug fine on either system alone but only have this issue when using "remote" to debug one from the other. I suspect it's shared libraries not matching but I'm unsure about that and was hoping maybe someone had seen this before.

---

### Post by dwhitney67 on 2011-04-26
Please provide an example of the "simple" program you are attempting to debug.  From the description offered earlier, it seems that it would be something along the lines of:
```

...

for (int i = 0; i < 10; ++i)
{
   char ch;

   std::cout << "Enter a char: ";
   std::cin  >> ch;
}

...

```

---

### Post by BkkBonanza on 2011-04-27
Even simpler. It's not the program that is a problem as I get the same results with real programs I have and that's why I made a simplest case to test.
eg.
```

#include <iostream>
using namespace std;
int main()
{
char ch;
while(ch != 'x') {
    cout << "Test Running" << endl; 
    cin >> ch;
    }
}

```

---

### Post by dwhitney67 on 2011-04-27
If you set the breakpoint in the middle of the while-loop, there's always the possibility it is never reached, because the condition fails.

Either initialize the variable 'ch' (to a value other than x), or use a do-while construct.

Also please confirm that you are not optimizing the code when you compile it.

---

### Post by BkkBonanza on 2011-04-27
I just wrote this quickly on screen here as an example. I can assure you it's not failing due to init. I run the loop over and over, entering keystrokes, with a breakpoint in the middle and it never breaks. You can stop trying to show how I'm using it wrong. I've used these tools quite extensively on a single system (without remote) for years. Many years. 

As stated it will break fine when debugging on the local system - on either local system, but not when using "target remote" mode. Using "until" it breaks into library code somewhere without any reference how to get back to my code. With "break" it sets the breakpoint but never stops at it. I'm expecting there is some sync problem between libraries on each system. I was hoping someone with specific knowledge of how that works could help out.

Definitely compiling without optimization. Have tried both -g and -gstabs with same results. I've even compiled with debugging on the remote even though it should work fine without symbols.

The code above is an example of a simple test case. I'm actually debugging a multi-threaded fast-cgi cpp web back end application. I can debug it fine on the server by attaching to it after it's started by the process manager. However, I could never get it to break when using the remote feature. I stepped back and reduced it to a simple test to figure out what as happening.

---

