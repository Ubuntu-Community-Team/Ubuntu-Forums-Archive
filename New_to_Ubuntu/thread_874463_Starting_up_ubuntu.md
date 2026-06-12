---
title: "Starting up ubuntu"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by napsta on 2008-07-30
I've already installed ubuntu onto a second hard drive (My family uses windows unfortionatly) but when ever I boot-up the computer is will go strait to windows without showing a choise between the two
1.Why
2.How can I get onto ubuntu
3.What can I do to show a choice at the start up

---

### Post by knightcoder on 2008-07-30
Your boot records should reside on the primary hard drive. Your secondary hard drive may contain Ubuntu, but its boot loader should be in the primary.

Install grub in the primary drive and specify to it saying ubuntu is in the secondary drive.

---

