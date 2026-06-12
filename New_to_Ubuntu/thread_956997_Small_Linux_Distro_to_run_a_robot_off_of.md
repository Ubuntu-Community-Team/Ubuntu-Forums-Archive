---
title: "Small Linux Distro to run a robot off of"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by anti-node on 2008-10-23
As the title says i am looking for a distro that can be developed on relativly easely. As i am new to linux what would you recomend for a distrobution that can run off of a USB stick that takes up preferably less space than 4 GB when installed. As it is going to be acsessed through SSH it does not need to have mouse or monitor support. Preferably it would be close to bug free because it has to run a Autonomous Robotic Vehicle. Suggestions??

---

### Post by bsharp on 2008-10-23
If I were you I would take a look at [Linux From Scratch]("http://www.linuxfromscratch.org/").

---

### Post by quirks on 2008-10-23
Damn Small Linux is probably the way to go:
[http://www.damnsmalllinux.org/index.html](http://www.damnsmalllinux.org/index.html)

It was built to be run on USB sticks.

---

### Post by Mud.Knee.Havoc on 2008-10-23
You can get a minimal Debian install and just load the programs that you need (ssh, etc). There are a handful of distros that are perfect for running off of USB sticks (Damn Small Linux, Puppy Linux, Slax, Wolvix), but these are expected to run as GUI-based desktops.  Barebones Debian might be the easiest to customize the way you want it.  It'll be tiny, too (4GB is loads for a lightweight linux setup).

The good thing about Debian is that most of the advice you see on the Ubuntu Forums can be used with Debian, as well.

I doubt you'll find any OS (linux or otherwise) that has no bugs.  There are continuously updates to programs and services.  I think you should probably worry more about whatever kind of software is going to be running your robot.  If it's full of bugs, it doesn't matter what you're running it on.

---

