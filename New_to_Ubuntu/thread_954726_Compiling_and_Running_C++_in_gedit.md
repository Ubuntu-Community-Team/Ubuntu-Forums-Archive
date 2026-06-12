---
title: "Compiling and Running C++ in gedit"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Optimus_Jazz on 2008-10-21
I am tring to compile and run c++ programs in gedit but so far im having know luck.

I know there is a way to do this in the terminal but to me this seems ridiculous because with Dev and other compilers all i have to do it go to the task bar,click compile and run the .exe

My lecturer in college uses Ubuntu and he seems to be able to compile and run the program in a window that pops up but have not managed to ask him and it is important i get this sorted tonight.

Thank you for any help given.

---

### Post by Crandom on 2008-10-21
using notepad or gedit for any type of programming is very 1990's - i suggest you open a terminal and type in:

sudo apt-get install monodevelop

to install an IDE called MonoDevelop. Go to Applications > Programming > MonoDevelop and start a new c++ project. Type in the code then build the project. Voila.

To compile from the terminal you can use the gcc command or something. I personally have never needed to, being a c# programmer.

Also, you won't get a .exe but a file without an extension. Exe's are only for windows.

---

### Post by Optimus_Jazz on 2008-10-21
cool so monodevelop will basically cater for what i need?

---

### Post by eye208 on 2008-10-21
MonoDevelop is an IDE for C# which can also handle C/C++ projects although this is not its main focus. Similarly, Eclipse is an IDE for Java which can also handle C/C++.

If your main focus is C/C++, try Anjuta.

---

### Post by Sinkingships7 on 2008-10-21
> **Optimus_Jazz said:**
> cool so monodevelop will basically cater for what i need?

That depends on your specific needs. I suggest trying many different IDE's/editors and see which one you like the most. I prefer Geany for hacking Python and some C, while I favor NetBeans/Eclipse for Java/C++ programming.

I don't know if MonoDevelop comes with its own compiler and whatnot, but just in case you get tons of errors, you probably need this:

```
sudo aptitude install build-essential
```

---

### Post by Optimus_Jazz on 2008-10-21
I have tried installing these programs and i am either getting errors or they're just too complicated for my liking,so can anybody out there please explain to me how:

 To compile and run C++ programs through gedit, WITHOUT  having to enter commands into the terminal.

I have added an option of "Build" into the tools but when i use it, "No makefile found" is displayed

---

### Post by Sinkingships7 on 2008-10-21
> **Optimus_Jazz said:**
> I have tried installing these programs and i am either getting errors or they're just too complicated for my liking,so can anybody out there please explain to me how:

 To compile and run C++ programs through gedit, WITHOUT  having to enter commands into the terminal.

I have added an option of "Build" into the tools but when i use it, "No makefile found" is displayed

You can't. Gedit is an editor, not specifically designed for programming. If you install Geany with

```
sudo aptitude install geany
```

then you'll get what you're looking for. It's lightweight, takes only seconds to install. You write the program, SAVE THE FILE (very important), then press F8 to compile, F9 to build, and F5 to run your program. Very simple, very straightforward.

---

### Post by Joeb454 on 2008-10-21
> **Crandom said:**
> using notepad or gedit for any type of programming is very 1990's

Not true, I do a lot of coding using vim. I'll either use 2 or 3 terminal tabs (which is more convenient) or if that's not practical, I'll use screen instead.

Also for C/C++ IDE's I would also recommend geany or anjuta

---

### Post by Optimus_Jazz on 2008-10-21
> **Sinkingships7 said:**
> You can't. Gedit is an editor, not specifically designed for programming. If you install Geany with

```
sudo aptitude install geany
```

then you'll get what you're looking for. It's lightweight, takes only seconds to install. You write the program, SAVE THE FILE (very important), then press F8 to compile, F9 to build, and F5 to run your program. Very simple, very straightforward.

Fantastic,THANK YOU!

---

### Post by DragonM on 2010-11-21
Try this Site below. Even though he does it in C I think it's a good start for you.

[http://www.dreamincode.net/forums/topic/63945-game-programming-in-linux-for-windows-programmers-part-1/]("http://http://www.dreamincode.net/forums/topic/63945-game-programming-in-linux-for-windows-programmers-part-1/")

Happy Coding

---

