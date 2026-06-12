---
title: "C compiler not working"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by tallpaul66 on 2008-09-04
I am trying to install webcam software called Camstream. The instructions say to change to the folder containing the installation files and type ./configure. When I do that it tries to create the "make" file (I think) but stops with this error message: configure: error: C compiler cannot create executables
Obviously I am new to Ubuntu and Linux in general but I do understand what a compiler is supposed to do. Is there something in Ubuntu itself that I need to change or authorize to allow the compiler to work or should I just move on to something simpler? If it makes any difference I installed Ubuntu as a dual boot with XP.

---

### Post by oldos2er on 2008-09-04
Ubuntu does not come with a compiler by default, you have to install it. Type "sudo aptitude install build-essential" in a terminal.

---

### Post by tallpaul66 on 2008-09-04
Thank you very much. That solved part of the problem. When I ran it again it complained about QT multithreading. So I found this command: sudo apt-get build-dep camstream which seemed to work. The next step in the install is "make install" which I tried. Now it says "No rule to make target `install'". I am guessing that many people have had problems installing camstream so I will search the forums to see what I can find. I wonder why it does not show up in the add/remove programs list though.

---

### Post by tallpaul66 on 2008-09-04
I managed to get it installed. I was not aware that it was a command line application. It runs okay but does not seem to recognize my Logitech camera.
Oh well, one more problem to solve.

---

### Post by sema_mc on 2008-09-05
I've had same problem as tallpaul66 and after your suggestion, it is solved now. Tnx :)

---

