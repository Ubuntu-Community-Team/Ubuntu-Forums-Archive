---
title: "Questions on the linux directory structure and more"
date: 2008-07-20
forum: Programming Talk
---

### Post by Anvilsmith on 2008-07-20
Caveat: I am more or less new to programming; some of what I say may sound nonsensical or silly. If it does, please point it out. 

My goal for this summer is to write a dynamic prose generator (in C++), which may later be incorporated into MUDs and text adventures. To my knowledge, nothing of this sort has been written so far. I hope to gain solid knowledge of open source programming (i.e. writing highly readable code) on this project, as well as some much-needed knowledge on Linux. Since I know next to nothing about Linux right now, I thought I'd bring up some questions regarding...

...The actual programming:
* Would it be quicker to learn the Linux API, or should I use GTK or some other multi-platform API? My concern for now is not portability, but completing the project as quickly as possible. I have never used an API before, apart from reading a bit of Charles Petzold's Programming Windows.
 
* Can you recommend a _concise_, _exhaustive_, _**bottom-up**_ tutorial for any of the above APIs? For reference, I consider [www.cplusplus.com/doc/tutorial/](www.cplusplus.com/doc/tutorial/) to be an excellent tutorial. 

* On a purely aesthetic note, where is it more "kosher" to put the project files? /src or /home/[...]/my_project?

...Making the package:
* Would it take long (i.e. more than 8 hours) to learn how to manually create a package? Also, how can I ensure that the package will be compatible with standard Linux distributions?

* Where should the package install which file? I assume the program's binary executable would go into /usr/bin or perhaps /usr/local/bin (or is that a temporary directory for installation-related files?) or /usr/bin/[program name], documentation files might go into /usr/man, but what about data files like savegames? /var/run ?

(I'll note that the Linux directory structure looks grossly obfuscated, with files for the same application thrown all over the place. Is there any reason for this, apart from the convenience of not having to set permissions for each file? Also, how can I quickly determine which files "relate" to a certain binary or belong in the same package?)

There are undoubtedly a lot of other things I'll need to know before I could ever get a linux application off the ground. The [Linux Knowledge Base and Tutorial]("http://www.linux-tutorial.info/index.php") seems useful, though it was written way back in 2003. If anyone here ever read it, I'd like to know whether it's still up-to-date.

---

### Post by rabatitat on 2008-07-20
1. It's always better to learn more. If you're going for the quickest way to do this, go with whatever you're currently running.

2. Well concise and exhaustive but beginner-friendly tutorials are hard to come by. [http://kernelbook.sourceforge.net/kernel-api.pdf](http://kernelbook.sourceforge.net/kernel-api.pdf) is the reference for the Linux API.
I always have the manuals for the environment (chip, OS, language, etc.) I'm working on for reference. So I suggested you get your hands on the manuals for your environment to go along with that tutorial you have.

3. Use your home directory. It's more manageable that way.

4. If you already know C/C++ and Linux it'll take less than an hour to wrap your head around making packages. For compatibility, compile the source code.

5. You're on the money with the first two locations. You could put the user-related data files in the user's home directory.

There are a lot of reasons and most of them are developer choices. Check the package itself for file locations. For relationships, check the manual and/or the source code.

Most of what you read there still works.

---

### Post by dwhitney67 on 2008-07-20
> **Anvilsmith said:**
> ...

(I'll note that the Linux directory structure looks grossly obfuscated, with files for the same application thrown all over the place. Is there any reason for this, apart from the convenience of not having to set permissions for each file? Also, how can I quickly determine which files "relate" to a certain binary or belong in the same package?)
...
Linux directories are generally organized per the Filesystem Hierarchy Standard (FHS).  Here's a quick guide listing the common directories and the purpose for each:  [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

Btw, what is a "dynamic prose generator"?

---

### Post by Anvilsmith on 2008-07-20
Thanks for the replies. 
> For compatibility, compile the source code.
I'm not sure what you mean by that. Would I need to set up preprocessor directives and compile the source code differently for each distribution?

Dwhitney67, when I say "Dynamic prose generator", I mean that, based on a given set of entities and different phenomena affecting them, the program could generate a narration (prose) on the spot (which is why it's "dynamic"). I don't think the term has ever been used before. A dynamic prose generator would allow the typical roguelike phrase "the orc hits you with a glowing sword!" to be replaced with other phrases, like "the orc drives his blood-red, glowing sword through you!" or "The gangly, red-haired orc hits you with a sudden thrust of his sword!", at random, if the game's engine allows it.

---

### Post by mssever on 2008-07-20
Linux source distributions typically make use of GNU autotools. The typical way to build from source is ```
cd source/directory
./configure && make
sudo make install
```In general, your program should follow that convention, although there exist good reasons to do otherwise.

Following the FHS, your configure script should default to the prefix /usr/local. However, it should generally accept the --prefix option to comply with different distros' packaging requirements. For example, .deb packages by policy use a prefix of /usr.

---

