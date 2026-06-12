---
title: "C/C++ Plug-in based programming"
date: 2010-02-02
forum: Programming Talk
---

### Post by opengl_cpp on 2010-02-02
Hi,
I wonder how to read the content of a shared object inside my c/c++ source code. Let me explain more.

Imagine i have a main.c file and it can get 2 int numbers and add them, then i compile this file using gcc and then i have an executable file.

after a while i notice that i like to add subtraction ability(function) to my simple program. there are 3 major way to do it:

1- adding the code inside to source file (main.c) and recompiling it.
2- creating another source file and implementing the new function into it, then compiling it as an static or shared object and the recompiling the main.c against this object file

**3- embedding a peace of code, i mean new function into main.c to read and deal with the content of a directory, say "./plugin" at runtime and checking if there is any shared library within the directory, if any, reading their contents and adding the extra functionality to the main program on the fly. 

so, my question is that how can we implement the third approach? in other words, how can we read the content of shared objects on the fly?

---

### Post by opengl_cpp on 2010-02-02
oh i forgot to name an extra way to do it, although this is not my favorite way, and my question still remains on third approach.

well, this extra way is to use and embed an scripting language, say perl or lua, to add the new functionality as scripts into our executable program. this approach is useful in some situation, but here you have to force the end user to download another program (perl, lua, ...) to be able to run your app correctly, or it would lack a lot of functionalities, though you won't need to recompile your app anymore.

---

### Post by nvteighen on 2010-02-03
Ok, let's put names to each "way" you've mentioned :) You're quite in the right track. Implementing the code yourself is actually a different thing, because you're not including anything from elsewhere, so let's look at the other ones.

1. **Static linking**: Inline code inclusion from other files at compile-time. The *.a GNU/Linux (and other Unix-like) format is just a convenience archiving format GCC is able to expand into its component files... But the actual linking is done with the .o object files.
2. **Dynamic linking**: Linking to code at compile-time so that it loads at the program's startup.
3. **Dynamic loading**: Loading code at runtime.
4. **Embedded scripting**: It's actually more a sort of dynamic loading, but as you mentioned, it's also a way to include code from somewhere.

For plugins, the usual way is to use dynamic loading or scripting. Dynamic loading in C and C++ is done through dlopen() and family and are amazingly easy to use. Scripting, instead, depends on your chosen platform's API.

---

### Post by opengl_cpp on 2010-02-03
thanx nvteighen.

actually your right.

I will search the net for it.

---

### Post by Portmanteaufu on 2010-04-20
> **opengl_cpp said:**
> 
well, this extra way is to use and embed an scripting language, say perl or lua, to add the new functionality as scripts into our executable program. this approach is useful in some situation, but here you have to force the end user to download another program (perl, lua, ...) to be able to run your app correctly, or it would lack a lot of functionalities, though you won't need to recompile your app anymore.

I've had a really great experience embedding Lua in a massive C++ application for work.

Are you distributing your program's source or as an executable? When you embed Lua in your program, the interpreter actually becomes part of your binary file. If you are distributing a pre-compiled executable, this means that the end user would not have to take any extra steps to be able to run your code or any associated scripts.

(Of course, if you are distributing the source for your code so the end-user can build it themselves, then they'll need to have access to Lua -- but you could always bundle Lua's code with your own, seeing as it's under a free-to-redistribute license and only about 200k.)

Lua is written in C, so you control it from your own code. There's a function to start the Lua interpreter, a function to execute a Lua file, and functions to trade information between the Lua interpreter object and your own code. It's pretty easy once you get going.

---

