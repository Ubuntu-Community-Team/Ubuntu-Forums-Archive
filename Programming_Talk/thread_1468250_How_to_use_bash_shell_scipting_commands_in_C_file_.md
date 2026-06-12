---
title: "How to use bash shell scipting commands in C file in ubuntu ?"
date: 2010-05-01
forum: Programming Talk
---

### Post by youralibaba on 2010-05-01
Can I use echo etc shell commands in my C language code ? Or vice versa ?

e.g 

#include<stdio.h>
int main (){

echo "Hello World"

printf("Hello World");

return 0;
}

---

### Post by CptPicard on 2010-05-01
```

man system:

SYSTEM(3)                                                           Linux Programmer's Manual                                                           SYSTEM(3)

NAME
       system - execute a shell command

SYNOPSIS
       #include <stdlib.h>

       int system(const char *command);

DESCRIPTION
       system() executes a command specified in command by calling /bin/sh -c command, and returns after the command has been completed.  During execution of the
       command, SIGCHLD will be blocked, and SIGINT and SIGQUIT will be ignored.


```


So the answer is "yes", but I get this weird feeling that you are going about this wrong if you plan on making use of this a lot :)

---

### Post by Penguin Guy on 2010-05-01
Yes - look into [FONT="Courier New"]system()[/FONT], but I would **strongly** advise you try to stick to one language per program as much as possible. Because pratiquant des langues différentes peut être source de confusion and create portability issues.

---

### Post by CptPicard on 2010-05-01
And oh yes... "vice versa" -- that is what shell scripts are; most of the "commands" in them are external tools, and the majority of those are written in C.

---

### Post by ApEkV2 on 2010-05-01
Also if you want to use a shell command and use the output from it, here's a way to do so.
```
char *cmd = "free -m | grep 'buffers/cache:'"; // example command
FILE *result = popen(cmd,"r");
```
Then make some functions to parse through result.
Picard is right though as most shell commands are written in C.

---

### Post by ssam on 2010-05-01
also if you use system() then you are starting a new process, which is a big overhead if you only need to output something. so you get the pain of C, with the slow of shell.

that said there are probably cases where it will save you some effort. sometimes you really need one program to start/control others.

---

