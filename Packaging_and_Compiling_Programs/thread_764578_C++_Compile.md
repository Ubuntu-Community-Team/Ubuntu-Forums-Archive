---
title: "C++ Compile"
date: 2008-04-24
forum: Packaging and Compiling Programs
---

### Post by Q-ro on 2008-04-24
[FONT="Comic Sans MS"][B]i'm really in a hurry, so i don't have much time to search for the info i'm needing, i'm trying to compile a C++ file, i instal g++, then used 

```
 g++ -o main.cpp main 
```

and i got "binary" file, or at least that what it says when i use 

```
bash main
```

and i got as an answer " could not run binary" or something like that, i don't know what i'm doing worng, how do i get it to run, i did the same on fedora and it work, so i don't know if the thing is that ubuntu use another compiler, or if i'm missing something of g++ like a port or i don't know, thanks to any one how can help me, by now i gotta do a lot of thinks so thas why i'm asking for help, i dont have time to search all over internet for an answer.[/B][/FONT]

---

### Post by Natr0n on 2008-04-24
```

g++ -o main main.cpp
./main

```

---

### Post by PypeBros on 2008-04-24
To make it a little less magic, what you produced is an ELF executable. you can ask linux which file is of what kind using "file <filename>" command, e.g. 
```

home/you> g++ main.cpp -o main
home/you> file main
main:  ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), not stripped
home/you>

```

Second, there are two kind of things a linux system can natively run: ELF executables (like g++, bash, and now main) and scripts (text files containing a batch of commands). when you invoke "bash <filename>", you start another instance of the shell and you ask it to read commands from <filename> rather than from the keyboard. After a good deal of characters read out of "main" without finding a 'new line' character, bash concludes that it is likely to be a binary file (such as .jpg images, .mp3 files, etc.) and not lines of text. It complains about it.

If you're comfortable with DOS (oops. I mean windows, sorry) shell, you certainly wonder now why just invoking "main" on the command line did not work and why you're forced to type "./main" instead.
The answer is that, unlike in DOS/windows, the unix shells *only look for binaries in the directories that are mentionned in the $PATH environment variable*, where DOS command interpreter looked *first* for a matching .EXE/.COM in the current directory *and then* in directories mentionned in %PATH%.
Note that you can see the content of your $PATH by typing
```

home/you> echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/X11R6/bin:/usr/games

```

By saying "./main", you override this, as what you're now giving is recognizable as a path, not simply as a name to be resolved by the shell. invoking "/home/you/main" would have worked as well.
If you find this silly and want to be able to test your freshly compiled programs, all you have to do is to include "the current directory" in your $PATH with
```

home/you> export $PATH=".:$PATH"

```

Be warned, however, that by making this, you could be fooled by a program named "ls" or "firefox" or (worse) "sudo" that lies in the current directory rather than in the regular system location for programs. That's why this "shortcut" isn't present by default.
If you like it that way, you can edit your .bashrc file so that the $PATH is fixed everytime you open a new console.

---

### Post by Q-ro on 2008-04-25
[B][FONT="Comic Sans MS"]thanks a lot, but i still don't get it, i mean, in fedora i just called main and it runs normally, but its ok, no on i'll use ./<filename> to run files, other thing i wanted to ask is:

i used to program on windows, turbo C, and dev C++, there you usualli put 

```
#include <iostream.h>
```

i have noticed in linux you don't put the ".h", so the obvious question is, what was that  ".h"? 

( sorry if it is a silly question but you don't learn that stuff when the teach you to program =.= )


other thing i wanted t ask, if there something like windows/linux libraries ?? , is because i'm trying to use "conio", but it semes not to be a linux library, so i think maybe an linux library that do the same as conio.

Thaks for the past answers, they were very helpfull, thats the ubuntu spirit ;)[/FONT][/B]

---

### Post by Natr0n on 2008-04-25
Not putting the ".h" in isn't limited to Linux. You're not really supposed to do it anywhere, including windows - at least not with system includes like iostream. If you have your own header to include you would still say```
#include "MyHeader.h"
```but the only reason I can think of to write something like```
#include <iostream.h>
```would be if you had some really old C++ compiler.

As for conio, you can get the same functionality from [[COLOR="Blue"]ncurses[/COLOR]]("http://invisible-island.net/ncurses/ncurses.html") (curses.h), which is probably already installed. If not,```
sudo apt-get install libncurses5 libncurses5-dev
```should do the trick.

---

### Post by Q-ro on 2008-04-25
[FONT="Comic Sans MS"]**actually i used a very old compiler for windows, turbo C is really old, it runs on DOS =P, dev c++ uses no ".h" for iostream, but does use it for other libraries, and thanks for curses, it worked perfectly, now i have all i need, just one little thing but i'll do it by my self, any way thanks a lot, hope to cross post again in another time, take care you all that helped me so much =)**[/FONT]

---

