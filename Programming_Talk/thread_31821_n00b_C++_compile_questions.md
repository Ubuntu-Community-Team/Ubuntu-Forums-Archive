---
title: "n00b C++ compile questions"
date: 2005-05-04
forum: Programming Talk
---

### Post by MikePB on 2005-05-04
mmkay, Yeah, I'm new still fairly new to Linux and programming C++, I was wondering how to compile and run a simple teminal program.

I used g++ and got a file called [FONT=Lucida Console]a.out[/FONT], but don;t know what to do from there. The file says it's executable but won't run when I double-click it, nor when run from a terminal.

Help a poor n00b? :) :roll:

---

### Post by dataw0lf on 2005-05-04
boringprompthere$ g++ foo.cpp -o foo
boringprompthere$ ./foo

---

### Post by lorap on 2005-05-06
hi friend!
well the previous reply was very good.
this's mine one:
i use native unix compiler that's built in in any linux/unix system - cc.
to compile the file say "mixer.c" and build an object file do this:

cc -c mixer.c

if you wanna build an executable then you do this:

cc -o mixer mixer.c

this'll produce an executable "mixer".
if you've any questions how to create static and dynamic libraries then write to my private email:
[email]prianfamily@gmail.com[/email]
feel free, i'm silly so no prob :-)
i'm not proposing you use anjuta or any other environment, but make everything by your hands so no way a poison gets in your food :-)

---

### Post by Kimm on 2005-05-06
then theres just the problem to that a *.c file is not a C++ file [-X 

MikePB, Linux does not work the same way as windows on this area (if it does in any area). A console program will start when you dubble click on it, the thing is woever that it will not open a console window automaticly, if you want to see the output you have to run it from the console, like so:

./a.out

if you want a different filename for your program, you can type (lets say the file is called green.cpp):

g++ green.cpp -o green

the file is now called green, to run it, type:

./green

---

### Post by LordHunter317 on 2005-05-06
[QUOTE=lorap]
i use native unix compiler that's built in in any linux/unix system - cc.[/quote]As has been said, this is C++. There is no standard C++ compiler.

> to compile the file say "mixer.c" and build an object file do this:

cc -c mixer.c

if you wanna build an executable then you do this:

cc -o mixer mixer.cIt's worth noting that this is about the limit of flags you can expect to be stanard across all UNIX.


> i'm not proposing you use anjuta or any other environment, but make everything by your hands so no way a poison gets in your food :)This line of thinking is downright silly at best.

---

