---
title: "errrr C++"
date: 2008-04-02
forum: Programming Talk
---

### Post by t3hi3x on 2008-04-02
So me an C++ are having this love-hate relationship. I love it, but sometimes it gives me hell.

I'm working on a program with more than one cpp file so I need to make more than one .o file on compile.

I want to declare some global variables, and I'm doing that in an h file, but it calls a multiple declaration error.

What is a good practice for using global variables?

---

### Post by bfallik on 2008-04-02
> **t3hi3x said:**
> So me an C++ are having this love-hate relationship. I love it, but sometimes it gives me hell.

I'm working on a program with more than one cpp file so I need to make more than one .o file on compile.

I want to declare some global variables, and I'm doing that in an h file, but it calls a multiple declaration error.

What is a good practice for using global variables?

The best practice is not to use global variables...

---

### Post by LaRoza on 2008-04-02
See keyword "extern", I assume it is in C++.

---

### Post by dwhitney67 on 2008-04-02
> **LaRoza said:**
> See keyword "extern", I assume it is in C++.
Wrong, 'bfallik' had/has the correct response... "do not use global variables".  Data (variables) should be encapsulated within classes, and as a last resort, within namespaces.

---

### Post by LaRoza on 2008-04-02
> **dwhitney67 said:**
> Wrong, 'bfallik' had/has the correct response... "do not use global variables".  Data (variables) should be encapsulated within classes, and as a last resort, within namespaces.

C++ doesn't have the extern declaration? I haven't used C++ in a while, but I could have sworn it was there.

I will have to read up on that, thanks, I didn't know C++ enforced it.

**Edit:**
extern declarations are allowed: [http://www.cppreference.com/keywords/index.html](http://www.cppreference.com/keywords/index.html)

I tested it with g++ and it works.

---

### Post by dwhitney67 on 2008-04-02
Yes, the "extern" is available in C++.  But declaring global variables is considered poor OOD, or as some people have mentioned, "evil".

Write nonsense code for all I care... It keeps me employed till the day I retire.

Cheers!

---

### Post by LaRoza on 2008-04-02
> **dwhitney67 said:**
> Yes, the "extern" is available in C++.  But declaring global variables is considered poor OOD, or as some people have mentioned, "evil".

Write nonsense code for all I care... It keeps me employed till the day I retire.

Cheers!

Yes, it is considered poor OOD, but that wasn't the OP's question. The OP directly asks about declaring global variables in another file, I assume that a lecture on global variables isn't what the OP wants. 

What I stated wasn't "wrong" as you said, it was actually 100% correct.

If you wanted to point out it was poor practice, fine, but I would appreciate it if you didn't say I was wrong when I was not. 

[quote="OP"]
What is a good practice for using global variables?
[/quote]

As stated, global variables are not usually a good practice. I assume you have a reason for it, as you asked. A good practice would be to keep them to an absolute minimum and to elimate them if possible. If you aren't going to be changing this value, you can make it a constant, which can be global safely.

---

### Post by heikaman on 2008-04-02
i know that global variables are bad practice, but i always wondered , if they are so "evil" how come the std is full of global variables ? like errno ?:confused:

---

### Post by pedro_orange on 2008-04-02
I wouldn't consider Global Variables "evil" - the only problem with them is that you cannot encapsulate them within a class to restrict access to it. You can use global variables all you want, its your program. But there is usually a better/safer way to do things than to resort to globals. It all depends on what you're making.

I may be wrong....but I presume:

The namespace std needs to be accessed by loads of different things (within classes/fns/files), and therefore require project-wide access.

---

### Post by LaRoza on 2008-04-02
> **heikaman said:**
> i know that global variables are bad practice, but i always wondered , if they are so "evil" how come the std is full of global variables ? like errno ?:confused:

Aren't they constants?

(Can you change it?)

---

### Post by heikaman on 2008-04-02
> **LaRoza said:**
> Aren't they constants?

(Can you change it?)

maybe some are constants, but errno for example is not.
actually when a library function call sets errno you should save the errno before another call changes it. 

anyway i am sure there are good reasons why some variables in std are global, which means that it's okay "sometimes" to use global variables.:)

---

### Post by t3hi3x on 2008-04-02
I know global varibles should be avoided, that's why I'm only declaring 3. Sometimes there are good reasons for using them, or you wouldn't be able to ;)

I've tired the extern thing, and that is actually how I figured out it has to do with the header file being called twice using extern - it through a warning.

I've also tired using #ifndef #define #endif statments.

Here's the error report with no extern:

```

g++ -o client ClientSocket.o client.o -L./libsockets++ -lSockets -lpthread -lssl -lcrypto
client.o: In function `__tcf_0':
/usr/include/c++/4.1.3/iostream:76: multiple definition of `toplay'
ClientSocket.o:/usr/include/c++/4.1.3/iostream:76: first defined here
client.o: In function `__tcf_0':
/usr/include/c++/4.1.3/iostream:76: multiple definition of `quit'
ClientSocket.o:/usr/include/c++/4.1.3/iostream:76: first defined here
client.o: In function `__tcf_0':
/usr/include/c++/4.1.3/iostream:76: multiple definition of `playing'
ClientSocket.o:/usr/include/c++/4.1.3/iostream:76: first defined here
client.o:(.data+0x0): multiple definition of `debug'
ClientSocket.o:(.data+0x0): first defined here
collect2: ld returned 1 exit status
make: *** [client] Error 1

```

Here it is with extern:
```

ClientSocket.h:17: warning: ‘quit’ initialized and declared ‘extern’
ClientSocket.h:18: warning: ‘playing’ initialized and declared ‘extern’
ClientSocket.h:19: warning: ‘debug’ initialized and declared ‘extern’
g++  -Wall -g -O2 -I./libsockets++  -MD `Sockets-config`  -c -o client.o client.cpp
/bin/sh: Sockets-config: not found
ClientSocket.h:17: warning: ‘quit’ initialized and declared ‘extern’
ClientSocket.h:18: warning: ‘playing’ initialized and declared ‘extern’
ClientSocket.h:19: warning: ‘debug’ initialized and declared ‘extern’
g++ -o client ClientSocket.o client.o -L./libsockets++ -lSockets -lpthread -lssl -lcrypto
client.o: In function `__tcf_0':
/usr/include/c++/4.1.3/iostream:76: multiple definition of `toplay'
ClientSocket.o:/usr/include/c++/4.1.3/iostream:76: first defined here
client.o: In function `__tcf_0':
/usr/include/c++/4.1.3/iostream:76: multiple definition of `quit'
ClientSocket.o:/usr/include/c++/4.1.3/iostream:76: first defined here
client.o: In function `__tcf_0':
/usr/include/c++/4.1.3/iostream:76: multiple definition of `playing'
ClientSocket.o:/usr/include/c++/4.1.3/iostream:76: first defined here
client.o:(.data+0x0): multiple definition of `debug'

```

---

### Post by dwhitney67 on 2008-04-02
Don't initialize the extern value unless you plan to declare it as a constant.

For example, this definition would generate your warning message:
[PHP]extern int value = 5;[/PHP]

This declaration will get rid of the warning:
[PHP]extern const int value = 5;[/PHP]

If you need to have a read/writable value, then do not initialize it during the declaration.  Initialize it where it is first used.

You really should declare these variables in a namespace!
[PHP]namespace global
{
  int value;
};[/PHP]

---

### Post by t3hi3x on 2008-04-02
> You really should declare these variables in a namespace!


What would I do in straight C where there are no namespaces?

---

### Post by dwhitney67 on 2008-04-02
In reference to the declarations of external variables in C, there's probably a many ways to "skin this cat".

Here's a simple example of how one could declare a global variable and a global function definition (which will use the global variable):

hdr.h:
[PHP]#ifndef HDR_H
#define HDR_H

#ifdef MAIN
#define EXTERN
#else
#define EXTERN extern
#endif

// global variables
EXTERN int value;

#endif[/PHP]

main.c:
[PHP]#define MAIN
#include "hdr.h"
#include "other.h"

int main()
{
  value = 10;
  someFunction();
  return 0;
}[/PHP]

other.h:
[PHP]#ifndef OTHER_H
#define OTHER_H

// function definitions
void someFunction();

#endif[/PHP]

other.c:
[PHP]#include "hdr.h"
#include <stdio.h>

void someFunction()
{
  printf( "value = %d\n", value );
}[/PHP]

---

### Post by LaRoza on 2008-04-02
> **t3hi3x said:**
> What would I do in straight C where there are no namespaces?

Prefix it :-)

---

### Post by t3hi3x on 2008-04-02
> **LaRoza said:**
> Prefix it :-)


lol. Explain.

---

### Post by t3hi3x on 2008-04-02
Ok, so I'm confused. Why do I need to put these in a namespace, if it is perfectly OK to use them in C without one - of course you can't because there is no such thing.

I understand (finally) what those macros do. That will help with that, but I still don't understand why it is wrong for me to delcare them outside of a namespace, when I don't plan on using the varibles outside of the program, which is only a few cpp files.

---

### Post by WW on 2008-04-02
> **t3hi3x said:**
> lol. Explain.
I think LaRoza means give your global variables names like global_playing, global_quit, global_debug, etc.

---

### Post by t3hi3x on 2008-04-02
> **WW said:**
> I think LaRoza means give your global variables names like global_playing, global_quit, global_debug, etc.

That's what I figured. This just re-iterates my last post.

---

### Post by LaRoza on 2008-04-02
> **t3hi3x said:**
> lol. Explain.

Well, in python, you would have:

```

import gtk
gtk.main_quit()

```

and all things in the gtk namespace are qualified.

In C:

```

#include <gtk/gtk.h>
gtk_main_quit ();

```

There is no namespace, but all the gtk function are prefixed with gtk_.

---

### Post by t3hi3x on 2008-04-02
RIght, but why is it wrong to declare global varibles outside of namespace. Of course there may be a better way to do it, but why do people see it sooo wrong? Some things need to be accessed on a global scope.

I just don't see why people are so against it. Especially with a bool that takes up one byte...

---

### Post by LaRoza on 2008-04-02
> **t3hi3x said:**
> RIght, but why is it wrong to declare global varibles outside of namespace. Of course there may be a better way to do it, but why do people see it sooo wrong? Some things need to be accessed on a global scope.

I just don't see why people are so against it. Especially with a bool that takes up one byte...

It is easier to say no, than to make exceptions. Next thing you know, goto's are rampant and raptors are eating your innards.

---

### Post by stratavarious on 2008-04-02
.

---

### Post by the_unforgiven on 2008-04-03
I feel, posting at least the offending part of code would be much helpful than just asking why global variables don't work in general.

There are several reasons why they *might* not work for the compiler.

Maybe, the way your headers are written are wrong?

Also, global variables may be required - especially if you need to interface your code with someone else's code that uses globals.
So, I think using globals should be treated more as part of the developer's taste - there is no rule as such that globals should not be used at all.

---

### Post by aks44 on 2008-04-03
> **heikaman said:**
> i know that global variables are bad practice, but i always wondered , if they are so "evil" how come the std is full of global variables ? like errno ?:confused:

errno (like most other global "standard" variables) is part of the C standard library. And using the libc in a C++ program is itself considered bad practice (not to say evil) as it brings numerous issues, esp. exception safety.

The C++ STL has no globals that I know of.

---

### Post by t3hi3x on 2008-04-03
Of course - all of these responses are good. Thanks.

I just wish some people would actually focus on the question, rather than question a programmer's practice. I know how to program in general, thus I know the basic rules. You assume that just because I'm not amazing at C++ that I do not know what not to do.

I wanted to create 4 bytes worth of global data - bools. And their justified as the program is very event driven.

Just keep in mind that some people know what their doing, they just need help. Thank LaRosa for making that point for me.

I know with all of the questions that could be googled are asked all the time - and it can be frustrating, but don't forget this is a support forum - and some of your customers aren't too bright all the time. They will also learn that Google is a MUCH faster way to find answers when you need them.

Lol just my 10 Cents.

---

### Post by lnostdal on 2008-04-03
yeah, use globals and gotos all you want, t3hi3x .. smear them all over your code and shove it in the faces of the "pointy finger people" .. question what is said (and what you think and say), especially when words like "always" and "never" is used 

"Gotos aren't damnable to begin with. If you aren't smart enough to distinguish what's bad about some gotos from all gotos, goto hell. " -- Erik Naggum

..the people who "aren't smart enough" need crutches like:

* gotos are baaad .. never use them! .. always avoid them!
* globals are baaad .. never use them! .. always avoid them!

..and strive to avoid gotos and globals at all times even in cases where using them would be the cleanest most sensible and natural thing to do

.. ignore these people .. think out of the box and for yourself .. you don't need this kind of artificial over-general advice because you're the kind of person that understands that coffee can sometimes be hot ( [http://www.google.com/search?q=coffee+hot+mcdonalds](http://www.google.com/search?q=coffee+hot+mcdonalds) )

by the way, and now i'm the one to go (more?) off-topic, you'll probably find that "the c++ community" is full of these "pointy-finger" characters (teenagers/gamers) .. i know i did .. language form the way one think i suppose

---

### Post by t3hi3x on 2008-04-03
> **lnostdal said:**
> ... "the c++ community" is full of these "pointy-finger" characters (teenagers/gamers) .. i know i did

I find that all software communities from M$ to BSD are all like that. Too many people that think programming = intelligence and power.

Programming is like any type of engineering - you make something that suits the needs you create. Sometimes you ignore cautions because the simply don't apply your solution. That is the power of choice and knowing what choice is right and most applicable to your solution.

Just a shame people waste their time pointing fingers. They could be doing more for the community besides scaring people off.

And BTW 'always' and 'never' are bad words in a lot of applications - you should be careful when using them - kinda like goto's and global's.

---

### Post by Aztek on 2008-04-03
There's an exception to every rule. Including that one.

Lots of good points made here, but seriously off-topic. Are you still getting these errors? Maybe you could post some of the code as suggested.

I've done a fair amount of embedded C programming and we used a whole load of globals. Here's how I've seen it done:

In my_src.c/.cpp:
```

bool my_var;

```

In my_header.h:
```

#ifndef MY_HEADER_H
#define MY_HEADER_H

extern bool my_var;

#endif // MY_HEADER_H

```

It's as simple as that. Then of course any file which #includes the .h would be able to modify the variable.

---

### Post by t3hi3x on 2008-04-03
I'm going to try the macro thing later tonight when I get out of class.

But here is basically what I have that throws the error.

Main.cpp
[PHP]#include "client.h"

int main()
{
function();
return 0;
[/PHP]

client.h
[PHP]#include <iostream>

bool playing = false;
bool quit = false;

int function();
[/PHP]

client.cpp
[PHP]#include "client.h"

int function()
{
std::cout << "hi\n";

return 0;

}
[/PHP]


```
g++ -c client.cpp -o client.o
```
```
g++ main.cpp client.o -o client
```

---

### Post by Aztek on 2008-04-03
Okay, I'm guessing your problem is that you have your globals defined in client.h, instead of declared.

In case you don't know, defining is when the memory is actually allocated for the variable, declaring is just telling the compiler, "Hi, I'm a variable of such and such type. I exist, but I'm defined somewhere else. Just take my word for it."

Your problem should be solved by moving 

```

bool playing = false;
bool quit = false; 

```

from the header to the top of main.cpp or client.cpp, whichever you prefer. Then add the following to client.h:

```

// At the top
#ifndef CLIENT_H
#define CLIENT_H

// Somewhere in the body
extern bool playing; // note that you don't include the = false
extern bool quit; // note that you don't include the = false

// At the bottom
#endif // CLIENT_H

```

---

