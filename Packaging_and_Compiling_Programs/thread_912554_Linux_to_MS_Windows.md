---
title: "Linux to MS Windows"
date: 2008-09-06
forum: Packaging and Compiling Programs
---

### Post by Spoodt on 2008-09-06
How would one take a simple source program written in C on a Linux machine and then compile it on the same machine for a separate Windows machine? Is it possible on gcc? And if so, is gcc the best solution?

---

### Post by Claus7 on 2008-09-06
Hello, 

could you be a little more pricise on that? If you have the source code then you can compile it with the compiler you mention (using the latest version I think it's better). Doing that you will have created an output file, which if you run it in a linux box you will get the output of your program. 

Now the source code can be compiled both from a windows machine or a linux one, as long as the two different compilers in these machines do not differ a lot. Am I answering to what you are asking?

Regards!

---

### Post by Spoodt on 2008-09-11
Sorry for such a long wait for a reply. I hope you haven't forgotten about me! Well, I'm taking an intro to C class where everyone but me has a windows system. My professor would like it if I could make .exe files that would run on windows, but I don't know how to do it without using their MSVS/MSVE software, which doesn't run on my system.

---

### Post by robzon on 2008-09-11
It's possible and it's called cross-compiling. I haven't used that in practice so I can't give you any details - just google it up and you should get all the info you need.

---

### Post by fmartinez on 2008-09-11
If it's as simple as compiling a C source code you can always use Cygwin to compile the C source code. This application runs under Windows. It's what I used when I took C in school and worked great. 
Sorry I'm not too familar with cross-complining.

---

### Post by ad_267 on 2008-09-11
It's a lot simpler if you just open up your code in visual studio and compile it there on windows. If it works in Ubuntu and you're only using the default C libraries then there shouldn't be any problem compiling. You could do all of your coding and testing on Ubuntu but just compile it under Windows when you need to make a .exe file.

---

### Post by curvedinfinity on 2008-09-11
For a windows compiler, I'd recommend MSYS over Cygwin (which is slow) or Visual Studio (which uses a different tool-chain).

For cross-compiling, I've never gotten it to work. You would need a windows machine to test on, anyway, so there's no real point in cross compiling unless it is for a platform that doesn't have a native compiler.

---

### Post by fmartinez on 2008-09-11
Good suggestion curvedinfinity I forgot about Visual Studio.... and to think I just used to do some VB script. Yes Visual Studio has an option to compile C languages. I thinks it's a separate download from the MS website. I'd give that a shot. 
Good Luck.

---

### Post by inportb on 2008-09-11
Mingw is a gcc cross-compiler for Windows. See if you could get that to work.

---

### Post by jpkotta on 2008-09-11
MinGW is a minimial libc for Win32 (I think).
```
sudo aptitude install mingw32
```

Example program:
```

#include <stdio.h>

int main(void)
{
    printf("Hello World.\n");
    return 0;
}

```

Compile:
```
i586-mingw32msvc-cc hello.c -o hello.exe
```

Is it a Windows executable?
```
file hello.exe 
```
```
hello.exe: MS-DOS executable PE  for MS Windows (console) Intel 80386 32-bit
```

Seems to be so.  Can WINE run it?
```
wine ./hello.exe
```
```
Hello World.
```

I don't have a Windows installation here, so I'll just assume that it will work there too.

---

### Post by ad_267 on 2008-09-11
That's cool. I had no idea it was that easy to cross compile for windows.

---

