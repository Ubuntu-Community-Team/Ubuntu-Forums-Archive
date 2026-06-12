---
title: "g++ and ncurses"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by AllanLindh on 2012-02-29
makefiles don't seem to be able to find
g++  and
ncurses
even though they may be here

when I type g++ it just gives instructions on using get-app
   but that doesn't help

sure would appreciate any help on determining if they are installed
  standard fresh install of ubuntu-32 on an old PC
everything else seems to be working
thanks
Allan

---

### Post by jerome1232 on 2012-02-29
My first question is do you have build-essentials installed? If not install it.

My second thought is you might need the development versions, I would search like this, the two marked in red look like good canidates to me. What is it your trying to compile?

```
jeremy@voiceserv:~$ apt-cache search ncurses | grep dev
[COLOR="Red"]lib64ncurses5-dev - developer's libraries for ncurses (64-bit)
libncurses5-dev - developer's libraries and docs for ncurses[/COLOR]
libncursesw5-dev - developer's libraries for ncursesw
btscanner - ncurses-based scanner for Bluetooth devices
libcunit1-ncurses-dev - Unit Testing Library for C (ncurses) -- development files
libcurses-ocaml-dev - OCaml bindings for the ncurses library
libghc6-hscurses-dev - ncurses bindings for Haskell - development files for GHC6
libkaya-ncurses-dev - Ncurses binding for kaya
libkaya-ncursesw-dev - Ncurses binding for kaya
libtexttools2-dev - Ada and C++ library for writing console applications: development
libvuurmuur-dev - netfilter frontend (library development)

```

---

### Post by AllanLindh on 2012-03-01
Sorry, but I'm dumber than you realize

How do I install *build essentials*?

Can find a button under apps/system for an uninstalled package
Synaptic Package Manager, but double clicking on icon doesn't seem to do anything

It's just been a very long time since I had to fight my way through a Linux/UNIX thicket

Thanks very much

---

### Post by AllanLindh on 2012-03-01
when I type
sudo apt-get install build-essential checkinstall

I just get

allan@allan-ThinkCentre-M55:/usr/local$ sudo apt-get install build-essential checkinstall
[sudo] password for allan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential
E: Unable to locate package checkinstall

---

### Post by jerome1232 on 2012-03-01
is this a brand new installation? Run update first.

```
sudo apt-get update
sudo apt-get install build-essential checkinstall
```

I'm still curious as to what it is your trying to compile, there is probably an easier way to go about it than compiling yourself.


edit:In synaptic you should be able to hit "reload", to get the same result, checking build-essential and then clicking apply should install the package, I usually just use apt-get though so I don't have much experience with synaptic. I just realized the package is called build-essential, not build-essentials :D

---

### Post by AllanLindh on 2012-03-01
What I'm trying to compile from source are C programs for processing genomics files (ie lists of nucleotides from various creatures genes).  Only available as source.  Quite good packages, with serious people behind them, I just can't get beyond the essentials to get things compiling.  Do have some compiled and running, but have about 5 different sets of programs have to have running.

I'll try your update suggestions.

This is very kind of you
Allan

---

### Post by jerome1232 on 2012-03-01
Do they come with documentation that tells you how to compile them? Perhaps some documentation from the web site?

Generally the author will provide details about what packages you need, it can be quite a headache to figure it out on your own. That build-essentials package I'm asking you to install provides the general basics needed for compiling, most packages will want more in addition to that.

Essentially you will be running the configure script (if your source code has one that is) watching for errors and installing any packages it cries about. Usually if it says it wants, for example, ncurses5, you'll want the dev version. In Ubuntu all dev packages are designated with a -dev at the end (like libncurses5-dev or similar)

Good luck!

---

### Post by AllanLindh on 2012-03-01
Sir, you are a wonder
The udates went fine.
the build essential went fine
and one of my program packages
   the one that required g++
seems to have compiled just fine

I'll keep looking for the ncurses files

Thank you very much
Allan

---

### Post by AllanLindh on 2012-03-01
They do come with cursory documentation
They just aren't designed for beginners like me
But thanks to you, tonite I'm ahead on points
thanks again

---

### Post by jerome1232 on 2012-03-01
My best guess is to install libncurses5-dev.


If it still complains about ncurses hit the documentation to see if it wants a specific version. If it does the real fun begins.

---

### Post by AllanLindh on 2012-03-01
You were exactly right about the ncurses developers pack
found it, installed it
recompiled
no errors
You ever need a favor
just ask
Allan Lindh

---

