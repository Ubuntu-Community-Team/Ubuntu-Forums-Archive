---
title: "I need help to compiling ChatScript"
date: 2017-10-19
forum: Packaging and Compiling Programs
---

### Post by rezaee on 2017-10-19
Hi
I am newbie in Linux. I like to compile and use ChatScript program on my Ubuntu16.04, as the tutorial says here: [https://github.com/bwilcox-1234/ChatScript/blob/master/WIKI/CLIENTS-AND-SERVERS/ChatScript-External-Communications.md](https://github.com/bwilcox-1234/ChatScript/blob/master/WIKI/CLIENTS-AND-SERVERS/ChatScript-External-Communications.md)
> 
[h=3]Embedding Step #1[/h] First, you will need to modify common.h and compile the system. You need to add all the CS .cpp files to your build list.

 Find the // #define NOMAIN 1 and uncomment it. This will allow you to compile your program as the main program and ChatScript merely as a collection of routines to accompany it. 



But I can not understand this part " **You need to add all the CS .cpp files to your build list.**"
What is my build list? how can I add .cpp to it?

I tried to compile the source file(as you can see it here: [https://github.com/bwilcox-1234/ChatScript/tree/master/SRC](https://github.com/bwilcox-1234/ChatScript/tree/master/SRC)), by ```
make server
``` command as tutorial says, but 
I got this error message: 

```
/usr/lib/gcc/x86_64-linux-gnu/5/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: error: ld returned 1 exit status
Makefile:107: recipe for target 'binary' failed
make: *** [binary] Error 1
```

I asked the author from this error and he said: 
> it was all well and good BUT  you dont have your own C++ program also in  the list of files and YOUR code would have a main program

But I couldn't understand what he says and how can I solve it?

Also the full result of my execution output is visible here: [https://github.com/bwilcox-1234/ChatScript/issues/171](https://github.com/bwilcox-1234/ChatScript/issues/171)

I really need help and want to compile and run it...please help me if you can ](*,)

---

### Post by rezaee on 2017-10-20
Heeeeeeeeeeeeelp meeeeeeeeeee pleaaaaaaaaaaaaaaaaaaaaase

---

### Post by ventrical on 2017-10-20
> **rezaee said:**
> Heeeeeeeeeeeeelp meeeeeeeeeee pleaaaaaaaaaaaaaaaaaaaaase

Let me have a look at this.

Are you familiar with a C++ compiler?

---

### Post by ventrical on 2017-10-20
quoting from your link:

> 
You add ChatScripts files to your project and compile it under a C++ compiler.


so you need to download an opensource C++ compiler, navigate through it and try to learn how to compile with it.

regards..

---

### Post by ventrical on 2017-10-20
> 
But I can not understand this part " **You need to add all the CS .cpp files to your build list.**"
What is my build list? how can I add .cpp to it?


please see here...i think they mean this file.

[B][https://github.com/bwilcox-1234/ChatScript/blob/master/SRC/csocket.cpp](https://github.com/bwilcox-1234/ChatScript/blob/master/SRC/csocket.cpp)


[/B]

---

### Post by rezaee on 2017-10-21
I know I can compile a C program that is written within Test.c file by this command:

```
 gcc -o Test Test.c 
```

not more! But about compiling this program it says we should do it by ```
 make server 
``` command!

---

### Post by rezaee on 2017-10-21
> **ventrical said:**
> quoting from your link:



so you need to download an opensource C++ compiler, navigate through it and try to learn how to compile with it.

regards..


May you introduce some of the good ones? I use gcc for c. So you say I must download another compiler? (I thoght gcc can compile c++ code also)

---

### Post by rezaee on 2017-10-21
in the first page of git([https://github.com/bwilcox-1234/ChatScript](https://github.com/bwilcox-1234/ChatScript))  it says:

 > [h=2][]("https://github.com/bwilcox-1234/ChatScript#how-to-compile-the-engine")How to compile the engine.[/h]
On Linux, go stand in the SRC directory and type make server  (assuming you have make and g++ installed). This creates  BINARIES/ChatScript, which can run as a server or locally. There are  other make choices for installing PostGres or Mongo.
 



---

### Post by ventrical on 2017-10-21
> **rezaee said:**
> May you introduce some of the good ones? I use gcc for c. So you say I must download another compiler? (I thoght gcc can compile c++ code also)

Nope .. It has to be C++ compiler.

 I have <eclipse> installed but you have to download the plugins eclipse-cdt C/C++ Development Tools. Might be better to use synaptic.

I suggest: 1. re-read your links and you will see where C++ compiler is needed
                2. Wait and see if anyone has an easier suggestion or more compressed way to compile using terminal.
                3. Go to the Ubuntu Software Center> Development and take a look at some of  the tools there. (Cmake)

if I have time I'll look at it again..

Regards..

---

### Post by mc4man on 2017-10-21
Install g++ & libcurl4-gnutls-dev then try again.
Though it seems you may be confused as to what you expect here?
[https://github.com/bwilcox-1234/ChatScript/issues/171](https://github.com/bwilcox-1234/ChatScript/issues/171)

---

### Post by steeldriver on 2017-10-21
Are you actually trying to write your own program that uses ChatScript (what they refer to as "ChatScript External Communications")?

If you are just trying to build the standalone ChatScript bot then you are WAY overthinking this - like rezaee says above, all that's necessary (provided you have the necessary compiler and development libraries) is to go to the SRC subdirectory and type

```

make server

```

In fact, you don't really even need to do that - since the git repo appears to include prebuilt platform-specific binaries already:

```

../BINARIES/chatscript.exe
../BINARIES/MacChatScript
../BINARIES/LinuxChatScript64

```

---

