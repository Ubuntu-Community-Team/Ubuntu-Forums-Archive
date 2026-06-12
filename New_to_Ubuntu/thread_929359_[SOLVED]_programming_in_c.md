---
title: "[SOLVED] programming in c"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by mihid on 2008-09-24
so I just switched over to ubuntu from windows and I am trying to create a basic hello world program, I installed the build-essential thing and I can get my program written in the text editor to compile without any errors however when I try to run it I think I'm missing the run window lol :(.
```

#include <stdio.h>
int main(void)
{
printf("Hello world!\n");
return(0);
}

```
I'm using 
```

gcc program.c -o program

``` In terminal to attempt to run it but I seem to be missing where the output is :(.
any help would be great thanks :)

---

### Post by iaculallad on 2008-09-24
Try:

Source file: program.c

Compile the code:

```
cc -c program.c
```

Doing that will produce the object file of your source file. To create an executable:

```
cc -o program program.c
```

To execute it:

```
./program
```

---

### Post by wolterh on 2008-09-24
Well.. in ubuntu programs do not run in console by default, so you have to start a terminal and run it from there. But easy there tiger, you have to 'cd' into the directory where the binary is, and then type:
./application
Where application is to be replaced with the name of your executable (I think in your case is program)

---

### Post by TriSwords on 2008-09-24
You need ./program to run it.

---

### Post by ByteJuggler on 2008-09-25
Just as some added illumination: The reason for needing "./blah" to run a program called "blah" in the current directory, is because the current folder is not on the search path by default.  This is a security precaution, to help prevent spoof programs put in system writable locations (e.g. /tmp) that might otherwise accidentally get run instead of normal system programs  by the "root" account.

---

### Post by AndrewTheArt on 2008-09-25
When I program in C, I used Geany.

1. ```
sudo apt-get install geany
```2. Open Geany, click File -> New (With Template) -> C Source File
3. <write code>
4. File -> Save As, then save it
5. Back in the main Geany window, go to Build -> Set Includes and Arguments
6. Make sure it looks like this - 

Compile: gcc %f -o %e
Build: gcc %f -o %e
Execute: "./%e"

7. You're done. Now you can click Compile, then Execute. It will launch your prog in a window.

---

### Post by Primefalcon on 2008-09-25
To run a compiled program that has console output you need to open up the terminal and switch to its location using the cd command, 

If you need help on using the cd command, type ```
man cd
``` into your terminal.

once your in the same location as your program type

```
./program_name
```

you need to have the ./ before it.

---

### Post by mihid on 2008-09-25
awesome many thanks guys :-D

---

### Post by superprash2003 on 2008-09-25
you could also use the turbo c (which is very popular in windows) in linux.
[http://prash-babu.blogspot.com/2008/09/how-to-get-turbo-c-compliler-to-work-in.html](http://prash-babu.blogspot.com/2008/09/how-to-get-turbo-c-compliler-to-work-in.html)

---

