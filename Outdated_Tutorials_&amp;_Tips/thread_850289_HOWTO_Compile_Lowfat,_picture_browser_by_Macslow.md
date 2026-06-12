---
title: "HOWTO: Compile Lowfat, picture browser by Macslow"
date: 2008-07-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Sam Lars on 2008-07-05
From Macslow:
There isn't any install process. lowfat is far from finished and it is only meant to be run right out of this directory. See the start-lowfat.sh script.

This means that it will not install like a normal program in the repos, but will just be run from where we put it.  This program is by far not a finished product.  It's meant for developers only.  It's pretty cool to play around with, though. :)

Ok, that in mind, let's get started.
First, we need git, to copy the source from Macslow's site.
```
sudo apt-get install git git-core
```
Now, choose a directory in a terminal to download Lowfat to.  This command will then download Lowfat into a folder called "lowfat" in the directory you're in with the terminal.  The default is your home folder.
```
git clone git://people.freedesktop.org/~macslow/lowfat
```
Now that you have the source code, we need to compile it, but we need a few packages first.
```
sudo apt-get install automake autoconf build-essential libtool gobjc libglib2.0-dev libglib2.0-0 libgtk2.0-0 libgtk2.0-dev libsdl1.2-dev libsdl-image1.2 libsdl-image1.2-dev
```
These programs may not all be necessary or enough for all of you.  Please let me know about any errors you get from that or the following commands, and I'll modify this accordingly.
Now to compile it.
```
./autogen.sh
```
This should have a coulple of "ok"s and some *info*.  No errors.
```
./configure
```
This should end with some lines beginning with
```
config.status:
```
and no errors.
```
make
```
This will spit out a bunch of stuff and eventually end with four lines like
```
make[2]: Leaving directory...
```
If you get errored out of any of that, complaining about a missing library or something, let me know.
You should now be able to start Lowfat with
```
./start-lowfat.sh
```

It flickers where my Conky and stalonetray are, but other than that it's not bad.
I haven't figured out how to change what images it browses.  If I add images to the test-images directory inside the lowfat directory, they don't load.  I tried a symlink to a directory of jpegs, and nothing loaded.  I added some images of my own and named them as the test images, and they loaded, but with the dimensions of the old test images, so they were distorted...

> **artichoke said:**
> 
i : show **i**nfo
  l : **l**oad images
  q : **q**uit

Note that I had to Tab to get to the load images dialogue box.

---

### Post by artichoke on 2008-08-28
Thanks for the HowTo.

A bit of rootling around in the code (specifically src/lowfat.cpp:402 onKey()) show the following keystrokes:

[CENTER]  i : show **i**nfo
  l : **l**oad images
  q : **q**uit
[/CENTER]
Note that I had to Tab to get to the load images dialogue box.

---

### Post by b3n87 on 2009-01-14
This prog is wicked, its more of a "proof-of-concept" but still very good!

---

### Post by durand on 2009-01-14
Pretty neat. Would be very cool with wiimote tracking.

---

### Post by joesnose on 2009-03-03
Nice one Sam, great how to.

---

