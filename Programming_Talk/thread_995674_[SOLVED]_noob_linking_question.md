---
title: "[SOLVED] noob linking question"
date: 2008-11-28
forum: Programming Talk
---

### Post by blake82 on 2008-11-28
Hi all,

I'm trying to write a simple JACK client, I've installed the jack header files, and my IDE can see it. However, when I try to build my project, I get this error:

/home/blake/NetBeansProjects/Application_1/main.cc:26: undefined reference to `jack_client_new'

My understanding is that g++ is trying to link my compiled main.o to another (jack) object file, but this file is nowhere to be found.

I've downloaded all of the JACK dev parts, but I can't find any object files. I've had this problem with the gtk libraries in the past (causing me to switch to Qt), so I'm thinking there's something simple I'm just not doing.

Any help is appreciated.

Thanks,

Blake

---

### Post by dribeas on 2008-11-28
> **blake82 said:**
> I've downloaded all of the JACK dev parts, but I can't find any object files. I've had this problem with the gtk libraries in the past (causing me to switch to Qt), so I'm thinking there's something simple I'm just not doing.


It is probably a library, you may want to pass it to the linker with -lname_of_library. Depending on how you have downloaded/installed the library you may need to build it, look for instructions in the jack directory.

---

### Post by nvteighen on 2008-11-28
You have to add the -l switch to your compiling command. This occurs with the C Math Standard Library (/usr/lib/libm.so) and the switch is always written as -l**library's name without lib- and without .so**, so, to use it, you add -lm to the gcc command. CUPS, e.g -lcups (/usr/lib/libcups.so, if I'm not mistaken) and so on...

Locate the JACK library and try using the switch. If more libraries are needed, possibly you have to use pkg-config (as GTK+ does) to grab all libraries together in a single step.

---

### Post by blake82 on 2008-11-28
Thanks for your help!

So I found libjack.so in /usr/lib/, and added -ljack to the Make options (using netbeans), but I'm still getting the undefined reference error

any ideas?

---

### Post by nvteighen on 2008-11-28
> **blake82 said:**
> Thanks for your help!

So I found libjack.so in /usr/lib/, and added -ljack to the Make options (using netbeans), but I'm still getting the undefined reference error

any ideas?

Ok, got it.

You have to do exactly the same as you'd do in GTK+ ;) You need more than one library, so there is a pkg-config command for JACK that will do it for you automatically:

```

gcc -o prog source.c -Wall `pkg-config --libs jack`

```

(NOTE: Use backticks (` `) not quotes (' ')!)

If you try running **pkg-config --libs jack** directly into the shell, you'll get the correct switches as output (try it!).

And, as you mentioned it before, now you know how to compile a GTK+ program: use `pkg-config --cflags --libs gtk+-2.0` (--cflags grabs headers in non-standard places)

---

### Post by blake82 on 2008-11-28
Wicked!

This has been one of those obstacles that you know has a simple solution but can't find

Thanks for your help, I really appreciate it!

---

### Post by nvteighen on 2008-11-29
> **blake82 said:**
> Wicked!

This has been one of those obstacles that you know has a simple solution but can't find

Thanks for your help, I really appreciate it!
(Mark this thread as solved!)

---

### Post by WitchCraft on 2008-11-29
You gave the compiler the file to link with, but not the directory where this file is in...

---

### Post by blake82 on 2008-11-29
> **nvteighen said:**
> (Mark this thread as solved!)

Done!

> **WitchCraft said:**
> You gave the compiler the file to link with, but not the directory where this file is in...

Actually, I just put 

```
`pkg-config --libs jack`
```

In the linker command line options for my project, and that did the trick

---

### Post by nvteighen on 2008-11-30
> **blake82 said:**
> 
Actually, I just put 

```
`pkg-config --libs jack`
```

In the linker command line options for my project, and that did the trick

Well, what pkg-config does is to create the linker options for you (for those packages that provide a pkg-config file). The backticks (` `) execute the enclosed expression and pipe the output to the command you were giving in.

Try this in your Terminal (no backticks, no gcc, just this line):
```

pkg-config --libs jack

```

And you'll see the -l options needed for JACK to be linked.

---

