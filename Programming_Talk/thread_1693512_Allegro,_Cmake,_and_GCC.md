---
title: "Allegro, Cmake, and GCC"
date: 2011-02-22
forum: Programming Talk
---

### Post by Armaeddon on 2011-02-22
Recently i've decided that i wanted to make visual C++ programs. Currently i have a basic knowledge of C++, and have made a few simple programs with Code::Blocks.

I've learned that i should use allegro to create the c++ programs, and i have downloaded allegro.tar.gz, and used Cygwin to configure it. I soon learned that i needed Cmake for allegro the work, so i configure the .tar.gz file in the same way. However, i cannot get any further because this keeps coming up.

```

Emilio Garcia@Emilio-MacWin /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4
$ ./configure --ssl-dir=/usr/local/include gcc-4.5.3
---------------------------------------------
CMake 2.8.4, Copyright 2000-2009 Kitware, Inc.
---------------------------------------------
Error when bootstrapping CMake:
Cannot find appropriate C compiler on this system.
Please specify one using environment variable CC.
See cmake_bootstrap.log for compilers attempted.

---------------------------------------------
Log of errors: /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4/Bootstrap.cmk/
.log
---------------------------------------------

Emilio Garcia@Emilio-MacWin /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4
$ ./configure --ssl-dir=/usr/local/include bootstrap.cmk
---------------------------------------------
CMake 2.8.4, Copyright 2000-2009 Kitware, Inc.
---------------------------------------------
Error when bootstrapping CMake:
Cannot find appropriate C compiler on this system.
Please specify one using environment variable CC.
See cmake_bootstrap.log for compilers attempted.

---------------------------------------------
Log of errors: /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4/Bootstrap.cmk/
.log
---------------------------------------------

Emilio Garcia@Emilio-MacWin /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4
$ cd /cygdrive/c/"Documents and Settings"/"Emilio Garcia"/Desktop/Source/gcc-4.5.2

Emilio Garcia@Emilio-MacWin /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/gcc-4.5.2
$ ./configure
checking build system type... i686-pc-cygwin
checking host system type... i686-pc-cygwin
checking target system type... i686-pc-cygwin
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for a sed that does not truncate output... /usr/bin/sed
checking for gawk... gawk
checking to see if cat works as expected... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/gcc-4.5.2':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```As you can see, i have also downloaded GCC and configure it, and tried to include it in the configuration of cmake.

what do i do?

---

### Post by lkjoel on 2011-02-22
> **Armaeddon said:**
> Recently i've decided that i wanted to make visual C++ programs. Currently i have a basic knowledge of C++, and have made a few simple programs with Code::Blocks.

I've learned that i should use allegro to create the c++ programs, and i have downloaded allegro.tar.gz, and used Cygwin to configure it. I soon learned that i needed Cmake for allegro the work, so i configure the .tar.gz file in the same way. However, i cannot get any further because this keeps coming up.

```

Emilio Garcia@Emilio-MacWin /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4
$ ./configure --ssl-dir=/usr/local/include gcc-4.5.3
---------------------------------------------
CMake 2.8.4, Copyright 2000-2009 Kitware, Inc.
---------------------------------------------
Error when bootstrapping CMake:
Cannot find appropriate C compiler on this system.
Please specify one using environment variable CC.
See cmake_bootstrap.log for compilers attempted.

---------------------------------------------
Log of errors: /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4/Bootstrap.cmk/
.log
---------------------------------------------

Emilio Garcia@Emilio-MacWin /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4
$ ./configure --ssl-dir=/usr/local/include bootstrap.cmk
---------------------------------------------
CMake 2.8.4, Copyright 2000-2009 Kitware, Inc.
---------------------------------------------
Error when bootstrapping CMake:
Cannot find appropriate C compiler on this system.
Please specify one using environment variable CC.
See cmake_bootstrap.log for compilers attempted.

---------------------------------------------
Log of errors: /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4/Bootstrap.cmk/
.log
---------------------------------------------

Emilio Garcia@Emilio-MacWin /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/cmake-2.8.4
$ cd /cygdrive/c/"Documents and Settings"/"Emilio Garcia"/Desktop/Source/gcc-4.5.2

Emilio Garcia@Emilio-MacWin /cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/gcc-4.5.2
$ ./configure
checking build system type... i686-pc-cygwin
checking host system type... i686-pc-cygwin
checking target system type... i686-pc-cygwin
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for a sed that does not truncate output... /usr/bin/sed
checking for gawk... gawk
checking to see if cat works as expected... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/cygdrive/c/Documents and Settings/Emilio Garcia/Desktop/Source/gcc-4.5.2':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```As you can see, i have also downloaded GCC and configure it, and tried to include it in the configuration of cmake.

what do i do?
Try this into a Terminal window:
```
sudo apt-get install gcc
sudo apt-get install cc

```
Then retry.

---

### Post by Armaeddon on 2011-02-23
I am currently using Windows 7 as my primary operating system. I have both Ubuntu 10.10 and Mac OSX on other partitions, but i would like to stick with windows for coding.

Is there any way to use the command you gave me in windows? or will i have to switch to a Unix-based OS?

---

### Post by lkjoel on 2011-02-23
> **Armaeddon said:**
> I am currently using Windows 7 as my primary operating system. I have both Ubuntu 10.10 and Mac OSX on other partitions, but i would like to stick with windows for coding.

Is there any way to use the command you gave me in windows? or will i have to switch to a Unix-based OS?
I doubt that it is possible to do that on Windows.
You will have to switch to a Unix-based OS for compiling.

---

### Post by Armaeddon on 2011-02-23
Is there any way to use allegro/cmake on windows at all?

---

### Post by JDShu on 2011-02-23
I have managed to compile Allegro programs on windows before. It was a long time ago so I don't remember what I did, but it is possible.

---

### Post by Armaeddon on 2011-02-23
Is there a way to configure everything in a Unix OS and then bring it to Windows?

and also thanks to everyone who is helping.

---

### Post by Vox754 on 2011-02-23
> **Armaeddon said:**
> Recently i've decided that i wanted to make visual C++ programs. Currently i have a basic knowledge of C++, and have made a few simple programs with Code::Blocks.

I've learned that i should use allegro to create the c++ programs, and i have downloaded allegro.tar.gz, and used Cygwin to configure it. I soon learned that i needed Cmake for allegro the work, so i configure the .tar.gz file in the same way. However, i cannot get any further because this keeps coming up.
...
As you can see, i have also downloaded GCC and configure it, and tried to include it in the configuration of cmake.

what do i do?

Your issue is confusing.

What does "visual C++" programs mean?
Graphical User Interfaces (GUI)?
Using Microsoft Visual C++?
Using GTK, Qt, Wxwidgets?
Using the native windows graphical toolkit?
Are you using Windows or Linux?
Do you intend to program for Windows or for Linux, or for both (portable)?
Why do you "need" to use allegro for C++?

Since this is an Ubuntu forum, most of us assume that you are doing your work on an Ubuntu system and will provide solutions based on that. If this is not the case, or you are cross-compiling or doing something out of the ordinary, you should really mention this in the first post to avoid further confusions.

As you can see, I do not provide directly an answer to your problem, I only warn you that the quality of the responses you get depends greatly on the quality of the questions you ask, specifically the opening post of the thread. Consider this in the future when asking for advice.

---

### Post by Armaeddon on 2011-02-23
> **Vox754 said:**
> Your issue is confusing.

What does "visual C++" programs mean?
Graphical User Interfaces (GUI)?
Using Microsoft Visual C++?
Using GTK, Qt, Wxwidgets?
Using the native windows graphical toolkit?
Are you using Windows or Linux?
Do you intend to program for Windows or for Linux, or for both (portable)?
Why do you "need" to use allegro for C++?

Since this is an Ubuntu forum, most of us assume that you are doing your work on an Ubuntu system and will provide solutions based on that. If this is not the case, or you are cross-compiling or doing something out of the ordinary, you should really mention this in the first post to avoid further confusions.

As you can see, I do not provide directly an answer to your problem, I only warn you that the quality of the responses you get depends greatly on the quality of the questions you ask, specifically the opening post of the thread. Consider this in the future when asking for advice.

Sorry for not  being clearer, it was very late at night for me.

1.) To be honest, im not sure of the exact title of what i wish to do. By visual, i meant something along the lines of graphical, ex. a game of Pong or a side scrolling game.

2.) As previously mentioned, i am using Windows 7 Home Premium with both Ubuntu 10.10 and Mac OS X on separate partitions.

3.) A multi-OS program would be preferable, but I would be fine creating a program for only one OS. 

4.) I "need" allegro because i have been told that it is necessary for game creation.

---

### Post by JDShu on 2011-02-24
> **Armaeddon said:**
> 
4.) I "need" allegro because i have been told that it is necessary for game creation.

hmm, who told you that? Allegro is good, but SDL does the same thing.

Btw, I used mingw for compiling allegro games in Windows, if that helps.

---

### Post by Armaeddon on 2011-02-24
> **JDShu said:**
> hmm, who told you that? Allegro is good, but SDL does the same thing.

Btw, I used mingw for compiling allegro games in Windows, if that helps.

Everywhere i looked actually told me to use Allegro, but now ill be sure to give SDL a try.

---

