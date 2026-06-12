---
title: "Problem with ./configure"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by TheBigBadWolf on 2013-02-24
Hi! I just got ubuntu, my very first not-windows system, and I love it so far.
I just have a problem with installing gedit. after I already updated the system and issued
sudo -s
and
sudo apt-get update

I tried to install the unpacked gedit 3.2.6 using
cd /media/[username]/[harddrive]/C/gedit-3.2.6
and then ./configure
first problem: it says permission denied.
then i tried chost -x ./configure

when I do that, it simply skips a line and it appears as if it did nothing. not even issue a warning.

I'm at the end of my wisdom, pleaaase help me!

Thanks,
The big bad Wolf

---

### Post by steeldriver on 2013-02-24
Hello and welcome

Why are you trying to build gedit from source? it is available pre-built from the standard Ubuntu repositories - you can install it from Software Center / Synaptic or by using apt-get

[FWIW I would guess your actual configure error is because your /media/../C/.. directory is on is a Windows filesystem, which doesn't understand Unix executable permissions]

---

### Post by TheBigBadWolf on 2013-02-24
Oooh.. thank you very much, that explains a lot! I'm gonna try that.
...
Alright this is so weird, either it was already installed (which I don't think, since it couldn't be found) or my chost -x ./configure worked, because in the software center it says it's installed.
...
Or I simply don't get ubuntu yet.

Thanks again, I obviously tried to complicate something that wasn't complicated at all! :)

---

### Post by steeldriver on 2013-02-24
Running ./configure on a source package doesn't actually install anything, it just prepares the build environment... and if it *did* install anything it would likely do so outside of the package management system (so Software Center wouldn't know about it)

In any case, gedit is the standard text editor for Ubuntu and should be installed as part of the ubuntu-desktop package - if yours isn't working for some reason we can try to fix that - but installing from source would not normally be required

Cheers

---

