---
title: "compiler"
date: 2005-12-26
forum: Programming Talk
---

### Post by emo on 2005-12-26
How shall I use gcc 4.0 to displays a simple "hello world" which command lines I have to type on the shell ? in windows I have to make one .exe file so linux I have no idea what I have to do .Anyone that can help me ?:confused:

---

### Post by coredump on 2005-12-26
OK, here's a rough outline of how to create a Linux executable from C source, with 'gcc'.  First, write your C program and type it into a text file:

```
#include <stdio.h>

main ()
{
   printf ("Hello, world\n");
}
```

Let's call that file 'hello.c'.  Now, you need to tell 'gcc' to compile that file, and also tell it the name of the executable file that you want (note that executable program files in Unix do not have a .exe suffix):

```
gcc -o hello hello.c
```

Then, to run the resulting program, execute the 'hello' file in the current directory:

```
./hello
```

Hope that helps!

---

### Post by lcg on 2005-12-26
Or in C++, "Hello World" would look like this:
```
#include <iostream.h>

int main(int argc, char *argv[])
{
   cout << "Hello World" << endl;
   return 0;
}
```
Save it as hello.cpp and use 'gcc hello.cpp -o hello' to compile.

And in my favorite, Ada95:
```
-- Hello World
with Ada.Text_IO;
use Ada.Text_IO;

procedure HelloWorld is
begin
   Put_Line("Hello World");
end HelloWorld;
```
Save this one as helloworld.adb and use 'gnatmake helloworld.adb'. However, Ada95 needs the gnat(-4.0) package to compile.

HTH,
Lars

---

### Post by CompiledMonkey on 2005-12-26
And my favorite, MIPS assembly:

```

# Program that displays "Hello World!" to the console

# Data
        .data
dis:	.asciiz   "Hello World!"


# Text
        .text
main:

# show "dis" message on screen
        la      $a0, dis
        li      $v0, 4
        syscall

# exit program service
        li      $v0, 10
        syscall

```

---

### Post by lcg on 2005-12-26
[QUOTE=CompiledMonkey]And my favorite, MIPS assembly:[/QUOTE]
Nice one! :)

But then again, it isn't really compiled, so you cheated. ;)

Lars

---

### Post by CompiledMonkey on 2005-12-26
[QUOTE=lcg]Nice one! :)

But then again, it isn't really compiled, so you cheated. ;)

Lars[/QUOTE]

:razz: :cool: 

I just got Ubuntu installed so I can do some NASM for my Athlon XP chip.

---

### Post by lcg on 2005-12-26
[QUOTE=CompiledMonkey]I just got Ubuntu installed so I can do some NASM for my Athlon XP chip.[/QUOTE]
Uh, x86 assembly. Why not just ask someone to whip you? Might be easier and someone else could have some fun, too. ;)

Lars

---

### Post by CompiledMonkey on 2005-12-26
Haha, true...

Well, I'm taking an assembly course this semester based around MIPS.  I got a little bit of a head start and have been really interested so far.  I'm hoping I'll find some spare time to learn some Athlon XP specific stuff.

---

### Post by thumper on 2005-12-27
Actually minimal C++ one is
```

#include <iostream>
int main()
{
   std::cout << "Hello World!\n";
}

```:)
Although if you are also wanting good style, then add the 
```
return 0;
```

---

### Post by m87 on 2005-12-28
[quote=CompiledMonkey]Haha, true...

Well, I'm taking an assembly course this semester based around MIPS.  I got a little bit of a head start and have been really interested so far.  I'm hoping I'll find some spare time to learn some Athlon XP specific stuff.[/quote]

useful :)
MIPS assembly, I mean

---

