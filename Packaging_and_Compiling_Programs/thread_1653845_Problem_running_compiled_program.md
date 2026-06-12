---
title: "Problem running compiled program"
date: 2010-12-27
forum: Packaging and Compiling Programs
---

### Post by QUARKSPIN on 2010-12-27
Ok, I'm very new to ubuntu so I'll describe my process step by step:

First, I write the following C program in gedit, and save it as helloworld.c:

```

#include <stdio.h>

int main() {
  printf("hello, world\n");
  return 0;
}


```Then, I compile the program with:
```
gcc -o helloworld helloworld.c
``` (In the console)

Typing "```
ls
```" into the console prints out:
```
helloworld  helloworld.c  rougelib
```So I type "```
helloworld
```" into the console and it says:
```
helloworld: command not found
```The permissions for the file are set to "executible", and everybody can read it. (Only "Owner" can write)

What am I doing wrong here?

---

### Post by dev.konverje on 2010-12-27
you will need to tyoe the following

```
$ ./helloworld 
```the "." signifies from the current directory

this is because it when you try to execute a command, the bash shell tries to find it in the locations defined by the path variable

```
$ $PATH
```

---

### Post by hakermania on 2010-12-27
[dev.konverje]("http://ubuntuforums.org/member.php?u=960442")'s reply was complete. If you want to run your ***helloworld*** program from any location of the terminal by simply giving ```
helloworld
``` while being to the directory of the compiled `helloworld` give ```
sudo cp helloworld /usr/bin/
``` :) This way you can convert any program to console command :)

---

### Post by QUARKSPIN on 2010-12-29
Thanks! I guess I should start reading manuals before I ask questions...

---

