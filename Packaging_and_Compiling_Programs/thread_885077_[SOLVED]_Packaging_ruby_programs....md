---
title: "[SOLVED] Packaging ruby programs..."
date: 2008-08-09
forum: Packaging and Compiling Programs
---

### Post by viciouslime on 2008-08-09
How can I create a deb file of a program written in ruby? All the guides I've found only eveer refer to c/c++ and I can't figure out how to adapt them.

Ideally, I want to use launchpad's ppa, so I need to be able to make a source package...

Thanks in advance for any help :D

---

### Post by viciouslime on 2008-08-11
For anyone else who is stuck with this, I would recommend learning by example.

Create a new temporary directory and run "apt-get source <prexisting ruby package here>" this will download the source package of a ruby package that already exists in the ubuntu repos, including its debian folder and any makefiles etc so you can learn by example :)

---

