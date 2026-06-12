---
title: "How to : install  Intel(R) Fortran Compiler 10.1.011 for Linux"
date: 2008-01-11
forum: Programming Talk
---

### Post by Claus7 on 2008-01-11
Hello,

The installation of ifort compiler is not so difficult, at least in my case. The documents which accompany the compiler are very helpful. I post this so as someone to avoid a loss of time in some minor issues. The installation was done in Ubuntu Gutsy Gibbon 7.10.

At first one has to download the right version of the compiler for one's computer. First of all what it counts is the architecture of the computer and secondly, yet most importantly, is the operating's system architecture. For example you might have a 64bit processor, yet your operating system might be 32 bit. Then you have to choose the compiler for the 32 bits.

Helpful commands in order to see the architecture of your computer are the following:

```
lshw | less
```

```
uname --all
```

from 

[http://ubuntuforums.org/showthread.php?t=268515](http://ubuntuforums.org/showthread.php?t=268515)
[http://ubuntuforums.org/showthread.php?t=662700&highlight=lshw](http://ubuntuforums.org/showthread.php?t=662700&highlight=lshw)

I downloaded for my computer the 32bit version of the compiler.
I untared the tar file and I went in the untared folder. When I tried to lanch the installation script, a message that no g++ was installed appeared. 

I went to synaptic and typed g++. There I found exactly the package with the same name and I installed it with the dependencies it required. I was unable to do so without having the Ubuntu cd. So for me it was impossible to download the packages from the internet. The sudo apt-get install g++ command didn't make any difference (it required the cd too). 

When I installed g++ I initialised the installation of the fortran compiler. What was needed was the registration key. I did the unsupported installation and I didn't change the default folders for the installation.

In order to be able to use the compiler I typed :
```
vim .bashrc
```

and I added the line
source /opt/intel/fc/10.1.011/bin/ifortvars.sh

I hope that this was helpful,
Regards!

---

### Post by LaRoza on 2008-01-11
See the stickies if you are new to this language in Linux.

---

