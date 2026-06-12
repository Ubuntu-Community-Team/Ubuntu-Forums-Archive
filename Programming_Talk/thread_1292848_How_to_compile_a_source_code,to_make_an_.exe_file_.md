---
title: "How to compile a source code,to make an .exe file on linux?"
date: 2009-10-16
forum: Programming Talk
---

### Post by GrfyGrumpyBear on 2009-10-16
Well... As the title says... How and with what do i compile a source code from a windows application to make a working .exe on linux?

I have the program's source here on a folder,and it has .c .rc .h and .rbuild files,so i guess it's written in C.

I don't know also which file to compile.

I logged into my windows installation before some hours,and i tried to compile the source with the dev-c++ but i didn't get compiled any file.

I don't have any idea about programming (except html,php,asp,etc),but i'm smart enough to understand how the whole thing working.

By the way,it's an application that comes together with the ReactOS.

---

### Post by TheBuzzSaw on 2009-10-16
You cannot produce a working .exe for Linux. You can attempt to run a Windows .exe in Linux by using WINE.

You really should do more research on the matter. Do a Google search on the compiler you are using. Learn how to build large projects.

---

### Post by benj1 on 2009-10-16
> **TheBuzzSaw said:**
> You cannot produce a working .exe for Linux. You can attempt to run a Windows .exe in Linux by using WINE.

You really should do more research on the matter. Do a Google search on the compiler you are using. Learn how to build large projects.

+1 you will probably have to make changes to it so it will actually run on linux, and without programming experience thats unlikely

---

### Post by nexes128 on 2009-10-16
If the program is a .Net program you *MAY*(might require some tweaking) be able to get it to compile under mono.

---

### Post by directhex on 2009-10-16
> **nexes128 said:**
> If the program is a .Net program you *MAY*(might require some tweaking) be able to get it to compile under mono.

Except the .c files implies it's not.

Now, TECHNICALLY, you could investigate mingw32, which comes with a compiler command, i586-mingw32msvc-gcc, which compiles to Windows executables (which you can test with WINE). But it's REALLY fiddly, so good luck.

---

### Post by GrfyGrumpyBear on 2009-10-16
Ok thanks guys.

finally,after 2 days research,i successfully compiled the program on my windows xp installation.

On windows was pretty easy,but on linux it's a bit confusing.:)

The program also runs fine on Wine and it's 1000% usable. :D

---

### Post by nexes128 on 2009-10-16
> **directhex said:**
> Except the .c files implies it's not.

Now, TECHNICALLY, you could investigate mingw32, which comes with a compiler command, i586-mingw32msvc-gcc, which compiles to Windows executables (which you can test with WINE). But it's REALLY fiddly, so good luck.

lol, i should have read the whole post before i replied

---

### Post by Gorillabond on 2011-02-12
> **TheBuzzSaw said:**
> You cannot produce a working .exe for Linux. You can attempt to run a Windows .exe in Linux by using WINE.

You really should do more research on the matter. Do a Google search on the compiler you are using. Learn how to build large projects.

I  think he/she means how to compile a source code to an .exe that would work on windows

---

### Post by Quadunit404 on 2011-02-12
[IMG]http://i563.photobucket.com/albums/ss76/Quadunit404/threadnecromancer.jpg[/IMG]

---

### Post by The Cog on 2011-02-13
Yes, the thread was 16 months old, so its participants are long gone.
I'm closing the thread. 

But I will add my own note for the record that you can compile .exes on Ubuntu. I wrote this reminder for myself:
> To compile for windows:
install package mingw32
i586-mingw32msvc-gcc -Wall -o whatever.exe whatever.c


---

