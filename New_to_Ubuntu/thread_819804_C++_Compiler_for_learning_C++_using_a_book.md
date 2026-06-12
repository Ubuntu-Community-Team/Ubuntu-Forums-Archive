---
title: "C++ Compiler for learning C++ using a book"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by SilverDragon on 2008-06-05
A while ago I had purchased Sams Teach Yourself C++ in 24 Hours(The title is gimmicky but it seems like a good book)

I was just curious about which C++ Compiler I could use to use this book. It comes with a CD, but I'm not exactly sure if I could get the .exe file to work under wine to install it, and finding the serial key on the site wasn't exactly simple either.

Either way using a native compiler might be best anyway?

Any insight into my inquiry would be helpful.

---

### Post by cmnorton on 2008-06-05
gcc should take care of you. You would be running linux executables.

You'll need to install build-essential. You may have to install gcc as well. Not everything runs under wine, and learning a second platform is helpful.

---

### Post by SilverDragon on 2008-06-05
I went into synaptic and gcc was already installed, maybe because I already had build-essential installed from trying to compile wine before.

I was just wondering how do I run gcc?

Is there a GUI option I need to find in synaptic or is it CLI only?

Also, in synaptic for gcc there's gcc but also gcc-3.3, gcc-3.3-base, gcc-3.3-doc, and the same things for gcc-3.4/4.1/4.2. Do I need those?

Thanks for your quick response :)

edit: I actually just asked my dad about if the compiler needed a GUI. He laughed at me. :P I'm taking that as a no :)
      Also, the window I see in the book I'm guessing is part of the IDE(Integrated Development Environment?)

---

### Post by Oldsoldier2003 on 2008-06-05
```
sudo apt-get install build-essential
``` will get all the compilers and support files you need

edit i see you have build essential, but no you don't need a gui to use gcc

---

### Post by Joeb454 on 2008-06-05
> **Oldsoldier2003 said:**
> ```
sudo apt-get install build-essential
``` will get all the compilers and support files you need

True, and after running that, lets say your source code is in /home/user/cpp
```
cd ~/cpp
g++ <file>.cpp -o <filename>
```

Obviously <file> is the name of your source file, and <filename> can be whatever :)

---

### Post by SilverDragon on 2008-06-05
Two questions:

When you use ~/cpp, can you only use that when it's a folder in /home/user/ or is that for any directory?

Also, why is it g++ instead of gcc?

---

### Post by omi291 on 2008-06-05
> **SilverDragon said:**
> 

Also, why is it g++ instead of gcc?

You use gcc when compiling C source code and g++ for C++ code

---

### Post by AndyCee on 2008-06-06
<Not strictly relevant>
Strictly speaking, you can use either gcc or g++ (try "man g++" and you'll see what I mean). But use g++ in terminal if you're learning - I used it for all my assignments at Uni. If you have multiple source files, you can try and look l33t by having four terminals open at once on your screen (I had to SSH and compile on a remonte server at the time and had to use pico for all my code)
</Not strictly relevant>

The tilde '~' refers to your home directory.
ie.

```
cd ~
```

will take you to your home directory in exactly the same way that

```
cd /home/myusername/
```
will.

If you ever want to try a gui-based compiler, two of the more popular ones are netbeans and eclipse. For a learner though, I thoroughly recommend the g++ CLI compiler.

---

### Post by SteveNorman on 2008-06-06
cd into whatever directory you saved your source code in then run the compiler. Ive never tried,,but you may be able to enter the whole path in your compile command:
```

g++ /path/to/file.cpp -o <filename>
```

try it and see....

I have a directory called prog_practice for umm..program practice(creative huh?)

My process goes:
```
cd prog_practice
vi filename.cpp
g++ filename.cpp -o compiled_filename
./compiled_filename
dance around like a monkey while the program runs


```
where vi is the text editor I use to write my code,,so it is saved automatically in my prog_practice directory

---

### Post by Trail on 2008-06-06
Obligatory mention of KDevelop as an awesome developping platform.

---

