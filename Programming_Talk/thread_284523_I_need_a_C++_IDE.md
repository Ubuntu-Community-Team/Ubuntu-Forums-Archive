---
title: "I need a C++ IDE"
date: 2006-10-25
forum: Programming Talk
---

### Post by involutaryhaxor on 2006-10-25
So, I just updated to Edgy Eft because I had some time on my hands. I am in a class learning c++ and need an IDE for c++ programming. I used to use Anjuta, but now the UI got updated and I can't find how to compile. I tried to reinstall Anjuta and now I can't even run it... help?

I don't care if it's another program, but I need something. Btw, I tried KDevelop, but I had the same problem, couldn't find out how to compile.

---

### Post by skymt on 2006-10-25
[Code::Blocks](http://www.codeblocks.org/)? The official release is hard to compile under Linux, but you can get a nightly deb [here](http://forums.codeblocks.org/index.php?board=20.0) ([direct link](http://prdownload.berlios.de/codeblocks/CB_20061025_rev3145_Ubuntu6.06.deb) to the latest as I write this).

---

### Post by finalbeta on 2006-10-25
> **involutaryhaxor said:**
> 
I don't care if it's another program, but I need something. Btw, I tried KDevelop, but I had the same problem, couldn't find out how to compile.

Code blocks is the nicest, but pretty unstable.
To compile, make sure you always start a project, they don't let you compile individual files. No idea why.

---

### Post by acascianelli on 2006-10-25
Anjuta

---

### Post by tzulberti on 2006-10-25
Geany...
It has it sources for drapper but they do work on edgy
[http://geany.uvena.de/Download/Releases](http://geany.uvena.de/Download/Releases)

---

### Post by coder_ on 2006-10-25
How about vim? ;)

---

### Post by involutaryhaxor on 2006-10-25
> **tzulberti said:**
> Geany...
It has it sources for drapper but they do work on edgy
[http://geany.uvena.de/Download/Releases](http://geany.uvena.de/Download/Releases)

thnx, seems pretty good, im gonna try code:blocks next, see which one i like more

---

### Post by FyreBrand on 2006-10-25
Code::Blocks is pretty nice.  I use KDevelop too sometimes, but I haven't gotten the hang of it quite yet. Also I like Kate because the terminal is right there and you can compile and run from right there.

Make sure you have build-essentials installed.  That is make sure you have a compiler and automake utility (unless you write your own make files).  Do a forum search for compiler install or build-essential.  There are a couple really good threads that cover what packages to install to make sure you have every tool you need to compile in C/C++.

edit: Geany is in the repos so that is an easy install.  I'm checking it out now.

---

### Post by jlintz on 2006-10-26
there's always eclipse

---

### Post by kopilo on 2006-10-26
Indeed Eclipse looks really good, however if it is too much for you to download, you could get [Arachnophilia]("http://www.arachnoid.com/arachnophilia/").

---

### Post by amo-ej1 on 2006-10-26
i'm using eclipse and cdt,

it's only a shame that it's a rahter old version of cdt that comes with edgy :(

---

### Post by tzulberti on 2006-10-26
> **kopilo said:**
> Indeed Eclipse looks really good, however if it is too much for you to download, you could get [Arachnophilia]("http://www.arachnoid.com/arachnophilia/").

I think that it has not release any new version in quite a long time:  "Download Arachnophilia 5.2, build 1959 (12/08/2003) (Java)"

---

### Post by bigjimlad on 2006-11-01
removed.

---

### Post by involutaryhaxor on 2006-11-03
Thanks guys, im sticking with Geany

---

### Post by madirajuananth on 2007-04-04
please help me downloading c++ for ubuntu 6.10 free of cost.thank you.

---

### Post by mysticrider92 on 2007-04-04
> **madirajuananth said:**
> please help me downloading c++ for ubuntu 6.10 free of cost.thank you.

The gcc command line C++ compiler is preinstalled on Ubuntu. If you want a different one, open Synaptic (System>Administration>Synaptic Package Manager), and do a search for 'c++ compiler' or just 'c++'. If you want an IDE, Anjuta and Eclipse are both good. Every program in Synaptic is free to get (some are not open source though).

---

### Post by lnostdal on 2007-04-04
no, i don't think a compiler is installed by default .. one need to install it (gcc/g++) by doing:

```

sudo aptitude install build-essential

```

(i wonder how many times i've typed this the last couple of months ..)

---

### Post by Zdravko on 2007-04-04
> **lnostdal said:**
> no, i don't think a compiler is installed by default .. one need to install it (gcc/g++) by doing:

```

sudo aptitude install build-essential

```(i wonder how many times i've typed this the last couple of months ..)

Why do you wonder then? I've repeated it many times - include C++ compiler in the default installation! :-x

---

### Post by madirajuananth on 2007-04-05
i have installed g++ successfully but i don't know how to open & start working with it.please help me.

---

