---
title: "Compiler/IDE for SDL+C++ with Ubuntu and Windows"
date: 2012-05-29
forum: Programming Talk
---

### Post by vedelumino on 2012-05-29
Hey, i would like to make games for Ubuntu and Windows, so i choose SDL that can run in many platform and C++ as the main language. :KS

The problem's i'm don't know which compiler/IDE that the best for working with SDL. In Windows, i use MinGW, but, mingw can't compile it to *.deb isn't it?
So, when i take a look Code::Blocks, that run in Windows, and available in Ubuntu too. I have both of them, but, i don't know how to setting SDL in Code::Blocks, and then i follow the instruction in Lazyfoo(the tutorial only available code::blocks for windows). And the result, the linker not found.

well, my reason to this question is : i want to distribute the game in both Operating system :)

so, i would like to ask :KS :
1. Which IDE is the best to working with SDL in Ubuntu?
2. Is the IDE can compile into *.exe and .deb?

---

### Post by PeterP24 on 2012-05-29
> The problem's i'm don't know which compiler/IDE that the best for working with SDL. In Windows, i use MinGW, but, mingw can't compile it to *.deb isn't it?
You're confusing the output of the compilation process with the .deb package format. See for more info here:

[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

> I have both of them, but, i don't know how to setting SDL in Code::Blocks, and then i follow the instruction in Lazyfoo(the tutorial only available code::blocks for windows). And the result, the linker not found.

It happen that I have Code::Blocks too installed and guess what - it offers you the possibility to directly make a SDL project. I never worked with it (don't know why it is installed on my machine) but I guess that in order to use the SDL project option you have to have the (libsdl??) proper libraries and header files installed on your machine. Just use synaptic and pull it up from repositories - don't go on the SDL website and take the last version since it is not 100 % compatible with some current games. I found out on my own, because I didn't bother to spent 5 minutes to read about it, before installing it. 

1. Pretty much every IDE will work, assuming you can correctly configure to link your stuff with sdl libraries. 
2. Nope - read the link above and then read the manpages for gcc and ld. Go and read the reference manual for gcc also ([http://gcc.gnu.org/onlinedocs/gcc-4.7.0/gcc/](http://gcc.gnu.org/onlinedocs/gcc-4.7.0/gcc/)), especially the part that says options for linking.

---

### Post by vedelumino on 2012-05-29
> **PeterP24 said:**
> You're confusing the output of the compilation process with the .deb package format. See for more info here:

[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)



It happen that I have Code::Blocks too installed and guess what - it offers you the possibility to directly make a SDL project. I never worked with it (don't know why it is installed on my machine) but I guess that in order to use the SDL project option you have to have the (libsdl??) proper libraries and header files installed on your machine. Just use synaptic and pull it up from repositories - don't go on the SDL website and take the last version since it is not 100 % compatible with some current games. I found out on my own, because I didn't bother to spent 5 minutes to read about it, before installing it. 

1. Pretty much every IDE will work, assuming you can correctly configure to link your stuff with sdl libraries. 
2. Nope - read the link above and then read the manpages for gcc and ld. Go and read the reference manual for gcc also ([http://gcc.gnu.org/onlinedocs/gcc-4.7.0/gcc/](http://gcc.gnu.org/onlinedocs/gcc-4.7.0/gcc/)), especially the part that says options for linking.

but, how to find the correct sdl to use? i'm using ubuntu 12.04.
1. Is code::blocks in ubuntu can be use to compile sdl(with *.deb)?(working with it, linking, until .deb)
2.ah, well, and then can we use the code in code::blocks ubuntu(.deb) and compile it in code::blocks windows(.exe) as well?

as long the setting of the code::blocks can be configure to use sdl, or i mean is the different of code::blocks in ubuntu and windows is only in the settings and compiler isn't it?
thx..

---

### Post by Avaritia on 2012-05-30
You don't compile anything into into a .deb file, .deb, .exe, .dmg etc... are self extracting archives with extra information added do do with the installation path, think of them as advanced .zip files.

You compile your program first then you package it.

---

### Post by vedelumino on 2012-05-30
> **Avaritia said:**
> You don't compile anything into into a .deb file, .deb, .exe, .dmg etc... are self extracting archives with extra information added do do with the installation path, think of them as advanced .zip files.

You compile your program first then you package it.
hmm, what's the meaning of package? isn't the compile process make the program?

forgive me, i'm not to understand that :(

---

### Post by PeterP24 on 2012-05-30
> **vedelumino said:**
> hmm, what's the meaning of package? isn't the compile process make the program?

forgive me, i'm not to understand that :(

Yes you have the program but you need to distribute it. On MSWindows you have to add an installer to your binaries in order to be sure they are copied in the right places, that the registry entries are created, etc, when the user starts the installation process. 
On Debian based systems, you package your programs in .deb files in order to distribute them to the end user. There are exceptions to this rule but - again - read the documentation, especially the first link I gave you in my first post to this thread.

---

### Post by vedelumino on 2012-05-30
Wow, it's interesting to developing with .deb :), i will read the documentation before asking again.

For now, Thankyou all for the helps!

---

### Post by overcast on 2012-05-31
You may want to read this information about packaging to get some idea. 

> 
[http://developer.ubuntu.com/packaging/html/packaging-new-software.html](http://developer.ubuntu.com/packaging/html/packaging-new-software.html)

---

### Post by vedelumino on 2012-05-31
> **overcast said:**
> You may want to read this information about packaging to get some idea.
oh, thankyou :D
and now, i have problem with code::blocks and sdl, should i post in this thread?
this is the error :
> Checking for existence: abcde....(directory of the project)
 Executing:abcde.....(in abcde.......)
 **Process terminated with status 255** (0 minutes, 0 seconds)


what should i do? thx.

---

### Post by PeterP24 on 2012-05-31
> **vedelumino said:**
> oh, thankyou :D
and now, i have problem with code::blocks and sdl, should i post in this thread?
this is the error :


what should i do? thx.

Please give more info - at least something so that we can reproduce your problem.

---

### Post by vedelumino on 2012-05-31
> **PeterP24 said:**
> Please give more info - at least something so that we can reproduce your problem.
I just install sdl libraries with synaptic, and run code::blocks, and then start SDL Project(template)(with no additional code). when build&compile, it show process terminate with status 255.

oh, i Follow this video : [http://www.youtube.com/watch?v=Ge0neKO1B6s]("http://www.youtube.com/watch?v=Ge0neKO1B6s")

in the video, he succeeded to compile and run the program. But, it doesn't work when i try. I'm doing like the video exactly.

---

### Post by PeterP24 on 2012-06-02
> **vedelumino said:**
> I just install sdl libraries with synaptic, and run code::blocks, and then start SDL Project(template)(with no additional code). when build&compile, it show process terminate with status 255.

oh, i Follow this video : [http://www.youtube.com/watch?v=Ge0neKO1B6s]("http://www.youtube.com/watch?v=Ge0neKO1B6s")

in the video, he succeeded to compile and run the program. But, it doesn't work when i try. I'm doing like the video exactly.

I don't know what is wrong. I didn't watched the full video. I did this: 
- created a new sdl project
- build project
- run project

And I do obtain the same results as that guy from the yt video. These being said, I am afraid I cannot do anything - since I cannot reproduce your error and I am not much of a Code::Blocks user. I saw in the comments on that video that there is another person who has exactly your problem. Further more, googling for "Process terminated with status 255" brought this: 

> [http://forums.codeblocks.org/index.php?topic=10415.0;prev_next=prev](http://forums.codeblocks.org/index.php?topic=10415.0;prev_next=prev)

But that post is rather old. It might work though - give it a try. 

Now, please don't press build&run. Press first build - and if everything goes well then run the executable. The idea is to see were the process is stopped due to the error.

---

### Post by roelforg on 2012-06-03
I used to use cygwin to compile the code, as long as the right dll's from cygwin's folders are there it'll work.
Lucky for you, i've wrote an article about it: [http://blog.roelf.org/?p=16](http://blog.roelf.org/?p=16) (Man, i should post more on there, but i don't have any ideas!)

---

### Post by vedelumino on 2012-06-04
> **roelforg said:**
> I used to use cygwin to compile the code, as  long as the right dll's from cygwin's folders are there it'll work.
Lucky for you, i've wrote an article about it: [http://blog.roelf.org/?p=16](http://blog.roelf.org/?p=16) (Man, i should post more on there, but i don't have any ideas!)

ho, what's cygwin like? where's the cygwin's folders?
perharps, should i try this? :D thx.

> **PeterP24 said:**
> You're confusing the output of the compilation process with the .deb package format. See for more info here:

[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)



It happen that I have Code::Blocks too installed and guess what - it offers you the possibility to directly make a SDL project. I never worked with it (don't know why it is installed on my machine) but I guess that in order to use the SDL project option you have to have the (libsdl??) proper libraries and header files installed on your machine. Just use synaptic and pull it up from repositories - don't go on the SDL website and take the last version since it is not 100 % compatible with some current games. I found out on my own, because I didn't bother to spent 5 minutes to read about it, before installing it. 

1. Pretty much every IDE will work, assuming you can correctly configure to link your stuff with sdl libraries. 
2. Nope - read the link above and then read the manpages for gcc and ld. Go and read the reference manual for gcc also ([http://gcc.gnu.org/onlinedocs/gcc-4.7.0/gcc/](http://gcc.gnu.org/onlinedocs/gcc-4.7.0/gcc/)), especially the part that says options for linking.

> **PeterP24 said:**
> I don't know what is wrong. I didn't watched the full video. I did this: 
- created a new sdl project
- build project
- run project

And I do obtain the same results as that guy from the yt video. These being said, I am afraid I cannot do anything - since I cannot reproduce your error and I am not much of a Code::Blocks user. I saw in the comments on that video that there is another person who has exactly your problem. Further more, googling for "Process terminated with status 255" brought this: 



But that post is rather old. It might work though - give it a try. 

Now, please don't press build&run. Press first build - and if everything goes well then run the executable. The idea is to see were the process is stopped due to the error.


i think i know the problem(in the previous post), when i choose  properties->Build target in the type, i change into GUI App. And the  result terminate with status 255. Perharps this is the problem.
---

wow, i did that. It works!
but, if i work the project from other drive(NTFS), it has problem :
This is  the result :

> Executing: xterm -T tes -e /media/...../bin/Debug/tes  (in .......)
Process terminated with status 0 (0 minutes, 0 seconds)
 and, in the console :
> 
sh: 1: /media/.../.../bin/Debug/project: Permission denied

Process returned 126 (0x7E) execution time : 0.007 s
Press ENTER to continue,
|
any suggestion? :)

---

### Post by PeterP24 on 2012-06-05
I am afraid I don't understand your last post. Please clarify: 
1) what problem did you manage to solve;
2) what new problem did you encounter;

Thanks

---

### Post by vedelumino on 2012-06-06
> **PeterP24 said:**
> I am afraid I don't understand your last post. Please clarify: 
1) what problem did you manage to solve;
2) what new problem did you encounter;

Thanks

1) Work from NTFS drive in code::blocks(ubuntu),
2) Access denied.

sorry for that post ;)

---

### Post by PeterP24 on 2012-06-06
> **vedelumino said:**
> 1) Work from NTFS drive in code::blocks(ubuntu),
2) Access denied.

sorry for that post ;)

So your problem is that you basically have your code on a windows (NTFS) partition and when you access it with Code::Blocks from Ubuntu, it says Access denied?

---

### Post by vedelumino on 2012-06-06
> **PeterP24 said:**
> So your problem is that you basically have your code on a windows (NTFS) partition and when you access it with Code::Blocks from Ubuntu, it says Access denied?
Exact :D

---

