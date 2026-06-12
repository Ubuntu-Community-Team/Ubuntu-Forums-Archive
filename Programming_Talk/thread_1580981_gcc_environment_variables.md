---
title: "gcc environment variables"
date: 2010-09-24
forum: Programming Talk
---

### Post by sudipm on 2010-09-24
[SIZE=2]Hi[/SIZE]
[SIZE=2]In my project, i need to access the include file search path as used by gcc.[/SIZE]
[SIZE=2]gcc is using the include file search path as[/SIZE]
[FONT=Verdana][SIZE=2]/usr/local/include[FONT=Verdana]libdir/gcc/[/FONT]target/version/include/usr/target/include/usr/include[/SIZE][/FONT][FONT=Verdana][SIZE=2]now the problem is how do i get the values of these libdir, target and version from my c program?[/SIZE][/FONT][FONT=Verdana][SIZE=2]I thought if i can access the environment variables [FONT=Courier New]LIBRARY_PATH or C_INCLUDE_PATH [/FONT]as used by gcc , then my problem could have been solved.[/SIZE][/FONT][FONT=Verdana][SIZE=2]i will very much appreciate any help or hint from anyone..[/SIZE][/FONT][FONT=Verdana][SIZE=2]Thanks in advance[/SIZE][/FONT][FONT=Verdana][SIZE=2]Sudip[/SIZE][/FONT]

---

### Post by dwhitney67 on 2010-09-24
Nice font.  Are you trying to drive the community blind?


The C_INCLUDE_PATH and the LD_LIBRARY_PATH environment variables are not always defined in one's environment; and the latter (if defined) does not have the context of what you are seeking.

Can you please explain why it is necessary for your application to know the include path of where header files, which are used to compile the source code, reside?

If it is essential, then define an environment variable, or pass it to the program as a command line arg.

---

### Post by sudipm on 2010-09-24
> **dwhitney67 said:**
> Nice font. Are you trying to drive the community blind?
 

 
Sorry about the font. 
It is supposed to be a mini preprocessor , where i just need to remove the comments and process the #include .

---

### Post by VernonA on 2010-09-24
I understand what you are trying to achieve, but I would not recommend you actually doing it. The library paths you pass to gcc in order to compile your program, are very specific to your src code. Assuming that they are the same for another application's source files which you are preprocessing is pretty dubious. 
The better solution is to expect the user to supply the paths in the same way you had to when you compiled your code. For example, if a user is running your preprocessor as part of a compilation, they will probably put it in a "make" file or script file of some sort. This file should also include a 'set INCLUDE_PATH="..whatever.."' line near the top, as you can't be expected to guess which version of, say, <std.h> he is trying to #include.
Rgds,
Vernon

---

