---
title: "Understanding dynamic linking"
date: 2009-10-14
forum: Programming Talk
---

### Post by ThomasJ02 on 2009-10-14
How come when I upgrade libraries on Ubuntu, everything doesn't break? If a library has changed, doesn't everything that links to have have to be recompiled? For example, when there's a new GLIBC version, how come I don't have to upgrade everything else on my system?

If I understand correctly from my own programming, when I compile a new version of myLib.so, I also have to recompile myProg if the myLib.so header files have changed. 

Can someone enlighten me?

---

### Post by MadCow108 on 2009-10-14
if you have a look at your /usr/lib you see that there are symbolic links and libraries they point to them and most have numbers behind them.
That has the purpose of avoiding problems when upgrading libraries.

Lets say you compile a program needing libX.so. In your /usr/lib you have a file libX.so.2 and a link libX.so pointing at it.
If you compile and link your program the linker will follow the symbolic link and link with libX.so.2 (wow a lot of links in one sentence :D )

Now if you upgrade libX.so it will not remove libX.so.2 but instead place a libX.so.3 in /usr/lib and just replace the symbolic link
Like this your program will still run because it is still linked with the correct library libX.so.2
only if you recompile it, this will change

---

### Post by djbushido on 2009-10-14
Basically the system creates a network of linking: when you say you want to include use a library, all the system finds is a chain to where the actual library is. So searching for libWhatever.so actually locates the major release libWhatever.so.1 which locates the minor release libWhatever.so.1.15.
Now when the system updates, it just replaces the links necessary so that the libWhatever.so link is changed to libWhatever.so.2 and so on and so forth.
Also, for dynamic linking at run time (Just to make sure all the bases are covered):
The system includes a list in the binary of what libraries are needed to run. This "list" can be retrieved using the "ldd" command (list dynamic dependencies). Then the system loads these libraries at run time, and if they don't exist, exits the program with a message like: "libWhatever.so does not exist on the search path"
Is that enough info?

---

