---
title: "Execute a command inside a program?"
date: 2005-11-26
forum: Programming Talk
---

### Post by Luggy on 2005-11-26
I'm trying to make a front end for all my roms. I'm going to build a GUI that will let me select which rom I want to play and then run my emulator with the proper game that I selected.

What I need to know is how do I run a program/execute a command from inside another program?

---

### Post by gord on 2005-11-26
[http://www.gnu.org/software/libc/manual/html_node/Executing-a-File.html#Executing-a-File](http://www.gnu.org/software/libc/manual/html_node/Executing-a-File.html#Executing-a-File)
is a nice detailed view on howto do that, of course it depends on what language you are using (you don't say)

---

### Post by Luggy on 2005-11-26
[QUOTE=gord][http://www.gnu.org/software/libc/manual/html_node/Executing-a-File.html#Executing-a-File](http://www.gnu.org/software/libc/manual/html_node/Executing-a-File.html#Executing-a-File)
is a nice detailed view on howto do that, of course it depends on what language you are using (you don't say)[/QUOTE]

Whooops.
Sorry about that. I'll be coding in C++.

---

### Post by cactus on 2005-11-26
I would recommend just doing a fork && exec, if you can "get away with it".

---

### Post by Luggy on 2005-11-26
I'm having some trouble making heads or tails of this.
> 
Function: int execv (const char *filename, char *const argv[])

    The execv function executes the file named by filename as a new process image.

    The argv argument is an array of null-terminated strings that is used to provide a value for the argv argument to the main function of the program to be executed. The last element of this array must be a null pointer. By convention, the first element of this array is the file name of the program sans directory names. See Program Arguments, for full details on how programs can access these arguments. 


I understand what I should put in for *filename* but I'm not sure what I should do for *argv*.

For testing purposes I was trying to open gmplayer. When I try to compile the code below:
```
#include<unistd.h>

int main()
{
	char *filename;
	char argv[]="";
	
	filename = "gmplayer";
	
	execv(filename,*argv);
	return 0;
}
```
I get this as my output:
```
paul@ubuntu:~$ g++ foo.cpp
foo.cpp: In function &#8216;int main()&#8217;:
foo.cpp:10: error: invalid conversion from &#8216;char&#8217; to &#8216;char* const*&#8217;
foo.cpp:10: error:   initializing argument 2 of &#8216;int execv(const char*, char* const*)&#8217;

```

Any ideas?

---

### Post by cwaldbieser on 2005-11-26
> **Luggy]I'm having some trouble making heads or tails of this.


I understand what I should put in for *filename* but I'm not sure what I should do for *argv*.

For testing purposes I was trying to open gmplayer. When I try to compile the code below:
```
#include<unistd.h>

int main()
{
	char *filename said:**
> ="";
	
	filename = "gmplayer";
	
	execv(filename,*argv);
	return 0;
}
```
I get this as my output:
```
paul@ubuntu:~$ g++ foo.cpp
foo.cpp: In function ‘int main()’:
foo.cpp:10: error: invalid conversion from ‘char’ to ‘char* const*’
foo.cpp:10: error:   initializing argument 2 of ‘int execv(const char*, char* const*)’

```

Any ideas?

Try this:
```

#include<unistd.h>

int main()
{
	char *filename;
	char* const argv[]= {"", 0};
	
	filename = "/usr/bin/kcalc";
	
	execv(filename, argv);
	return 0;
}
 

```

Basically, the "argv" argument is and array of pointers to command line arguments.  The pointers point to const C-style strings (sequences of chars that are null terminated).  To indicate the end of the argv array, the last entry is a null as well.

Of course, I used kcalc, because I don't have gmplayer on my system.

---

### Post by Luggy on 2005-11-26
Awesome, worked great. Thanks guys!

---

