---
title: "Anjuta crashes"
date: 2007-11-29
forum: Programming Talk
---

### Post by jespdj on 2007-11-29
Are there people using the Anjuta IDE here?

I'm just trying it out but so far I'm not impressed. I tried making a simple GTK "Hello World" project, by first creating a project with the wizard, and then selecting File / New / Glade File. It crashes with a long stacktrace when I try to make a Glade file.

It crashes also when I select Settings / Plugins and try to activate the API Help plug-in.

I'm using Anjuta 2.2.0 which is in the Ubuntu 7.10 repository.
Do you use Anjuta, and do you have similar problems?

Bug reports: [500473]("http://bugzilla.gnome.org/show_bug.cgi?id=500473"), [500475]("http://bugzilla.gnome.org/show_bug.cgi?id=500475").

---

### Post by kh_naba on 2007-11-29
See:
[https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/125343](https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/125343)

Fix:
[http://ubuntuforums.org/showthread.php?t=581449&highlight=anjuta](http://ubuntuforums.org/showthread.php?t=581449&highlight=anjuta)

---

### Post by jespdj on 2007-11-29
I added
```
deb http://ppa.launchpad.net/robster/ubuntu gutsy universe
```
to my /etc/apt/sources.list, did
```
sudo apt-get update
```
and removed Anjuta, and installed Anjuta again, however the wrong, crashing version is installed again. How do I make apt-get or Synaptic pick up the right version?

---

### Post by jespdj on 2007-11-29
That repository didn't work, so I downloaded the sources for Anjuta myself and after configuring / installing necessary libraries / building / installing I now have a working Anjuta version 2.2.2. :)

---

### Post by scavenger2008 on 2007-12-08
It worked like a charm, I can now edit glade files from within Anjuta. But Anjuta uses an code-generated window instead of my nice and shiny Glade file! How can I make sure Anjuta chooses the right one?

(using Glade 3, newest Anjuta, Gutsy, all deps installed)

---

### Post by roberto.ur on 2008-02-05
grrrrr

it is "main" not "universe"
deb [http://ppa.launchpad.net/robster/ubuntu](http://ppa.launchpad.net/robster/ubuntu) gutsy main

or 
deb [http://ppa.launchpad.net/robster/ubuntu](http://ppa.launchpad.net/robster/ubuntu) gutsy main universe

i don't know if there is actually something in universe

hours hours.... grr:mad:

---

### Post by DugDra on 2008-02-06
> **scavenger2008 said:**
> It worked like a charm, I can now edit glade files from within Anjuta. But Anjuta uses an code-generated window instead of my nice and shiny Glade file! How can I make sure Anjuta chooses the right one?

(using Glade 3, newest Anjuta, Gutsy, all deps installed)

Hi
I'm just working my way through this so this might be wrong but it gets Glade3 into Anjuta. I open the glade3 file in Anjuta. At that point I can view and modify Glade just as I would in standalone Glade.

So far Anjuta seems to work OK.  I wrote some terminal programs in C that compiled and ran fine.  I am currently trying to do some of the GTK example programs. These don't seem to work with Glade3. I have a C and C++ programing background but have found the Linux transition information very terse and in a lot of cases enough out of date that it is necessary to know something that this intermediate windows programmer doesn't know.  

So far I have only found one GTK Glade3 tutorial.  It compiles with GCC and runs but is three parts and the third part is not finish.  I'm at work now and I'm old and slow remembering but you can google "Glade3 GTK tutorial" and find it. Micha Carrick did an excelent job explaining Glade3 and has implement the C code framework to go with the GUI.  I ran into one problem. If you try to adapt the program to use a button gtk-builder-convert will not convert the .glade file to .XML.

Good luck
Doug Drader

---

