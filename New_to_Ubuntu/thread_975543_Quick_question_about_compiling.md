---
title: "Quick question about compiling"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Kosimo on 2008-11-08
What happen if I already have some program installed. (for example audacious) by using official repos, and then I compile myself the same program?  
It overwrites the original files? And how can I then remove it? synaptic will remember the old installation files?
I guess that it'll make a mass by doing this.

---

### Post by Anothermindbomb on 2008-11-08
The makefile which should be in the top level directory of the source will usually have a stanza for "install" - it's this stanza which actually copies the compiled, executable file into it's final resting place. 

The normal set-up for a makefile results in the executable being created somewhere within the source directory your sitting it when you start the compile. You'll probably find that the executable is dropped off in the top-level of the source directory, alongside the makefile.

If you're concerned, execute "make -n" first - that will list all of the commands which WOULD be executed without actually doing anything. You'll see the compiler being called for each source file, along with the linker... nothing will actually be done though - it's a dry-run mode. Near the end of this, if you see a "cp" command to copy the executable to another directory you know what may be overwritten.

As I said though, standard practise is to require the user to execute a "make install" to actually result in the executable being copied outside the source-tree..

---

### Post by Paqman on 2008-11-08
If a package is available through the repos, you shouldn't normally need to compile it. If you want newer versions of packages that are in the normal repos, try enabling the backports repo.

If you really need an updated version of a particular package, try to find a .deb before you think of compiling (GetDeb is a great site for getting up-to-date .debs). If you do compile, install the package checkinstall and substitute the "make install" instruction with "checkinstall". This will create a .deb package that the package manager will recognise. This goes some way towards solving the biggest problem with compiling (ie: that it breaks the package manager)

---

### Post by Kosimo on 2008-11-08
> **Anothermindbomb said:**
> The makefile which should be in the top level directory of the source will usually have a stanza for "install" - it's this stanza which actually copies the compiled, executable file into it's final resting place. 

The normal set-up for a makefile results in the executable being created somewhere within the source directory your sitting it when you start the compile. You'll probably find that the executable is dropped off in the top-level of the source directory, alongside the makefile.

If you're concerned, execute "make -n" first - that will list all of the commands which WOULD be executed without actually doing anything. You'll see the compiler being called for each source file, along with the linker... nothing will actually be done though - it's a dry-run mode. Near the end of this, if you see a "cp" command to copy the executable to another directory you know what may be overwritten.

As I said though, standard practise is to require the user to execute a "make install" to actually result in the executable being copied outside the source-tree..

As I am very new on compiling, there are some points I still need to understand. So, as far as I understood from your post, I will always need the compiling folder (in case it won't copy anything somewhere else) to run the program, and also to uninstall it if I need.  In this case, I'll have two instances of that program, one installed by the opearting system and another created by the make installation. How do I know if they are not linked, or use some specific dependencies that can be removed if I remove one of them?

Thank you again and sorry for that simple questions :)

---

### Post by Kosimo on 2008-11-08
> **Paqman said:**
> If a package is available through the repos, you shouldn't normally need to compile it. If you want newer versions of packages that are in the normal repos, try enabling the backports repo.

If you really need an updated version of a particular package, try to find a .deb before you think of compiling (GetDeb is a great site for getting up-to-date .debs). If you do compile, install the package checkinstall and substitute the "make install" instruction with "checkinstall". This will create a .deb package that the package manager will recognise. This goes some way towards solving the biggest problem with compiling (ie: that it breaks the package manager)

I am a getdeb addict :D 
But in this case I want to use a specific version of audacious, (1.90) witch is in mercurial. I've got the source code and before compiling it I wanted to make some questions. 

So, if I use checkinstall it creates a deb that then I can easily install. Right?   
Every time I try to compile I always miss tons of dependencies and I have to install them one by one... There is any way to find out all dependencies needed for some specific program?
Thank you!

---

### Post by Anothermindbomb on 2008-11-08
Sorry for any confusion. I'll try to elaborate.

Compiling from source is a multistage process.

Firstly, the source is compiled and an executable is produced.
Secondly, the executable is copied to somewhere on the path to ensure it's easily callable.
Once you have the executable stashed away in say, /usr/games/ you can delete the source-tree. it's no longer required.


Any package manager won't know anything about the newly compiled code - Synaptic for example will have no idea that there's now a directory in /usr/games called space-nethack and consequently, you'll never see any updates for it, nor will you be able to remove it via a package manager (all you'd do is delete the space-nethack directory from /usr/games)

In your situation, suppose you've installed Audacity via Synaptic. There's a new version released by J. Random Hacker which adds new functionality with your sound card... you desire this greatly but it won't be available in the repos for 6 months... you can't wait - you NEED that new release right now.

You grab the source and untar it
You "make" the executable - it's created in the top level of the source directory. (At this point if you start audacity in the normal way, the ubuntu version will be foundin /usr/bin and it'll fire up as normal.)
You "make install" - this copies the executable from the source directory into /usr/bin and overwrites the ubuntu version currently there.

Now if you start up audacity, you'll get the new version. Synaptic and other package managers will still be quite happy as they have an entry for the package in their control files, and as far as they are concerned everything still looks normal - there should be a file in /usr/bin called audacity and there actually is so all is groovy.

However, as soon as there's an update to audacity via a package manager, your sexy new version will be overwritten by the incoming version unless you prevent it from happening. 

To enable you run both version side by side, install your compiled version into /usr/local/bin - this was you seperate the code you have installed locally from that dropped off on your box via package managers.

Hope I'm not  confusing you even more! :)

---

### Post by Kosimo on 2008-11-08
> **Anothermindbomb said:**
> Sorry for any confusion. I'll try to elaborate.

Compiling from source is a multistage process.

Firstly, the source is compiled and an executable is produced.
Secondly, the executable is copied to somewhere on the path to ensure it's easily callable.
Once you have the executable stashed away in say, /usr/games/ you can delete the source-tree. it's no longer required.


Any package manager won't know anything about the newly compiled code - Synaptic for example will have no idea that there's now a directory in /usr/games called space-nethack and consequently, you'll never see any updates for it, nor will you be able to remove it via a package manager (all you'd do is delete the space-nethack directory from /usr/games)

In your situation, suppose you've installed Audacity via Synaptic. There's a new version released by J. Random Hacker which adds new functionality with your sound card... you desire this greatly but it won't be available in the repos for 6 months... you can't wait - you NEED that new release right now.

You grab the source and untar it
You "make" the executable - it's created in the top level of the source directory. (At this point if you start audacity in the normal way, the ubuntu version will be foundin /usr/bin and it'll fire up as normal.)
You "make install" - this copies the executable from the source directory into /usr/bin and overwrites the ubuntu version currently there.

Now if you start up audacity, you'll get the new version. Synaptic and other package managers will still be quite happy as they have an entry for the package in their control files, and as far as they are concerned everything still looks normal - there should be a file in /usr/bin called audacity and there actually is so all is groovy.

However, as soon as there's an update to audacity via a package manager, your sexy new version will be overwritten by the incoming version unless you prevent it from happening. 

To enable you run both version side by side, install your compiled version into /usr/local/bin - this was you seperate the code you have installed locally from that dropped off on your box via package managers.

Hope I'm not  confusing you even more! :)

No you didn't :)
That make total sense.
I found lot of information out there about compiling but what I needed is exactly what you did. A simple explanation to understand what it happens when compiling a source code.  
Ok so in this case. I want to have that new release that I've just download. So, in order to prevent errors with updates what I can do is just apt-get remove audacious, so the update manager will forget that audacious exist (right?) and then install my own copy. Then if I want to update I will do it manually. 
Last question I have (If I'm not overusing your kindness) :)  is:
Once installed using make install, I always need the source code folder witch I used to install in order to uninstall it, right? Because I won't remember the folder where the executable and all files where copied.
Another used mentioned that for this issue it can be better to use checkinstall, so I will create a simple .deb and it'll be easy to remove with synaptic for example.  But, in this case, do I'm going to have the problem we've been discussing about two different versions and conflicts with updates?

Thank you again.

---

### Post by ggaaron on 2008-11-08
Just my opinion - it's not so easy to compile things on binary platform like Ubuntu and using something that will create a package instead of installing something directly is a GREAT idea (imagine that you want to install some other program that depends on this package, if apt doesn't know that you already have this package it will install it's own version). If you create deb files instead of installing them directly you won't end up with two versions installed in the same time, updates still will be a concern but probably you can instruct this deb creating software to mark it as for example version 9999 so it will not be updated with versions from repository. Additionally make uninstall is not required, someone could have decided not to implement it and then you will be left removing things manually.

And make is not the only thing used to build packages=)

If you really start compiling things by yourself, don't be surprised if not everything works well, sometimes just ./configure && make && make install won't be enough.

---

