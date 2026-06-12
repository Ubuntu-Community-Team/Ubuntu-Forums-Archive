---
title: "C++ compiler???"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by malaya on 2008-05-16
im studying c++ and i dont know what compiler is available in ubuntu..

-can i use gcc or g++ ??
-how do i call the compiler??
-how does it look like, does it look like a visual c++/ devc++/ turbo c++ ??
(this compiler is what i used before)

- i really need it, and i prefer to have a GUI c++ compiler??
- please recommend me one.. thanks to all...

---

### Post by Joeb454 on 2008-05-16
It's g++ and you use it from a terminal I believe.

Lets say your programs where in a folder in your home directory called apps, then you would open a terminal and run (one line at a time) ```
cd ~/apps
g++ <filename>.cpp <options>
```

where <filename> is obviously the name of the file, and <options> are any options for compiling that you want.

There *may* be a GUI compiler out there, though I'm not sure

---

### Post by pedro_orange on 2008-05-16
```
sudo apt-get install build-essential
```

Get that. Now you've got g++/gcc etc.

Make a hello_world.c save it someplace.

Open a terminal a cd to the directory that .c is located.

```
g++ -Wall -pedantic hello_world.c -o hello.o
```

In that terminal command we're saying, compile hello_world.c using ISO standard c++ rules (-pedantic flag) and show me all warnings (-Wall), and in doing so create an output file called hello.o

To run our program type:

```
./hello.o
```

That says run hello.o located in the current directory.

G++ is a Command line compiler. And it's great. 
You can get a nice plug-in for Gedit so you can actually use that as an IDE (With language highlighting/built-in terminal) 
Who needs Visual Studio / Geany / Eclipse when you have Gedit & Terminal? 

:lolflag:

There are IDEs that sort the compiling out for you. Like the ones mentioned above (sans VS) 
But you'll learn more from using G++
Especially when it comes to making your own Makefiles...

Good luck

---

### Post by niteshifter on 2008-05-16
Hi,

There are other C++ compilers around (Intel, for example) but g++ is going to be the better choice for GNU/Linux (Ubuntu). As to a GUI programming environment there are C/C++ plugins for Eclipse and Netbeans. There's Bluefish ... and Xemacs ... there's a lot of Integrated Development Environments (IDEs) around. Search around, look at some screenshots, try some, see what you like. IDEs are very subjective choices. Myself, I use Netbeans - it's kind of like MS's Visual Studio in layout (as best as I remember, it's been a few years since I coded in the MS world).

---

### Post by malaya on 2008-05-16
- many many thanks

---

### Post by gg234 on 2008-05-16
If you want more example how to compile c++ programs check this [http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

---

