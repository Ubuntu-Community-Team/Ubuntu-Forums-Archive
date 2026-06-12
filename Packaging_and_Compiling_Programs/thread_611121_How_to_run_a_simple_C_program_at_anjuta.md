---
title: "How to run a simple C program at anjuta?"
date: 2007-11-12
forum: Packaging and Compiling Programs
---

### Post by yuval2111 on 2007-11-12
I am a new user of ubuntu and anjuta.
i worte a simple program at C that prints the word "hello":

#include <stdio.h>
int main(){
	printf("hello");
	return 0;
}

i run at the shell the command "gcc -Wall test.c -o 1"
and it's compile it fine, but when i wrote the command "1" it wrote to me "bash: 1: command not found". what is the problem? when i do it at the university computers it's run fine.
thanx.

---

### Post by Kevin on 2007-11-13
If you're in the directory where the "1" binary is, then you need to run "./1" at the terminal.

This goes for any executable.  Typing the name will always look in /usr/bin, you need to specify ./--name-- to run a file in the current directory.

---

### Post by yuval2111 on 2007-11-13
thanx, now it works.

---

### Post by elthumb on 2007-11-13
you can run it without return 0
just 
#include <stdio.h>
main()
{
printf("elthumb was here...\n");
}
:guitar:

---

