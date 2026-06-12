---
title: "codeblocks wont  build and run on ubuntu"
date: 2018-05-08
forum: New to Ubuntu
---

### Post by fernanda123321 on 2018-05-08
HI!!!
IM trying to build and run a simple program in codeblocks (c lenguage) but every time I press the build and run button it says : seems the project has not been build yet. But even though i press yes nothing happens.
Ive tried everything ive seen online but nothing seems to work :(
THANKS IN ADVANCE!!


Build log shows this:

-------------- Build: Release in Lab01PP (compiler: GNU GCC Compiler)---------------

gcc -Wall -O2 -std=c99 -ansi -m64  -c /home/fernanda/Escritorio/Lab01PP/main.c -o obj/Release/main.o
execvp(/bin, gcc -Wall -O2 -std=c99 -ansi -m64  -c /home/fernanda/Escritorio/Lab01PP/main.c -o obj/Release/main.o) failed with error 13!
Process terminated with status -1 (0 minute(s), 0 second(s))
0 error(s), 0 warning(s) (0 minute(s), 0 second(s))
 

-------------- Run: Release in Lab01PP (compiler: GNU GCC Compiler)---------------

Checking for existence: /home/fernanda/Escritorio/Lab01PP/bin/Release/Lab01PP
Executing: xterm -T Lab01PP -e /usr/bin/cb_console_runner LD_LIBRARY_PATH=$LD_LIBRARY_PATH:. /home/fernanda/Escritorio/Lab01PP/bin/Release/Lab01PP  (in /home/fernanda/Escritorio/Lab01PP/.)

---

### Post by TheFu on 2018-05-09
error 13 is a permissions issue.  And no, I don't have all the different possible errors memorized, but error 13 happens enough when you are new to memorize.

Since it is under your HOME, I have a strong suspicion that you used sudo incorrectly.  Yes? 
Another alternative is that the PWD is wrong.

Linux is multi-user from the ground up. Security begins with file and directory permissions.  Using fully specified or relative paths is also important for most software development.

---

