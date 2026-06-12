---
title: "How do I compile source code?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by moniker127 on 2008-11-10
Howdy folks. I'm very new to using Ubuntu, infact, I just downloaded 8.10 earlier this week. 

What I am curious about is how I compile source code. I'm not particularly interested in actually coding stuff, I just want applications to run, and half of them I need to compile first, for some inexplicable reason. 

Pretty much right now I just want to have a 3d desktop, and to be able to play Tabula Rasa. Id really appriciate any guides you have, as I've tried googling it for a few days and I always end up banging my head against the wall. 

Anyway, please make no assumptions as to what I know about Ubuntu, because I really don't know anything about Linux. At all. I'm interested in learning, but I need to have something to build my knowledge off of. I need to be able to make a hole in the brick wall before I can realize that its breakable, because thats where i'm at right now.

---

### Post by binbash on 2008-11-10
It depends of the source code.You should read README which mostly comes with the source package.

but mostly 

$./configure
$make
$sudo make install

---

### Post by ad_267 on 2008-11-10
> Pretty much right now I just want to have a 3d desktop, and to be able to play Tabula Rasa. Id really appriciate any guides you have, as I've tried googling it for a few days and I always end up banging my head against the wall.


Neither of those things require compiling source code.

For the 3D desktop read: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Tabula Rasa is a Windows game. It won't run natively on Linux. According to this page it should run in Wine, a compatibility layer that can run many Windows programs (pretty amazing really). [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5562](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5562)

This is also good to read: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by moniker127 on 2008-11-10
Well, thats the thing. I'm very much down with reading read-mes, but I havnt been able to decrypt a lot of them. For example, here is the readme file from ULL (Universal Linux Launcher for NCSoft(makers of tabula rasa) games):

```

Universal Linux Launcher for NCSoft Games
(C) 2008 AJackson

To build
========

Compile the ULL executable using

./configure
make
make install (as super user)

```

I open up the terminal, type in ./configre, it says this:
```

bash: ./configure: No such file or directory

```
So, I figure, Okay... probably not a terminal command. So I navigate to the trlinux folder where I extracted the .tar.bz2, and I find a file called configure. I figure this must be what the readme is refering to, so I double-click it, click on "run in terminal". I notice a few files in the directory move around. I'm not sure if I did this the right way, but ****, atleast something happened.
Now, I go back to the terminal, type in make, the terminal says:
```

make: *** No targets specified and no makefile found.  Stop.

```
I figure... okay... maybe I need to find the file first. So, I do CD ~Desktop/trlinux. Then, I type make again. Same result. I figure, there must be some way of setting the target in the command. I dont really know what i'm supposed to be targeting, but the command did say "no makefile", so I look for something like that in the trlinux folder. I find "makefile.in" and "makefile.am". I try make makefile.in, and then make makefile.in. Neither works. The shell says:
```

make: *** No rule to make target `makefile.am'.  Stop.

```
I figure... okay... well... ****. Why didnt they just let me download a program?

---

### Post by OutOfReach on 2008-11-10
> 
So, I figure, Okay... probably not a terminal command. So I navigate to the trlinux folder where I extracted the .tar.bz2, and I find a file called configure. I figure this must be what the readme is refering to, so I double-click it, click on "run in terminal". I notice a few files in the directory move around. I'm not sure if I did this the right way, but ****, atleast something happened.
Goto into a terminal first, change directories to where the configure file is and then type in ./configure
And see if it succeeds or fails.

---

### Post by ad_267 on 2008-11-10
Ok if you have to compile something then basic knowledge of the terminal is a good idea. 

Have a read of these: [http://linuxcommand.org/lts0020.php](http://linuxcommand.org/lts0020.php), [http://linuxcommand.org/lts0030.php](http://linuxcommand.org/lts0030.php)

You need to use "cd /path/to/directory/" to change into the directory where the configure script is located. Then when you run the ./configure command it will run a configuration script, this produces the makefile which is used when you run make. The problem is that the configure script is most likely encountering errors because you are missing required packages. It will give an error and say what libraries are missing. You have to actual run the command from the terminal so you can see the output and see what these errors are. You can install the missing packages by searching for them in the Synaptic package manager and make sure you get the development libraries, the ones with "-dev" on the end.

---

### Post by Iowan on 2008-11-10
Before you start compiling stuff, first check repositories to see if there is already a package. Much less painful - unless you just want the experience.

---

### Post by chrisod on 2008-11-10
I've been on Ubuntu for at least two years and I can count on one or two fingers the number of times I've needed to compile code. Just about everything you could want, and certainly anything a complete newbie needs, is available in the repositories or as a .deb file, which will one click install much like a .exe file in Windows.

If you've been on Ubuntu a week why are already trying to force Windows games to run. Give open source a chance.

---

### Post by moniker127 on 2008-11-11
Many thanks folks. I did eventually figure it out, after several cans of NOS.  

> **chrisod said:**
> 
If you've been on Ubuntu a week why are already trying to force Windows games to run. Give open source a chance.

Are you suggesting that I just NOT download tabula rasa because it isnt open source? If so I wonder if you've ever played a game in your life. :P

---

### Post by Sealbhach on 2008-11-11
Nice tutorial here:

[Compiling Made Easy]("http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy")

Follow the example, it includes most of the pitfalls you will encounter.


.

---

### Post by 3rdalbum on 2008-11-11
The reason why you can't just download an executable version of this program is because there is no way to compile a program so it will run on all the different architectures that Linux can run on.

Windows runs on exactly one CPU architecture: ia32. Linux runs on a massive array of architectures; ia32, ARM, MIPS, SPARC, PowerPC, Itanium, and many more. They all use different instructions.

Therefore, on Windows you can have a binary program that will always be able to run no matter what your system - because if you are running Windows, you have an ia32 processor. On Linux, you can't just have a binary program that will always run, because you might have a processor that doesn't understand ia32 instructions. Windows had the same problem when it supported Itanium processors; the people running Windows on Itanium couldn't get any programs for it, because no Windows-based developer distributes source code!

Source code can almost always be compiled for a different CPU, so that's why source code is so popular on Linux. You do sometimes come across binary installers for Linux but they are not popular with users, and are completely useless for people not on ia32.

Always look in the Synaptic Package Manager first, because it always has programs that have been compiled for your CPU architecture and are just two clicks away from installing. I appreciate that you can't exactly do that for Tabula Rasa because it's a Windows program, but check that it is supported on [www.winehq.org](www.winehq.org)

---

### Post by steveneddy on 2008-11-11
> **moniker127 said:**
> 


Are you suggesting that I just NOT download tabula rasa because it isnt open source? If so I wonder if you've ever played a game in your life. :P

](*,)

Maybe the first two links in my sig will educate you a little. Of course, you have to read the pages after you click the links.

Also try looking at the link in my sig labeled "Compiz"

---

### Post by moniker127 on 2008-11-11
> **steveneddy said:**
> ](*,)

Maybe the first two links in my sig will educate you a little. Of course, you have to read the pages after you click the links.

Also try looking at the link in my sig labeled "Compiz"

I already figured out how to run both programs.
Saying "Of course, you have to read the pages after you click the links." is rather patronizing. 

> **3rdalbum said:**
> The reason why you can't just download an executable version of this program is because there is no way to compile a program so it will run on all the different architectures that Linux can run on.

True that, but theres no reason developers cant include binaries for atleast the most common architectures, or, failing that, write an installer that executes the freaking config commands automatically. If it does not require any input from me, why cant it be automated? I know this is blasphemy to the mighty tinkering god of linux, but come on.

---

### Post by nothingspecial on 2008-11-11
> **moniker127 said:**
> 

True that, but theres no reason developers cant write an installer that executes the freaking config commands automatically. If it does not require any input from me, why cant it be automated? I know this is blasphemy to the mighty tinkering god of linux, but come on.

They do. There are many automatic installers for linux. Ubuntu uses apt and gdebi. It`s not difficult. What devs do with programs written specifically for windows is up to them. If you need to play a game but still want to run linux have a dual boot, that`s not difficult either.

---

### Post by 3rdalbum on 2008-11-11
> **moniker127 said:**
> True that, but theres no reason developers cant include binaries for at least the most common architectures

True, but Linux users generally don't like binary installers. A growing number of developers (myself included) will also package their program for Ubuntu 32-bit.

> or, failing that, write an installer that executes the freaking config commands automatically. If it does not require any input from me, why cant it be automated?

Well, that's just the thing. Compiling is easy if you have the dependencies; just type in three commands. Generally to compile you run the ./configure program, it tells you that you're missing one or more libraries, and then you go and grab them from your package manager and try it again.

I'm not going to try to explain why it would be difficult to write a program that would actually get the dependencies for you and still respect your package manager; I'm not sure I could explain it to someone with very limited Linux knowledge. There are also compile-time options that the user can enable to get spiffy features in the program, install to a different location (there are good reasons to do this), or disable all but the most stable features.

A GUI installer that compiles a program for you is certainly possible and has been done before, but you have to get the dependencies yourself. Getting the dependencies is usually the hardest part of compiling (usually easy anyway), so why bother writing a GUI frontend for it when you still have to do the hardest part yourself? The only times that a GUI frontend for compiling has been done before, is when you have a very complicated set of programs to build that must be built in a particular order.

95% of programs are compiled this way:

1. Open a terminal in the directory of the source code
2. Type "./configure"
3. When the configure script complains that you don't have a particular library, look in Synaptic and find out what the package is called, and install it.
4. Go back to 2.
5. When the configure script gets all the way through successfully, type "make".
6. Type sudo make install.

Easy. Why do you need a GUI frontend for that? The people who are compiling source code don't need a GUI. The people who are scared of the command-line should stick to the massive number of programs available through Synaptic or in Debian packages.

---

