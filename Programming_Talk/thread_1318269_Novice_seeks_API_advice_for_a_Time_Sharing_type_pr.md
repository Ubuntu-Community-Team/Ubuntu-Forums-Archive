---
title: "Novice seeks API advice for a Time Sharing type program"
date: 2009-11-07
forum: Programming Talk
---

### Post by cptnapalm on 2009-11-07
I am an early middle-aged, novice C programmer and I had an idea for a program which I believe would be of potential use to a number of people.  The functionality of this not yet written software is pretty well defined.  What would be of assistance is a pointer or two in the direction of what APIs to focus on learning so that this potential program might become an actual program.

The basic idea is an old one, really: time sharing.  What brought the idea to mind was an incident where I was busy with my computer and a visiting friend wanted to use it for something else.  Having only the one desktop and a sense of courtesy, I did a user switch so he could use the computer to complete a few tasks.  The incident planted a question in my head: would it not be useful to be able to have an extra monitor, keyboard and mouse hooked up to the same PC and have them act together as another workstation?  This thought gave the potential program its name: virtualstation.

When not in use, everything belongs to the base workstation, vs0.  Other virtualstations can be added and hardware "attached" to it.  For example, vs1 is created and assigned a monitor, a keyboard and a mouse.  Upon vs1's activation, a new X session starts with a login screen on vs1's monitor and only takes input from vs1's hardware which no longer sends input to vs0.  If the new virtualstation is deactivated, vs1's X session closes and all of its assigned hardware reverts to vs0's control.  Some types of external hardware could potentially be used by any of the virtualstations, webcams, for instance; I have not decided on that yet.

Aside from the scenario above which gave impetus to thinking about such a program, it could be useful in other situations.  Think of the utility such a program could provide an internet cafe.  People using the cafe's computers are typically going to be using a web browser and perhaps a word processor or some such.  For this, each seat has its own computer.  What this program could do is to enable the internet cafe to provide more seats for the customers at a lower cost per seat.

The hardware targets for virtual station are video and audio cards, mice, keyboards, web cams and joysticks.  Core machine hardware like CPUs and hard drives are not to be managed by virtualstation.  USB hubs might be able to be assigned to a particular virtualstation with attached hardware also being assigned to it; I do not know if that is feasible or not.

With its functionality in mind, I could use some experienced programmers help in determining which APIs would be best for bringing this program to fruition.  Any other types of comments or advice would also be quite welcome.

---

### Post by slavik on 2009-11-07
I believe this concept existed in the 60's/70's as a dumb terminal. :)

Multics was the OS on the mainframe.

---

### Post by cptnapalm on 2009-11-07
You've got the gist of what I would like to do.  Instead of a dummy terminal with a command line, this would be a dummy workstation with a GUI.

---

### Post by diesch on 2009-11-07
This kind of setup is often called "multi-seat". See e.g. [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX) [http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html) [http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html](http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html)

---

### Post by cptnapalm on 2009-11-07
That is indeed similar, though the phrase "calamitously complicated configuration" comes to mind.  My idea was to have all this below X.  An X session on vs1 should not even know that the hardware for vs0 even exists.  I'm not sure how to go about doing that, amongst other things, so that's why I was posting here.  :D

---

### Post by diesch on 2009-11-08
So you want to manage multiple X servers with dedicated configurations. 

I think that should be the job of an display manager (like xdm, gdm, kdm, ..). Maybe some of them already support something like this so you could just write an administration front end that makes using multi-seat easier. Otherwise you may extend one of them.

---

### Post by tgalati4 on 2009-11-08
I think the hooks within X-windows already exist.  consolekit is supposed to keep track of multiple users and input devices within an X session:

[http://www.freedesktop.org/wiki/Software/ConsoleKit](http://www.freedesktop.org/wiki/Software/ConsoleKit)

Thin clients take advantage of a single strong machine and distributed displays and keyboards.

Multiple mice and keyboards on a single X-display are possible--any thinkpad with a trackpoint and trackpad and multiple mouse buttons--all work together.  Multiple keyboards--just plug in another USB keyboard and it will usually be detected and work alongside a laptop's own keyboard.

apt-cache search mouse

This brings up several items:

x2x
synergy
x11-apps
x11-utils

---

