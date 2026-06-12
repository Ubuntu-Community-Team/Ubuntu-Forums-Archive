---
title: "How to compile the same program for another ubuntu release"
date: 2009-12-13
forum: Packaging and Compiling Programs
---

### Post by ras123 on 2009-12-13
Hi,
I had compiled and distributed some programs for hardy in launchpad.net, now I need to make versions for jaunty and karmic. I packed with debuild -S -sd but when uploaded launchpad rejected the same.
So please let me know how to make versions for jaunty and karmic.
Thanking You,
Ras

---

### Post by SevenMachines on 2009-12-14
there are a few different ways to do this in launchpad (as far as i know)
1. create a separate ppa for each distribution
2. or have one ppa and copy the built binaries to the other releases but in the same ppa (note, these are not rebuilt for each release)
3. or vary the package names to represent the different release names, ie, mypackage-karmic mypackage-hardy, etc, and put these in the same ppa (these will be built for there respective release)

personally i think number 1 is the cleaner choice, although i dont always do that :)

---

### Post by Yellow Pasque on 2009-12-17
Create chroots for your other OS's

---

