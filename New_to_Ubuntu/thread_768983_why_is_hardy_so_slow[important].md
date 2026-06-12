---
title: "why is hardy so slow[important]"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Smatt454 on 2008-04-26
I just upgraded from 7.10 and everything is so slow
Adept is sooo slow...and compiz lags horribly. It was fine before the upgrade.

what ideas???

---

### Post by Nesman on 2008-04-26
Try providing some more info.  How much RAM do you have?  Is your computer using a swap partition, and if so: how large?  

You might want to install htop:```
sudo apt-get install htop
``` and run it.  See what your RAM and cpu are doing.  Maybe something is hogging them.

---

### Post by Smatt454 on 2008-04-26
i have 512 MB of RAM and a 252MB swap partition (i know it should be 1GB but thats what Kubuntu gave me by default, i didnt set up my partitions manually)

nothing seems to be hogging CPU time.

i try restarting, reinstalling compiz. Nothing =/

this is a really big problem =/

EDIT: as i said it was fine before the upgrade. besides upgrading, i didnt change anything, software or hardware

---

### Post by Smatt454 on 2008-04-26
its getting worse, i reinstalled my drivers now compiz and xorg switch from using 70% of the CPU o_O i never had this problem with 7.10....

---

### Post by nicedude on 2008-04-26
look in your system monitor, something has to be using your resources and it should tell you what. If something in there is then kill the process if its not vital and see if your system snaps back.

What kind of graphics card do you have? and what driver are you using for it?

---

### Post by knavarathna92 on 2008-04-26
There has been a history of problems with ATI cards and compiz lag in heron.

---

### Post by Smatt454 on 2008-04-26
im using nvidia o_O

---

