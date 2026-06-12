---
title: "Cross Compiler for Compiling windows binaries??"
date: 2005-03-30
forum: Programming Talk
---

### Post by Kimm on 2005-03-30
I was woundering if anyone know of a C++ cross compiler for linux. So that I can compile my programs for windows aswell.

So far I have been able to run Dev-C++ in wine, it works somewhat good (not for editing code however) but mostly it will not compile the file, I have also tried running Digital Mars C++ compiler, and well it works... but it doesnt compile right, it seems to jumble up the code in the program so the commands dont execute in desired order :x 

Can anyone help??

---

### Post by toojays on 2005-03-30
Yeah, this can be done quite nicely, and makes my day job a helluvalot less sucky.

You need to install the mingw32 package from universe. This will give you all the usual gcc tools, prefixed with something like i586-mingw32.

What I do is run a script to set a whole bunch of environment variables, for instance```

CC=i586-mingw32-gcc
CXX=i586-mingw32-g++
```, etc.

This is off the top of my head; the scripts are at work and I'm at home. Hopefully you get the gist. This allows me to build entire wxWidgets programs, targetted at Microsoft Windows, from the comfort of my Ubuntu box.

---

### Post by schmendrick on 2009-11-11
thanks for the info so far (though its a quite old thread :) ) but I am confused. is this just the MSVC compiler running under linux?  

cross compiling simple hello worlds work just fine, but when i try to compile programs including sockets i get errors (he cant find the headers).

if i try to include <windows.h> though for testing, he can't find that either. 


so how can i do socket programming with this? or what am i doing wrong?

---

### Post by Fatman_UK on 2009-11-11
MinGW is a Windows port of the GNU compiler (and linker, etc). So no, it's not MSVC.

The win32api package (for MinGW) is quite good, but it still has some bits missing. Unicode support for instance.

For socket programming at the moment I'm using the Boost.Asio library. Once you grasp the concept of synchronous vs. asynchronous, it's quite easy.

---

### Post by schmendrick on 2009-11-11
you mean i would have to use boost for writing socket programs if i want to use this cross compiler?
is there no other way?

---

### Post by Fatman_UK on 2009-11-11
You don't have to use Boost. I was just letting you know what I use. Someone else might not like it. Asio has its flaws like any other library, but IMO it's the best there is for cross-platform C++ sockets programming.

You could look into native socket APIs, but then you have to learn the API for each OS you want to support.

---

### Post by schmendrick on 2009-11-11
ah ok, i misunderstood. thanks.

i am using a port of the socketCC library that compiles and runs under windows and linux by the way.

when i took a glance at asio it felt too complicated for my taste and i didnt want to rely on boost so i decided for that.

---

### Post by Fatman_UK on 2009-11-11
Glad you found something that works. :) It's the Monash university project, right? Looks like it supports a good few other platforms too.

Before Asio was available I was looking around for a cross-platform sockets library. Complete nightmare trying to find something which was cross-platform and actively maintained, now you trip over them while looking for something else.

Oh, did you look at SDL? I hear that has a nice networking library.

---

### Post by schmendrick on 2009-11-12
Yes, it was originally done by a guy in the monash university, though the author and code-maintainer is not there any more.

though the version supporting windows as well is not tested on other OSes than linux (centos and ubuntu) and windows(xp and vista).


I heard SDL had a networking library, but I didnt know if it was any good.

But I wouldnt normally use it if I dont create a game or something needing graphics. 

I think there are many frameworks providing that cross platform support for sockets (QT and wxWidgets also some I think). 
But like SDL they provide many other things as well that I dont need.

If you just want something that only does NETWORKING then there is not that much left  :)

---

