---
title: "help on compiling c program"
date: 2012-05-03
forum: Packaging and Compiling Programs
---

### Post by neil_1 on 2012-05-03
i found a chess program which i would like to compile
[http://www.craftychess.com/crafty-23.4.zip](http://www.craftychess.com/crafty-23.4.zip)

i have tried make, make linux-AMD64, linux-64, all gave me errors of some sort (there's a makefile included in the project)

it works fine on my friends windows though

can someone check it out ?

---

### Post by gmargo on 2012-05-03
No need to compile.

Crafty-23.4 is already available and packaged for 11.10 Oneiric: [http://packages.ubuntu.com/oneiric/crafty](http://packages.ubuntu.com/oneiric/crafty)

---

### Post by neil_1 on 2012-05-03
well, i have come across that but, me and my group at university are supposed to work with this code which is going to be the base for a robot arm to play chess, so i would like to be able to compile it

---

### Post by neil_1 on 2012-05-05
anyone ?

---

### Post by Hubi17 on 2012-05-06
I just tried it on my system. If I compile it with the debug flag it seems to work.

---

### Post by codingman on 2012-05-06
Have not tried it but try using GCC, it's the best Gnu C,C#,C++ compiler around.

---

### Post by Hubi17 on 2012-05-06
Hmm
Just realised that in the Makefile for "linux" and "linux-amd64" CXX is set to g++
However for the "debug" profile CXX was set to gcc

However CC was set to gcc in both, so its not the compiler thats the problem.
Seems that some options for "linux" are not compatible, or missing libs, I believe.

---

### Post by MrQuincle on 2012-05-13
> **neil_1 said:**
> i found a chess program which i would like to compile
[http://www.craftychess.com/crafty-23.4.zip](http://www.craftychess.com/crafty-23.4.zip)

I would recommend this:
```

mkdir ~/temp
cd ~/temp
apt-get source crafty
sudo apt-get build-dep crafty -y
cd crafty*
make help
make linux-amd64 # this one or make linux

```

This works flawlessly on my system and you'll have automatically the right build tools and the proper patches for your Ubuntu system.

---

