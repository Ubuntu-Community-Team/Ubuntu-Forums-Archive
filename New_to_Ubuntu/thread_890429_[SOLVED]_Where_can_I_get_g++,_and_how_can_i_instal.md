---
title: "[SOLVED] Where can I get g++, and how can i install it?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by jmbawagan on 2008-08-15
I have a computer at home w/ ubuntu, and I want to use g++ for my lessons. I don't have an internet connection at home (so I can't sudo apt-get install it), but I have access at my school. The questions are: Where can I get g++? and How do I install it?

---

### Post by lisati on 2008-08-15
If you already have gcc on your system, you should be able to use g++ as well. The only catch I'm aware of is that build-essential is often needed as well.

---

### Post by nicedude on 2008-08-15
do you mean gcc as in the c+ compiler? if so try running the following command to go into synaptic package manager and then search by name for gcc

sudo synaptic

When you can't find something searching synaptic is way better than trying different apt-get commands :-)

Hope that helps

---

### Post by InfinityCircuit on 2008-08-15
The package you want is definitely build-essential.  It will pull in g++, make, and most of the stuff you need for basic compiling.

---

### Post by jmbawagan on 2008-08-15
I don't have the gnu c++ compiler installed. Can't I just download the package and install it at my computer? Where can I get the build-essential package?

---

### Post by NovaAesa on 2008-08-15
You should always get packages using apt-get. I am right in assuming that you want to download it from the net at school though? If this is the case, you can download it here [http://packages.ubuntu.com/hardy/i386/build-essential/download](http://packages.ubuntu.com/hardy/i386/build-essential/download) and then install at home.

EDIT: You will need to download the dependencies as well, I have a feeling this is just a meta-package.

---

### Post by nicedude on 2008-08-15
"build-essential" and "make" are seperate packages and you need them both to compile anything

sudo apt-get install build-essential

sudo apt-get install make


But I still like synaptic for finding whats there to be installed since you can search via descriptions & in a GUI

---

### Post by eightmillion on 2008-08-15
These are the packages you'll need to start compiling software: [libc6-dev]("http://packages.ubuntu.com/hardy/libc6-dev"), [gcc]("http://packages.ubuntu.com/hardy/gcc") , [g++]("http://packages.ubuntu.com/hardy/g++"). It may be a good idea to also get [make]("http://packages.ubuntu.com/hardy/make").

---

### Post by wenuswilson on 2008-08-15
All of the stuff I need for g++ came on my copy of Ubuntu already, not sure if this is how it should be done, but for the most part I just use.

$ g++ filename.c
$ ./a.out

in my terminal, then again I'm self learning the whole damn language.
Use $ cd to find the files.

---

### Post by Irihapeti on 2008-08-15
I believe that the build-essential stuff is actually on the live CD. Check that the live CD option is ticked in System -> Administration -> Software Sources, and then install build-essential via Synaptic.

It's a while since I did this, so it's possible I've got it wrong and not all the packages are on the live CD. In that case, you can note which ones are missing and download them from packages.ubuntu.com with another computer.

---

### Post by jmbawagan on 2008-08-20
sorry for the late reply... 
I downloaded the packages for gcc (and the other dependencies eg. libc6-dev, gcc , g++, make) and just installed in in my computer. Well, thanks to you guys, I can compile my code now! Thanks a lot!

---

