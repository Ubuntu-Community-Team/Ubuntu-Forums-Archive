---
title: "Cross-compiling using mingw32 - adding libraries (freeglut)"
date: 2008-11-10
forum: Programming Talk
---

### Post by ljungkvist on 2008-11-10
So during the last few months I've been doing a simple game in c++ using  opengl. Now that it's finished, it seems like all of my friends use windows, which I don't, so I realized I had to compile it for windows.

I did a bit of research and found out that what I wanted to do was to *cross-compile* it, which could be done using the mingw32 package (available in the repos). Ok so I installed the thing and tried it on a small 'hello world' style program and it was all fine. However when I tried compiling my game, it was clear that the mingw32 libraries didn't have the freeglut libraries (only standard glut), hence glutLeaveMainLoop et al wasn't found. So I have to add these myself. The problem is that I have never done such a thing! If I'm not completely off, I first have to grab the freeglut source, compile it for windows (how?) and put the files in the mingw32 include folder.

As you see I need a bit of help, and I'd be very grateful if someone could tell me the basic procedure!

Also, what about the includes in the game source code? Do I have to change some of them, or add something like <windows.h> (which i've never understood)?

Thanks in advance!

Note: I found [this]("http://ubuntuforums.org/showthread.php?t=198459") thread. Since it's more about the wine related problem I decided to make a new thread. Hope that's ok.

---

### Post by samjh on 2008-11-10
If you have a copy of Windows, you could install [VirtualBox](www.virtualbox.org) and run Windows within VirtualBox to compile Free GLUT from source.  I use this approach to test and compile programs on Windows.

If you're feeling brave, you can try doing a normal ./configure && make, but use these flags for ./configure:
```
./configure --prefix=/usr/i586-mingw32msvc --host=i586-mingw32msvc --build=i586-linux
```Be warned: the command above is just a rough guess and you will most probably need to change it.  Trial is error is inevitable.

I have found that the --build flag is particularly problematic.  If you run /usr/share/libtool/config/config.guess, then it will spit out a value you can use for the --build flag.

Again, I have to emphasise that this will probably involve a lot of trial and error, and may possibly bork your Mingw32 installation (or even worse, depending on your adventurousness).

---

### Post by ljungkvist on 2008-11-10
> **samjh said:**
> If you have a copy of Windows, you could install [url=www.virtualbox.org]VirtualBox and run Windows within VirtualBox to compile Free GLUT from source.  I use this approach to test and compile programs on Windows.

If you're feeling brave, you can try doing a normal ./configure && make, but use these flags for ./configure:
```
./configure --prefix=/usr/i586-mingw32msvc --host=i586-mingw32msvc --build=i586-linux
```Be warned: the command above is just a rough guess and you will most probably need to change it.  Trial is error is inevitable.

I have found that the --build flag is particularly problematic.  If you run /usr/share/libtool/config/config.guess, then it will spit out a value you can use for the --build flag.

Again, I have to emphasise that this will probably involve a lot of trial and error, and may possibly bork your Mingw32 installation (or even worse, depending on your adventurousness).

ok thanks! this actually worked very well. here's what i did:

```
./configure --prefix=/home/kalle/lib/freeglut --target=i586-mingw32msvc --host=i586-mingw32msvc --build=i686-pc-linux-gnu

```

so now i have a couple of header files, a library .a file (and a '.la' file which i don't really know what it's for). Do i just have to put the header files in the include/GL directory and the .a file in the lib directory respectively, or do i have to let mingw32 "know they're there"?

---

### Post by samjh on 2008-11-10
I think if you put those files in the include and lib directories of your /usr/i586-mingw32msvc directory, it should be able to find them.  Just make sure to specify the correct -I and -l flags when you compile.

In fact, I think a [FONT="Courier New"]sudo make install[/FONT] from your freeglut source directory should probably install those files for you, as you specified --prefix=/usr/i586-mingw32msvc for ./configure.

Again, no guarantees.  Cross-compiling is usually a pain in the posterior.

---

### Post by ljungkvist on 2008-11-12
Thanks again for your reply. Now I've got it working and this was how it was done:

First I tried what you suggested, put the files in the correct folders and tried to compile. The compilation itself was ok, but I got a lot of linking errors. I could get rid of some of the by tweaking the -l commands, but all the errors involving freeglut specific commands just wasn't going away. At some point I lost interest.

So since I actually already had a working WinXP virtual machine installed I followed your advice. And since there were a lot more documentation available regarding how to install freeglut on windows, I finally got it working (in conjugation with minGW). Considering the fact that it now works, I don't think I will bother setting up the original cross compiler under ubuntu, although it would be more convenient.

---

