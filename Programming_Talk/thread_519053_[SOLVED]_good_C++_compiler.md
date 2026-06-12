---
title: "[SOLVED] good C++ compiler"
date: 2007-08-06
forum: Programming Talk
---

### Post by bribaetz on 2007-08-06
if some one could give me a site name that would be awesome i love C++ and need one for Ubuntu cause all i can find is for mac other Linux or windows.not Ubuntu Linux so i need a deb file

---

### Post by Wybiral on 2007-08-06
Compiler? G++ (the GCC C++ compiler) is basically standard for Linux.

---

### Post by Steveway on 2007-08-06
$sudo apt-get install build-essential
That should install gcc for you.

---

### Post by init1 on 2007-08-06
> **bribaetz said:**
> if some one could give me a site name that would be awesome i love C++ and need one for Ubuntu cause all i can find is for mac other Linux or windows.not Ubuntu Linux so i need a deb file
Do you want a IDE, or is command line fine for you? GCC is probably the best option.

---

### Post by bribaetz on 2007-08-06
so does the compiler build automatically when you save code from a text document text editor so wich langueges can i compile from text editor
what do i save the file as and i done that command

---

### Post by Skardal on 2007-08-06
The compiler never build an application unless it's told to! That means, it has no connection to the text-editor.

You're probably looking for an IDE, which can be configured to build upon save. I would recommend Eclipse with the C++ extension. ([CDT]("http://www.eclipse.org/cdt/"))

And..
> 
so does the compiler build automatically when you save code from a text document text editor so wich langueges can i compile from text editor
what do i save the file as and i done that command

It seems to me like you're pretty new to programming. (It wasn't too easy to understand that sentence :P). If this is the case, then you really should go through a step by step tutorial for creating a c++ program and compile it.

Check the[ sticky-post]("http://ubuntuforums.org/showthread.php?t=333867")!

---

### Post by bribaetz on 2007-08-06
so anyone what should i do im not exactly new i just need a c++ compilere im new to ubuntu

---

### Post by Nekiruhs on 2007-08-06
> **bribaetz said:**
> so anyone what should i do im not exactly new i just need a c++ compilere im new to ubuntu
I think you have your terms mixed up. A compiler takes already written source files an converts them to machine readable executables. An IDE is an Integrated Developement Environment. An IDE usually has a compiler as part of it, but not always. An IDE is a beefed up text editor with tools for the language. I think you need Eclipse with a C++ plugin.

---

### Post by Note360 on 2007-08-06
> **bribaetz said:**
> so anyone what should i do im not exactly new i just need a c++ compilere im new to ubuntu

G++ is the c++ compiler for linux and osx (I think). It is standard and it works. type
```
sudo aptitude install build-essential
```
the terminal.

---

### Post by bribaetz on 2007-08-06
> **Nekiruhs said:**
> I think you have your terms mixed up. A compiler takes already written source files an converts them to machine readable executables. An IDE is an Integrated Developement Environment. An IDE usually has a compiler as part of it, but not always. An IDE is a beefed up text editor with tools for the language. I think you need Eclipse with a C++ plugin.yeh i programm in other langueges that dont require a  compiler thats what i need [eclipse/]("http://download.eclipse.org/tools/cdt/releases/callisto/dist/3.1.2/")
does not have a deb file though

---

### Post by Nekiruhs on 2007-08-06
> **bribaetz said:**
> yeh i programm in other langueges that dont require a  compiler thats what i need [eclipse/]("http://download.eclipse.org/tools/cdt/releases/callisto/dist/3.1.2/")
does not have a deb file though
Its in the repos. Why do you seem to be avoiding the repositories like the plague?

---

### Post by Note360 on 2007-08-06
> **bribaetz said:**
> yeh i programm in other langueges that dont require a  compiler thats what i need [eclipse/]("http://download.eclipse.org/tools/cdt/releases/callisto/dist/3.1.2/")
does not have a deb file though


Urm learn to use somethign we call "apt". I would suggest getting used to Synaptic.

---

### Post by bribaetz on 2007-08-06
> **Nekiruhs said:**
> Its in the repos. Why do you seem to be avoiding the repositories like the plague?

no but im new to linux and ubuntu and all this operating system that i have very little expieriance with and have no idea what you are talking about

---

### Post by bribaetz on 2007-08-06
> **Note360 said:**
> Urm learn to use somethign we call "apt". I would suggest getting used to Synaptic.

apt i have heard of that before but cant put my finger on it and the synaptic i cant seem to figure out wat your saying
um just found it not apt synaptic now where is that eclipse at

---

### Post by Note360 on 2007-08-06
ok hit

alt-F2 then type gnome-terminal a terminal should pop up. Now since your new i think synaptic is better so type
```

sudo synaptic

```
at the prompt. That will bring up a nice gui to apt. its basically a collection of all the packages supported by the ubuntu team. its pretty simple so i think you can get around in it.

---

### Post by bribaetz on 2007-08-06
i found synaptic already so i got it thank you so very very much

---

### Post by Note360 on 2007-08-06
ah no problem. I would suggest using the terminal version, but that is a little less than self explanatory. Eventually youll be using everything jsut as good as any of us.

Just a warning also install build-essential

---

### Post by bribaetz on 2007-08-06
why exactly

---

### Post by Nekiruhs on 2007-08-06
> **bribaetz said:**
> why exactly
Build essential is a compiler.

---

### Post by Note360 on 2007-08-06
build essential isnt a compiler. It is a collection of all the tools you need to compile and build applications (like gcc/g++ which are compilers and make which is a make system and some other stuff)

---

### Post by bribaetz on 2007-08-06
thank you for your help

---

### Post by PandaGoat on 2007-08-06
Is English your second language?  I have to ask because your word choice sounds pretty good, but your lack of grammar makes my eyes bleed.


To get Eclipse with C++ support **open the terminal** and **type:**
```

sudo apt-get install eclipse-cdt

```

---

### Post by bribaetz on 2007-08-06
no but i do feel that grammar online is a waste of time considering i dont type 60wpm maybe 30wpm i dont touch type either

---

### Post by Lord Illidan on 2007-08-06
Geany is also a nice IDE, and very simple too. Eclipse might be a bit confusing..

Also available from synaptic.

---

### Post by PandaGoat on 2007-08-06
Using your grammar skillz online is not a waste of time.  You get good practice.  And please do it out of courtesy.  People do have to read your posts.  No grammar makes it hard to tell what parts of your sentence[?] stop and which begin a new idea.

---

### Post by bribaetz on 2007-08-06
sorry, is this better. just picking i will try.
oh where does eclipse show up at. i cant find it.
it did not show up in programming.

---

### Post by bribaetz on 2007-08-06
> **Lord Illidan said:**
> Geany is also a nice IDE, and very simple too. Eclipse might be a bit confusing..

Also available from synaptic.

how would i find eclipse its not on my applications menu ive searched it.

---

### Post by CptPicard on 2007-08-06
Sheesh, stop picking on him when it is clear what problems he's having (that is, not being used to Linux-style concepts). This is quite the "humiliate the n00b"- thread :)

I'm not sure where Ubuntu installs its own Eclipse package (I just always get the tar and unpack to /opt), but you should be able to just run it by doing an alt-F2 and typing "eclipse" (I assume it's put into the path). I'm a bit surprised it doesn't show up in a menu, maybe the GUI needs to be relaunched?

As an added bonus, you might take up a console, write "which eclipse", note the path you get to the executable and then make a launch button for it in your window manager so you get nice graphical access to it...

---

### Post by bribaetz on 2007-08-06
alt-f2 it says the location or file could not be found i typed in eclipse-cdt

---

### Post by Lord Illidan on 2007-08-06
Applications -> Programming -> Eclipse, maybe? That's where it is on mine.

---

### Post by bribaetz on 2007-08-06
thats what im saying its not there but it says its installed when i search for it it says could not locate or some bs

---

### Post by Lord Illidan on 2007-08-06
Hmm, try running it from a terminal.

---

### Post by bribaetz on 2007-08-06
whats the command for it

---

### Post by CptPicard on 2007-08-06
"eclipse" ;)

---

### Post by bribaetz on 2007-08-06
how do i run it from the terminal> bash eclipse no such file or directory

---

### Post by bribaetz on 2007-08-06
where is the folder that contains the program

---

### Post by bribaetz on 2007-08-06
is there another compiler and ide please this wont work

---

### Post by bribaetz on 2007-08-06
> **Lord Illidan said:**
> Geany is also a nice IDE, and very simple too. Eclipse might be a bit confusing..

Also available from synaptic.

your ide i am using right now
i need a compiler for you ide

---

### Post by bribaetz on 2007-08-06
thanx i got it

---

### Post by Lord Illidan on 2007-08-07
To run anything from a terminal, it's usually just

```
eclipse
``` not```
 bash eclipse
```.

Geany is quite easy to use, hope you like it.

---

### Post by bribaetz on 2007-08-07
ok screw eclipse

---

### Post by xtacocorex on 2007-08-07
If you only installed the eclipse-cdt package, you only got a plugin; you probably need to install the actual IDE. 
From the terminal:
```
sudo apt-get install eclipse
```

You don't need an IDE to use the compilers, they work from the command line.  The sticky threads at the beginning of the subforum contain a plethora of information you should look into.

---

### Post by bribaetz on 2007-08-07
i prefer an ide it makes it quicker and easier

---

### Post by bEpo0o on 2007-08-08
u can try  Netbeans IDE with C/C++ pack. To get the .bin files download it from [http://netbeans.org](http://netbeans.org). Install the IDE then install the C/C++ pack.

---

### Post by bribaetz on 2007-08-08
nah i dont need it i got a good one now

---

