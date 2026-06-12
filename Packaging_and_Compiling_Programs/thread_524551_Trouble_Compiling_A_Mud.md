---
title: "Trouble Compiling A Mud"
date: 2007-08-13
forum: Packaging and Compiling Programs
---

### Post by Noodels on 2007-08-13
I've been trying to do this for a long time. I've looked thoroughly on Google for source files for muds, preferably in lpc, and every mud I try to compile I fail. I am currently trying to compile this version; lpmud-3.1.2.tar.gz and having no luck. Here is what I am trying to do.

1 - Unload the archive into my home folder into a directory labelled mud.
2 - Go to the file labeled INSTALL and start reading that, I make the empty directories src, bin and lib as instructed in the mud folder.
3 - It then tells me to do this :
Move the game driver source (this code) to the src directory.
I am unsure what to do here, does it mean the file INSTALL that I am reading which appears to have no code whatsoever or to move a whole bunch of files to the src directory? Can someone help me get this mud working?

---

### Post by renzokuken on 2007-08-13
the whole bunch of files,

once you have moved all the files from the original tar.gz files you will need to run commands something like

```
./configure
make
sudo make install

```

to actually compile it.

make sure you have the "build-essential" package installed first.

are there no mud packages in Synaptic?

---

### Post by Noodels on 2007-08-13
> **renzokuken said:**
> the whole bunch of files,

once you have moved all the files from the original tar.gz files you will need to run commands something like

```
./configure
make
sudo make install

```

to actually compile it.

make sure you have the "build-essential" package installed first.

are there no mud packages in Synaptic?

So which files would that be? There's loads of files and I don't think all of them are meant to go in src are they?

---

### Post by renzokuken on 2007-08-13
are there no instructions about. where did you download the source from?

EDIT: i just read the INSTALL file and i think you'll find it means every file that came out of the original lpmud-3.1.2.tar.gz archive

when people say "source" or "source package" they are usually referring to a whole collection of files, often compressed into one zip file for your ease

DOUBLE EDIT: why are you trying to compile something from source? could you just not use gnome-mud which is in the repos?

```
sudo apt-get install gnome-mud
```

---

### Post by renzokuken on 2007-08-13
have a look at 
[http://packages.ubuntu.com/feisty/games/ldmud](http://packages.ubuntu.com/feisty/games/ldmud)
and
[http://packages.ubuntu.com/feisty/gnome/gnome-mud](http://packages.ubuntu.com/feisty/gnome/gnome-mud)

---

### Post by Noodels on 2007-08-13
> **renzokuken said:**
> are there no instructions about. where did you download the source from?

EDIT: i just read the INSTALL file and i think you'll find it means every file that came out of the original lpmud-3.1.2.tar.gz archive

when people say "source" or "source package" they are usually referring to a whole collection of files, often compressed into one zip file for your ease

DOUBLE EDIT: why are you trying to compile something from source? could you just not use gnome-mud which is in the repos?

```
sudo apt-get install gnome-mud
```

Gnome mud is a client for accessing muds. I already have that. What I am trying to do here is get my own engine working.

---

### Post by Noodels on 2007-08-13
> **renzokuken said:**
> have a look at 
[http://packages.ubuntu.com/feisty/games/ldmud](http://packages.ubuntu.com/feisty/games/ldmud)
and
[http://packages.ubuntu.com/feisty/gnome/gnome-mud](http://packages.ubuntu.com/feisty/gnome/gnome-mud)

Okay, I got ldmud off synaptic, I just don't know how to make it do anything.

---

