---
title: "Computer suddenly shuts down while doing specific things"
date: 2016-09-03
forum: New to Ubuntu
---

### Post by mohamadc on 2016-09-03
Whenever I run this command my computer suddenly shuts off

sudo dpkg --configure -a

It also shuts off when trying to change between the open source driver to nvidia driver. Also, when playing minecraft, creating a new world, waiting a couple seconds, and then my computer will suddenly shut off.

I'm on 16.04.1 LTS.

Specs: [http://paste.ubuntu.com/23128825/](http://paste.ubuntu.com/23128825/)

---

### Post by oldrocker99 on 2016-09-03
This sounds like a hardware problem. How old is your computer? See if you can hold SHIFT wile booting to get to the GRUB screen, and select Memtestx86, which will do an extensive memory test. I'd say that bad memory is a likely problem. It **could** be your CPU, but I'd check memory first.

---

### Post by ajgreeny on 2016-09-03
Could also be a dodgy PSU, but that is more difficult to diagnose, especially if a desktop machine..

Memtest is very easy to run so a good place to start.

---

### Post by poorguy on 2016-09-03
Another point of interest is to dust your computer vents out with a blast from an air hose.

---

### Post by RobGoss on 2016-09-04
If there is a over heating problem it's also good to use a cooling plate if you're using a laptop not sure if it's a desktop or laptop

---

### Post by autocrat on 2016-09-05
It could be an issue with the GPU. Did it work prior to playing with the drivers?

---

