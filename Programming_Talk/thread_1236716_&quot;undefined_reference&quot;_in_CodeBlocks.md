---
title: "&quot;undefined reference&quot; in Code::Blocks"
date: 2009-08-10
forum: Programming Talk
---

### Post by Muboo on 2009-08-10
Hello :)

As I have recently switched to Ubuntu, I am moving my C++ code to Code::Blocks. However I get an error when trying to use a function that is defined:

```
-------------- Build: Debug in N ---------------

Compiling: src/main.cpp
Linking console executable: bin/Debug/N
obj/Debug/src/main.o: In function `main':
/home/lazlo/N/src/main.cpp:18: undefined reference to `N::Network::Initiate()'
collect2: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 0 seconds)
1 errors, 0 warnings
```

Here is the code used:
[http://pastebin.com/d5bcc8f9a](http://pastebin.com/d5bcc8f9a)

Any input? This code worked correctly on Win32/MSVC++. Thank you :)

EDIT: Note: Placing the implementation of the functions directly in the header file allows the code to run, however this is not what I want.

-Lazlo

---

### Post by nvteighen on 2009-08-10
The linker is clearly missing a library. That's where I say I hate IDEs... using the command line would solve this immediately:

```

g++ -o (your program's name) (all your .cpp files) -Wall

```

---

### Post by Muboo on 2009-08-10
I wish to continue using my IDE, so does anyone else have a solution?
And I doubt it is a library problem, as as I told you, if the implementations are in the header, it works. Proves SDL is correctly linked.

---

### Post by dwhitney67 on 2009-08-10
When you get an "undefined referenced" error, this indicates either one of the following:

1. You are not linking your application with the library that provides the function.

or

2. You have failed to implement the function within your own code.

Without seeing your code, it is hard to know exactly whether your application or the IDE configuration has the deficiency.  But I'm sure you will figure it out.

Now back to my psychic exercises.

---

### Post by nvteighen on 2009-08-11
> **Muboo said:**
> I wish to continue using my IDE, so does anyone else have a solution?
And I doubt it is a library problem, as as I told you, if the implementations are in the header, it works. Proves SDL is correctly linked.
Then it clearly is an IDE/project configuration issue, if SDL is correctly linked.

I haven't ever used Code::Blocks, so I don't know how to do this. But what you need is to make the IDE aware of all compilation units your project has.

---

