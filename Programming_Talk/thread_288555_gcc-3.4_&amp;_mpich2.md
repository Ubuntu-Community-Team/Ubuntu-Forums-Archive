---
title: "gcc-3.4 &amp; mpich2"
date: 2006-10-30
forum: Programming Talk
---

### Post by ananghudaya on 2006-10-30
Hi, 

I'm quite new to ubuntu. I'm having a problem setting up the gcc compiler (gcc-3.4) on my ubuntu 6.06. It seems that it would be able to compile, but then it can only be called using the command gcc-3.4, not just gcc. This creates a problem to me as I want to install the mpich2 package and it requires gcc to be installed, but it seems that it couldn't find gcc-3.4. I looked ot the directory and the gcc-3.4 is installed at /usr/bin/gcc-3.4

I don't have internet connection to my machine, so i couldn't install using apt-get.

Please help me:confused:

---

### Post by lloyd_b on 2006-10-30
First question: Why gcc 3.4?  4.1.2 is what's "standard" with the latest Ubuntu.  Does that particular program require the older version?

Since you don't have a "gcc" link in your system, I suspect that you've not installed all of gcc.  Try installing a package called "build-essential" - this'll give you the latest gcc, many other necessary programs/files for compiling, and will set up the default "gcc" link in your system.

If you absolutely must use gcc 3.4:
```

[B]cd /usr/bin
sudo ln -s gcc-3.4 gcc
[/B]
```
This will create a symbolic link connecting "gcc" to "gcc-3.4

Lloyd B.

---

### Post by ananghudaya on 2006-10-30
thanks for the feedback... I tried to install build-essential package, but the trouble is i don't have connection on my ubuntu machine, therefore i need to install dependable packages as well. I  am stuck at the point to install g++-4.0. It prompted that it requires libstdc++-6.4.0-dev. the problem is when I installed this package, it prompted out that it requires g++-4.0:confused: i really confused now....

---

### Post by lloyd_b on 2006-10-30
> I am stuck at the point to install g++-4.0. It prompted that it requires libstdc++-6.4.0-dev. the problem is when I installed this package, it prompted out that it requires g++-4.0 i really confused now....

I suspect that the two g++'s you're looking at have different sub-version numbers.

Use this command with a package to find out what all of it's dependencies are:

```
**apt-cache showpkg {package}**
```

This will list all of the dependent packages.  Then run the same command against each of those, and see what dependencies those have.  Keep at it, and eventually you'll have a complete list...

Question:  Do you have the CD you installed from?  If so, it should have a directory called "pool".  Underneath of this directory you should find ALL of the packages you need (provided that you start with the "build-essential" package from the CD as well).

What program are you using to install the packages?  Synaptic, Aptitude, apt-get, dpkg, ?  

Lloyd B.

---

### Post by ananghudaya on 2006-10-30
i'm using aptitude... 

Fortunately, I'm able to run my apps now... thanks for the info :-D

---

