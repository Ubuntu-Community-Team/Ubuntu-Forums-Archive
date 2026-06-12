---
title: "[SOLVED] Qtractor and libasound2"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by I-dontknow on 2008-10-18
I'm trying to install qtractor.

```
ajzimmerman@ajzimmerman-desktop:~$ cd /home/ajzimmerman/Desktop/qtractor-0.2.2/
ajzimmerman@ajzimmerman-desktop:~/Desktop/qtractor-0.2.2$ ./configure 
./configure: line 1382: config.log: Permission denied
./configure: line 1392: config.log: Permission denied
ajzimmerman@ajzimmerman-desktop:~/Desktop/qtractor-0.2.2$ sudo ./
configure  debian/    icons/     src/       win32/     
ajzimmerman@ajzimmerman-desktop:~/Desktop/qtractor-0.2.2$ sudo ./configure 
AUTHORS              debian/              qtractor.spec.in
ChangeLog            icons/               README
config.h.in          INSTALL              README.VST
config.log           Makefile.cvs         src/
configure            Makefile.in          TODO
configure.ac         qtractor.desktop.in  win32/
COPYING              qtractor.pro.in      
ajzimmerman@ajzimmerman-desktop:~/Desktop/qtractor-0.2.2$ clear

ajzimmerman@ajzimmerman-desktop:~/Desktop/qtractor-0.2.2$ sudo ./configure 
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
ajzimmerman@ajzimmerman-desktop:~/Desktop/qtractor-0.2.2$ 

```

I tried a debian AMD x86_64 version (that's my processor) .deb package and it's looking for a dependency.
```
libasound2
```
In the repos, this dependency is listed, as already installed.
So, I just did the development libasound2 as well. Why not.
(By the way, I've already searched this forum for an answer to this problem, and I didn't find anything but an unsolved post.
)
So, so far, I've got everything for libasound2 but the docs. Seems pretty thorough but the .deb package is still not accepting it.

Also, I went and tried to find the origional libasound in debian repos, and am finding that the one in Ubuntu repos is actually a later version.

So the libasound2 origional is not installing.......

---

### Post by I-dontknow on 2008-10-18
I'm finding that the qtractor in our repos is several versions off.
And the installation of it from the apt-get doesn't even put it in the menu.

---

### Post by Claus7 on 2008-10-18
Hello,

I hope that you will get a solution to this, yet my humble experience to a problem similar to yours was solved, when I installed the source code of the program I was interested in. 

Regards!

---

### Post by I-dontknow on 2008-10-18
> **Claus7 said:**
> Hello,

I hope that you will get a solution to this, yet my humble experience to a problem similar to yours was solved, when I installed the source code of the program I was interested in. 

Regards!

I appreciate it.

---

### Post by Claus7 on 2008-10-18
Hello,

looking better the log file you provide, I would suggest you to open synaptic and install g++ and the package build essential. For the first one you might need the ubuntu cd. Check this out, it's easy and if you haven't installed those packages they will be very helpful in various applications.
Just a notice. It's better to try ./configure without being root. In case you face permission issues and you still want to install the program or library in the default place, then switch to root.

Regards!

---

### Post by Perfect Storm on 2008-10-18
```
sudo apt-get install build-essential
```

```
./configure
```

If all goes well and you have installed the required libs and their -devs

then;
```
make
sudo make install
```

note if ./configure failse to run either;
chmod +x <file>

or

sh configure

not
sudo ./configure

---

### Post by I-dontknow on 2008-10-18
[SIZE="1"]> **Claus7 said:**
> Hello,

looking better the log file you provide, I would suggest you to open synaptic and install g++ and the package build essential. For the first one you might need the ubuntu cd. Check this out, it's easy and if you haven't installed those packages they will be very helpful in various applications.
Just a notice. It's better to try ./configure without being root. In case you face permission issues and you still want to install the program or library in the default place, then switch to root.

Regards!


I did the g++ and that helped a bit. I'm running into some issues with terminal again.

[http://paste.ubuntu.com/59288/](http://paste.ubuntu.com/59288/)

> **Artificial Intelligence said:**
> ```
sudo apt-get install build-essential
```

```
./configure
```

If all goes well and you have installed the required libs and their -devs

then;
```
make
sudo make install
```

note if ./configure failse to run either;
chmod +x <file>

or

sh configure

not
sudo ./configure

I've done your commands (Thanks for the reminder of build-essential, I forgot that).
The same results are coming with the JACK library.

It shows in synaptic, as well as the above terminal output that Jack is installed already.

Here is another output, from what you've given me:

[http://paste.ubuntu.com/59282/](http://paste.ubuntu.com/59282/)

---
I am going to try another thing; there's another program called freewheelin (or other) which requires "libjack" or something, and I'll see if that helps.

ajzimmerman@ajzimmerman-desktop:~/Desktop/qtractor-0.2.2$ sudo apt-get install libjack0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libjack0 is already the newest version.
libjack0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ajzimmerman@ajzimmerman-desktop:~/Desktop/qtractor-0.2.2$[/SIZE]

[COLOR="Navy"]I've solved the problem. [/COLOR]

[FONT="Arial Narrow"]For JACK
For those of you seeing this problem as I had, go into synaptic and search for libjack. There's a few things that are already installed, but there's one core library for asynchronous and two development selections, both the same versions; the libraries and the "connection kit"
It's good to select what looks applicable. I selected a few, so I'm not exactly sure which ones solved my problem, but there's only a few to go through anyway. I'm guessing it was the development libraries.

For libasound2,
I cannot remember exactly what I did. But I believe I just went into synaptic and installed the development libraries for it.[/FONT]

**The successful way is to compile it**

---

