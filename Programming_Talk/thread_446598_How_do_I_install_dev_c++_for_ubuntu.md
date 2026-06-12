---
title: "How do I install dev c++ for ubuntu"
date: 2007-05-17
forum: Programming Talk
---

### Post by Fzero on 2007-05-17
What do I type in terminal to install dev c++ for ubuntu? I already have the files

---

### Post by FuturePast on 2007-05-17
Can you be more specific. What files do you have? Where did you get them from?

---

### Post by public_void on 2007-05-17
Even though the SourceForge page says it runs on Linux, all I could find was source files written in Delphi and Windows setup executables. Couldn't find it in the repositories. Maybe try another IDE like Anjuta.

---

### Post by LaRoza on 2007-05-17
It comes with an OpenOffice Document with all that you need. (File extension .odt)

You need to install other things first, so read carefully!

---

### Post by wolfgang959 on 2007-05-17
hi i was able to get those linux Dev C++ fiels aswell of source forage it took a lot of searching to find it tho.

anyway when i tried to use the files to install it i didnt seam to get very far. but try opening the (.sh)  
file in terminal (by clicking open then run in terminal). 

if you manage to get it working or not can you please tell me the web address for the files please.

thanks

---

### Post by kknd on 2007-05-17
DevC++ is not portable, the only way to run it is with "wine" or some derivation of it.

There is a lot of good IDE's that run on Linux.

Take a look at Anjuta, Eclipse (with CDT), Codeblocks, etc. They are way better than the DevCpp.

---

### Post by ibrahim-abdul on 2009-05-15
Well!
In order to run Dev C++, you need to use : System>>adminstration>>Synaptic package menager.

Write at the search field : gcc

It will give you unremarked gcc(3-4)(or may be the last version), you will need to download it by mouse right click, mark it, the apply.

it should work properly.
hope it will help you

---

### Post by hessiess on 2009-05-16
DevC++ has bean out of development since 2005, thus could be considered a dead program. Find a batter IDE, or learn a text editor like Vim.

---

### Post by bubuzzz on 2009-05-16
depend on what you want to do. If you are new to C++ and want to learn it, use Geany. If you want to do something bigger, use codeblock or anjuta. Don't use Eclipse cause it is heavy and basically, it is designed for java, not for C/C++

---

### Post by noerrorsfound on 2009-05-16
[http://codeblocks.org](http://codeblocks.org)

---

### Post by Sinkingships7 on 2009-05-16
Guys. This thread is two years old.

Also, Dev C++ runs perfectly through WINE, and that's the only way to run it. gcc is not a component of wine, but mingw comes with the Dev C++ binary.

---

### Post by bubuzzz on 2009-05-17
also, you can download codeblock right from add/remove program (ubuntu 9.04). I am very suprised that it 's already there

---

### Post by bhuvi07 on 2010-03-03
there r so many options when i type gcc so wat to download n wat not to???

---

### Post by Sinkingships7 on 2010-03-06
> **bhuvi07 said:**
> there r so many options when i type gcc so wat to download n wat not to???

gcc is installed on most GNU/Linux distributions by default. Open the terminal and use this command to get everything you need to compile and run programs:
```

sudo aptitude install build-essential
```

---

### Post by Pno3 on 2011-02-15
DEV C++ is not dead, in fact DEVC++5 is currently in beta. I also needed this program to run on Ubuntu 10.10 because my C++ college class  requires it. I was able to install it using wine, and it works fine until I tell it it compile and run. it will will compile, but it will not run. my first fix was to try to install windows command terminal because I thought that it would not run the program because I do not have the terminal, but I am unable to find a way to do this. anyone know how to fix this?

---

### Post by trent.josephsen on 2011-02-15
Gah!  It's THE THREAD THAT WOULDN'T DIE! :p

---

### Post by linuxsyst on 2011-02-15
Why?
```
g++ -o filename filename.cpp
```

---

### Post by MadCow108 on 2011-02-15
> **Pno3 said:**
> DEV C++ is not dead, in fact DEVC++5 is currently in beta.

it is very much dead.
the last commit to the repositories was 5 years ago.
the last binary release 5 years ago and it ships gcc 3.4.2 which is 6 years old.

you should use something else, there are plenty alternatives.

---

