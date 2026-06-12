---
title: "Trouble Compiling a File"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Shambopyro on 2013-04-05
So here's the deal:
 
I'm trying to install an aimbot mod for sauerbraten and it involves copying & replacing file in the game's directory. The instructions also say to recompile said file. After finding the command to compile a file & installing all the necessary packages, I can't compile this file. I did do the hello world test thing so I'm pretty sure I have everything installed. Here is the terminal window of my failures: 

sam@SAMSULTIMATE:~$ cd /downloadsbash: cd: /downloads: No such file or directory
sam@SAMSULTIMATE:~$ cd Downloads
sam@SAMSULTIMATE:~/Downloads$ cd sauerbroten
sam@SAMSULTIMATE:~/Downloads/sauerbroten$ cd sauerbraten
sam@SAMSULTIMATE:~/Downloads/sauerbroten/sauerbraten$ cd src
sam@SAMSULTIMATE:~/Downloads/sauerbroten/sauerbraten/src$ cd fpsgame
sam@SAMSULTIMATE:~/Downloads/sauerbroten/sauerbraten/src/fpsgame$ g++ client.cppIn file included from client.cpp:1:0:
game.h:4:18: fatal error: cube.h: No such file or directory
compilation terminated.
sam@SAMSULTIMATE:~/Downloads/sauerbroten/sauerbraten/src/fpsgame$ g++ client.cppIn file included from client.cpp:1:0:
game.h:4:18: fatal error: cube.h: No such file or directory
compilation terminated.
sam@SAMSULTIMATE:~/Downloads/sauerbroten/sauerbraten/src/fpsgame$ 


here's the link to the mod: 


[http://sourceforge.net/projects/cube2sauerbrate/](http://sourceforge.net/projects/cube2sauerbrate/)

here's the link to sauerbraten (it's a fun game): [http://sauerbraten.org/](http://sauerbraten.org/)

Any help is greatly appreciated!

---

### Post by Nr90 on 2013-04-05
Without looking at the code or knowing anything about the game:
The C++ file you're trying to compile includes a local header file (cube.h). This file is assumed to be in the same directory as the cpp source file.
Apparently it is not in that directory. You could try finding it in your installed files.
I googled the file with that game name and found [https://github.com/amstan/sauerbraten/blob/master/src/shared/cube.h](https://github.com/amstan/sauerbraten/blob/master/src/shared/cube.h)
It is most likely the header you need. Putting that in a file called cube.h in the compiling directory should fix that error.

There might be other missing things if you're compiling in the wrong directory in the first place.

---

### Post by Shambopyro on 2013-04-06
Thanks. I'll try it.

---

### Post by Shambopyro on 2013-04-06
Ok, I moved the file to the same directory as client.cpp, but when I try to run the command, I can't cp to the directory. 

sam@SAMSULTIMATE:~$ cp /Downloads
cp: missing destination file operand after `/Downloads'
Try `cp --help' for more information.
sam@SAMSULTIMATE:~$ cp
cp: missing file operand
Try `cp --help' for more information.
sam@SAMSULTIMATE:~$

---

### Post by steeldriver on 2013-04-06
[FONT=courier new]cp [/FONT]= **c**o**p**y

[FONT=courier new]cd [/FONT]= **c**hange **d**irectory

---

### Post by Shambopyro on 2013-04-06
*facepalm* Thanks!

---

### Post by Shambopyro on 2013-04-06
Ok, now I've tried the first solution and this is what I get:

sam@SAMSULTIMATE:~/Downloads/sauerbroten/sauerbraten/src/fpsgame$ g++ client.cpp
In file included from game.h:4:0,
                 from client.cpp:1:
cube.h:46:17: fatal error: SDL.h: No such file or directory
compilation terminated.
sam@SAMSULTIMATE:~/Downloads/sauerbroten/sauerbraten/src/fpsgame$ 




I'm going to assume now that I should find SDL.h, move it to the directory & try again. Am I correct?

---

### Post by steeldriver on 2013-04-06
I don't know anything about the sauerbraten game but if you are recompiling it you should probably be using the build instructions that come with the original source code (possibly a Makefile, or a ./configure ... make ... make install process) - rather than trying to compile the individual replacement file directly with g++

The build process for the game will probably set an appropriate environment / include flags / library path flags without which g++ probably won't find the required packages - even if you installed them all at Step 1 

IMO that's the correct way to resolve the 'No such file' errors - NOT chasing down / copying the missing files

---

