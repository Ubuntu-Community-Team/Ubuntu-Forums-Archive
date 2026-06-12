---
title: "Compiling dvdistaster: bzlib.h not found (dev files installed)"
date: 2012-02-07
forum: Packaging and Compiling Programs
---

### Post by _Smiler_ on 2012-02-07
Hey everyone... I was hoping to use the dvdisaster program to check a load of CDs and DVDs I have. When compiling, I get an error that bzlib.h is not found. 
```
Looking for includes and libraries:
Checking for bzlib.h: /usr/lib/ghc-7.0.3/haddock/bzlib-0.5.0.1 (user supplied, but seems not to work)
bzlib.h not found.
Please specify the include file location using the following option:
--bz2-includes=DIR

```

I have the development files and the debug files (just in case) and have ran apt-file search which returns: 
```
libbz2-dev: /usr/include/bzlib.h
libcomplearn1-headers: /usr/include/complearn-1.0/complearn/complearn-rcbzlib.h
libghc-bzlib-doc: /usr/lib/ghc-7.0.3/haddock/bzlib-0.5.0.1/bzlib.haddock

```

I've tried the following: (I'm not very good at CLI so I'm gonna post every command I've ran in case I'm making a mistake)
./compile--bz2-includes=/usr/include/bzlib.h
./compile--bz2-includes=/usr/include/
./compile--bz2-includes=/usr/include
Those last two are just because I'm unsure whether it's asking for the full path or the directory, and also I'm never sure whether putting a last slash will make a difference.
Also, I've tried those above commands for the other two files that apt-file gave me, just in case they worked. Probably really silly but *shrug* I just wanna check my dvds :(

Curiously, when I cd to usr/include ls doesn't return any bzlib.h. I'm out of ideas. Anyone have any ideas?

Paula

---

### Post by oldos2er on 2012-02-07
Moved to Packaging and Compiling Programs.

---

### Post by drmrgd on 2012-02-07
I myself had a problem with that same library when compiling a different program.  I can't quite recall what worked to fix it (I tried a ton of different things).  I think what I had to do (after basically installing every variant of libbz2 available in the repos!) was manually download and compile bzip2, and then reboot the system so that it was aware of the location of the new location of the library (not sure why this was necessary either, but the compiler kept saying that I didn't have the files until I did this).  

So (and hopefully someone comes along with a less clunky, more elegant solution), you can try to install all of the libbz2 packages in the repos:

```
sudo apt-get install libbz2-1.0 libbz2-dev libbz2-ocaml libbz2-ocaml-dev
```

If your prog still doesn't compile, then try installing bzip2 manually from [http://bzip.org/]("http://bzip.org/"), reboot your system, and try compiling the DVD program again.

Hope that works!

---

### Post by satanselbow on 2012-02-07
Are you using the unstable (79) branch? As it can be exactly that... and is frequently feature missing :(

The stable version is in the repos and relatively up to date - no compilation required ;)

---

### Post by _Smiler_ on 2012-02-08
> **drmrgd said:**
> I myself had a problem with that same library when compiling a different program.  I can't quite recall what worked to fix it (I tried a ton of different things).  I think what I had to do (after basically installing every variant of libbz2 available in the repos!) was manually download and compile bzip2, and then reboot the system so that it was aware of the location of the new location of the library (not sure why this was necessary either, but the compiler kept saying that I didn't have the files until I did this).  

So (and hopefully someone comes along with a less clunky, more elegant solution), you can try to install all of the libbz2 packages in the repos:

```
sudo apt-get install libbz2-1.0 libbz2-dev libbz2-ocaml libbz2-ocaml-dev
```

If your prog still doesn't compile, then try installing bzip2 manually from [http://bzip.org/]("http://bzip.org/"), reboot your system, and try compiling the DVD program again.

Hope that works!
Drmrgod - I have know idea how or why, but installing libbz2 worked. Now I can't seem to figure out what I'd been searching synaptic for the other day...oh well, thanks for your reply, it gave me the right package to search for :D

How does one become proficient at this type of thing...surely Google and Ubuntuforums aren't the only way forward? I mean, how do you develop the Linux/Ubuntu logic? I've tried the documentation but it still seems beyond me. 

Thanks again!!

---

### Post by SeijiSensei on 2012-02-08
> **_Smiler_ said:**
> How does one become proficient at this type of thing...surely Google and Ubuntuforums aren't the only way forward? I mean, how do you develop the Linux/Ubuntu logic?

First of all, you're asking about compiling programs.  That's not an easy task for most people, and it's why most Ubuntu users rely on the repositories.  I can count on one hand the number of applications I've built from source over the past year.

Now if you want to build a personal version of a particular application that already exists in the repositories, then you can use the convenient "build-dep" option to apt-get.  Suppose, for instance, you wanted to build a more up-to-date version of mplayer.  You can run:

```
sudo apt-get build-dep mplayer
```

and it should download and install all the required libraries and header files for you.

---

### Post by SeijiSensei on 2012-02-10
You marked this thread [SOLVED], but you didn't tell us what fixed the problem for you.  Please elaborate so others can learn as well.

---

### Post by oldos2er on 2012-02-12
> **SeijiSensei said:**
> You marked this thread [SOLVED], but you didn't tell us what fixed the problem for you.  

I have removed the 'Solved' tag for the above reason.

OP, please share your solution. The 'Solved' tag is for everyone's benefit, not just yours.

---

### Post by simon_w on 2012-11-18
Am I missing something?  The OP said > I have know idea how or why, but installing libbz2 worked.  (which happens to be the solution I was after...)

cheers!

---

