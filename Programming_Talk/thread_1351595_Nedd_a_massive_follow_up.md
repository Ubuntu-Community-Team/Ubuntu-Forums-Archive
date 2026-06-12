---
title: "Nedd a massive follow up"
date: 2009-12-10
forum: Programming Talk
---

### Post by Miansc on 2009-12-10
Hey guys. I've been using ubuntu now for a few months and I'm loving it. Anyway, back in window$, I was using MVS to code miny dos apps.. mainly to just learn c++.

Now,  my questions are, What are ubuntu applications codded in? Like when I download something, I see like something.unix, the the make file etc....

Then when I go to the add/remove apps, it just installs automatically. So, what format are those files in?

Also, is there a native linux coding... 

Whats a good app too to create c++ programs and to make graphical user interfaces?

Thanks heaps! :D

---

### Post by lisati on 2009-12-10
MVS on Windows? I've only ever used that OS on IBM mainframes. Were you running it in a VM? :)

---

### Post by Miansc on 2009-12-11
Microsoft visual studio lol?

---

### Post by lisati on 2009-12-11
> **Miansc said:**
> Microsoft visual studio lol?

Oh! Definitely LOL! The joys of acronyms! :)
(/me thinks how "FCB" on an IBM mainframe can mean something different to "FCB" in a program for CP/M or MS-DOS)

---

### Post by bamsanks on 2009-12-11
> **Miansc said:**
> Microsoft visual studio lol?
Is MVS a widely used acronym for Microsoft Visual Studio?

---

### Post by Zugzwang on 2009-12-11
> **Miansc said:**
> Hey guys. I've been using ubuntu now for a few months and I'm loving it. Anyway, back in window$, I was using MVS to code miny dos apps.. mainly to just learn c++.

Now,  my questions are, What are ubuntu applications codded in? Like when I download something, I see like something.unix, the the make file etc....


There are a couple of languages available and some stuff installed automatically with your Ubuntu is written in the one language and some in the other.

Perhaps the following post helps you as it contains further explanaition. Note that the Kdevelop tutorial contained is a little bit outdated: [http://ubuntuforums.org/showthread.php?t=1258665](http://ubuntuforums.org/showthread.php?t=1258665)

> **Miansc said:**
> 
Then when I go to the add/remove apps, it just installs automatically. So, what format are those files in?

Also, is there a native linux coding... 


These are so called "deb" files. These are similar to .zip files with some additional control information on where to install stuff, etc. (Basically they are two .tar.gz files stapled together. One contains the data, one the control stuff). See the "Debian packaging guide" for details.

> **Miansc said:**
> 
Whats a good app too to create c++ programs and to make graphical user interfaces?


This topic is covered in the "stickies" of this forum. Also, see the post I've mentioned above for details. However, the tutorial itself is outdated, just have a look at the explanaitions.

> **bamsanks said:**
> Is MVS a widely used acronym for Microsoft Visual Studio?

No, it isn't. People usually use "MVC" although strictly speaking this just refers to the "Visual C++"-Part of the studio suite.

---

### Post by Miansc on 2009-12-11
> **Zugzwang said:**
> There are a couple of languages available and some stuff installed automatically with your Ubuntu is written in the one language and some in the other.

Perhaps the following post helps you as it contains further explanaition. Note that the Kdevelop tutorial contained is a little bit outdated: [http://ubuntuforums.org/showthread.php?t=1258665](http://ubuntuforums.org/showthread.php?t=1258665)



These are so called "deb" files. These are similar to .zip files with some additional control information on where to install stuff, etc. (Basically they are two .tar.gz files stapled together. One contains the data, one the control stuff). See the "Debian packaging guide" for details.



This topic is covered in the "stickies" of this forum. Also, see the post I've mentioned above for details. However, the tutorial itself is outdated, just have a look at the explanaitions.



No, it isn't. People usually use "MVC" although strictly speaking this just refers to the "Visual C++"-Part of the studio suite.


Thanks a lot ;)

```
Now... when I wrote dos apps, for example.

#include <iostream>

void hello() {
    std::cout << "Hello world!\n";

```

That would pop up a dos window saying that... in ubuntu, will that open up the terminal? Meaning if I write things that work in the ms-dos in windows, will they work the same in the terminal?

Is compiling the same too? When comping in windows it becomes a .exe   .. in ubuntu do I compile to a .deb? 

Thanks for answering, it is helping me greatly. I will also read your post now ;)
[COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]

---

### Post by nvteighen on 2009-12-11
> **Miansc said:**
> Thanks a lot ;)

```
Now... when I wrote dos apps, for example.

#include <iostream>

void hello() {
    std::cout << "Hello world!\n";

```

That would pop up a dos window saying that... in ubuntu, will that open up the terminal? Meaning if I write things that work in the ms-dos in windows, will they work the same in the terminal?

Is compiling the same too? When comping in windows it becomes a .exe   .. in ubuntu do I compile to a .deb? 


1) That code won't compile. C and C++ require you to write a main function whose signatures can be:
```

int main(void)

```
or
```

int main(int, char **)

```

2) Nope, you don't get a .deb. .debs are installing packages, not programs, similar to self-extracting .zips in Windows. You get an ELF executable; ELF is the format used by the Linux kernel (and BSD-based OSs?) for executable files, while Windows uses another called PE. ELF executables usually don't have any extension.

3) The terminal won't open up. You have to start the terminal first and run the program from there.

---

### Post by Miansc on 2009-12-11
> **nvteighen said:**
> 1) That code won't compile. C and C++ require you to write a main function whose signatures can be:
```

int main(void)

```or
```

int main(int, char **)

```2) Nope, you don't get a .deb. .debs are installing packages, not programs, similar to self-extracting .zips in Windows. You get an ELF executable; ELF is the format used by the Linux kernel (and BSD-based OSs?) for executable files, while Windows uses another called PE. ELF executables usually don't have any extension.

3) The terminal won't open up. You have to start the terminal first and run the program from there.


WRONG CODE, accident.. besides the point. I ran a hello worlf from kdev, it opened in terminal? Anyway what about making guis? How do i do that?

Thanks ;)

---

### Post by nvteighen on 2009-12-11
> **Miansc said:**
> WRONG CODE, accident.. besides the point. I ran a hello worlf from kdev, it opened in terminal? Anyway what about making guis? How do i do that?

Thanks ;)

KDevelop, I suppose... Well, IDEs handle that for you... and I'm not sure about KDE either. I just know GNOME won't open the terminal for you.

GUIs are essentially done by using data structures and functions from GUI toolkit libraries such as GTK+ (GNOME & Xfce) and Qt (KDE). Though it's better to learn to build them by coding them by hand, GUI designers are usually used to build the GUI visually and just the "controller" code is written (the one that interfaces your GUI with your "backend" or "model"). This is a bit more advanced topic, so you better forget about that for now.

---

### Post by Miansc on 2009-12-12
> **nvteighen said:**
> KDevelop, I suppose... Well, IDEs handle that for you... and I'm not sure about KDE either. I just know GNOME won't open the terminal for you.

GUIs are essentially done by using data structures and functions from GUI toolkit libraries such as GTK+ (GNOME & Xfce) and Qt (KDE). Though it's better to learn to build them by coding them by hand, GUI designers are usually used to build the GUI visually and just the "controller" code is written (the one that interfaces your GUI with your "backend" or "model"). This is a bit more advanced topic, so you better forget about that for now.

Right, ok. I just wanted to make like, a simple blackjack game. With a random number generator, variables like you're score, cash etc... And to design a new gui along with it. I guess Ill stick to dos/terminal for now until I become better.

Ty. ;)

---

### Post by nvteighen on 2009-12-12
> **Miansc said:**
> Right, ok. I just wanted to make like, a simple blackjack game. With a random number generator, variables like you're score, cash etc... And to design a new gui along with it. I guess Ill stick to dos/terminal for now until I become better.

Ty. ;)

Hm... try to do it this way. It's a nice experiment I've done myself a couple of times:
1) Create a backgammon library where you model all what's needed in a backgammon game, making it 100% independent of the user interface. Anything that relates to how this will look after should be left outside; only write stuff essential to the game's nature into useful functions and classes. Make it richful, but don't add unnecessary features. (When I mean "library", I'm talking about the concept, not that you should compile this into a static/dynamic library... No, leave it as a source file and compile it straight with the rest of your program).
2) Create a text interface (a "client") by using the stuff written in your library. If you find a lack in your library (you'll find them), fix it, but always respecting its independence from the user interface.
3) Later, when you've learned about GUIs, replace the text interface with a GUI. If you've done things right, you shouldn't touch anything in the library's architecture (unless it's a bug, of course). When modularization has been correctly done, replacing an interface (not only user interfaces...) is like plugging something off a socket and plugging something else in.

It's a bit difficult at the beginning and needs a lot of trial and error (specially in step 2), because when building your library sometimes you don't have a chance to test it. The key is to separate tasks as much as you can... 1 function = 1 task, 1 class = 1 purpose

---

### Post by Miansc on 2009-12-12
> **nvteighen said:**
> Hm... try to do it this way. It's a nice experiment I've done myself a couple of times:
1) Create a backgammon library where you model all what's needed in a backgammon game, making it 100% independent of the user interface. Anything that relates to how this will look after should be left outside; only write stuff essential to the game's nature into useful functions and classes. Make it richful, but don't add unnecessary features. (When I mean "library", I'm talking about the concept, not that you should compile this into a static/dynamic library... No, leave it as a source file and compile it straight with the rest of your program).
2) Create a text interface (a "client") by using the stuff written in your library. If you find a lack in your library (you'll find them), fix it, but always respecting its independence from the user interface.
3) Later, when you've learned about GUIs, replace the text interface with a GUI. If you've done things right, you shouldn't touch anything in the library's architecture (unless it's a bug, of course). When modularization has been correctly done, replacing an interface (not only user interfaces...) is like plugging something off a socket and plugging something else in.

It's a bit difficult at the beginning and needs a lot of trial and error (specially in step 2), because when building your library sometimes you don't have a chance to test it. The key is to separate tasks as much as you can... 1 function = 1 task, 1 class = 1 purpose


That should be usefull to me in the future.. bit advanced now but thanks!!

---

