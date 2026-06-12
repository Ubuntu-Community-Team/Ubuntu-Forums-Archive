---
title: "Good place to learn to start programming in linux."
date: 2005-04-13
forum: Programming Talk
---

### Post by endoscient on 2005-04-13
I already know a basic amount of programming. But I have no clue how I would use it linux. I use to use Visual Studio on windows. Where is a good place to learn how to start making stuff for linux. I tried to use Kdevelop to make a simple commandline apps but I get errors for the simpliest of programs. Also after where could I learn to use GTK or KDE toolwork? THanks in advacne for the help.

---

### Post by wtd on 2005-04-14
A suggestion... become acclimated with using GCC via the command-line.  I would agree with anyone who says knowledge of the command-line isn't absolutely essential for a Linux user anymore, but it is critical for a programmer.

The various IDEs available on Linux simply use GCC, and it can be a complex program with many options.  IDEs often ease the process of dealing with these options.  Of course, they also force you to deal with those options, and for simple programs, you generally don't need to worry about them at all.

---

### Post by elwis on 2005-04-14
developer.kde.org developer.gnome.org

---

### Post by endoscient on 2005-04-14
[QUOTE=wtd]A suggestion... become acclimated with using GCC via the command-line.  I would agree with anyone who says knowledge of the command-line isn't absolutely essential for a Linux user anymore, but it is critical for a programmer.

The various IDEs available on Linux simply use GCC, and it can be a complex program with many options.  IDEs often ease the process of dealing with these options.  Of course, they also force you to deal with those options, and for simple programs, you generally don't need to worry about them at all.[/QUOTE]
How do you compile command line programs with GCC? Just some syntax highlighting and basic file managment is good enough for me for an IDE. Any suggestions?

---

### Post by dataw0lf on 2005-04-14
gvim or maybe KDevelop.

---

### Post by wtd on 2005-04-14
[QUOTE=endoscient]How do you compile command line programs with GCC? Just some syntax highlighting and basic file managment is good enough for me for an IDE. Any suggestions?[/QUOTE]
 At the most basic...

```
#include <stdio.h>

int main()
{
   puts("Hello world");
   return 0;
}

```

```
$ gcc hello_world.c -o hello_world
$ ./hello_world
```

Of course, for more complex projects there's the whole world of makefiles.

I could write for the next year and barely scratch the surface.  There's a lot of material online, and just a Google away.  Also, though Ubuntuforums are great, you may want to check out the Programmer's Symposium at ArsTechnica for an even larger, more active community.

Good luck.

---

### Post by jpb on 2006-03-30
I just installed the Ubuntu 5.10 release for i386 via bootable DVD. Everything seems to work. Now, I want to try some development.  I have installed the gcc 4.0.2 package but something is misconfigured since I can't compile hello world. Is there some easy way to automatically set up all the standard include and lib files so I can start compiling things?  Do I have to manually set PATH vars via shell scripts, etc?

beale@JPB-P3:~$ cat hello.c
#include <stdio.h>

main()
{
  printf ("Hello World!\n");

}
beale@JPB-P3:~$ gcc hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in
function ‘printf’
beale@JPB-P3:~$

---

### Post by hod139 on 2006-03-30
You may have wanted to start a new thread for this, but the answer is to install the build-essential package.
```
sudo apt-get install build-essential
```

---

### Post by jpb on 2006-03-30
I knew it must be something simple. That did the trick; thanks!

---

### Post by Javaman59 on 2007-03-11
Thanks, this thread got me started to! :) 

I would add that although gcc works by itself, it is easier to invoke it via "make". You will also need to get started with make files for any serious programming in Linux. Basically, "make" manages the compilation sequence of multiple source files, like Visual Studio does when you "build" a project (although Visual Studio does it without you even noticing).

Thus my recommended sequence for the first program is...

```

# install the essential Debian programming libraries
$ sudo apt-get install build-essential
# Edit the file. gedit is a good graphical edit, with syntax highlighting.
$gedit hello_world.c  
# Compile and link (ie. "make") the program
$ make hello_world
# Execute it
$ ./hello_world

```

---

