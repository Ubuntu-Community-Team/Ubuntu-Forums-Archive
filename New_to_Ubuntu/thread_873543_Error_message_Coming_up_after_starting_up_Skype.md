---
title: "Error message Coming up after starting up Skype"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by maloko1 on 2008-07-29
I'm getting this error message after opening skype in wine.

" Access violation at address 7DF6893C in module 'winealsa.drv'. Read of address 00000048. " 

and i have no clue what that means or what's gone wrong. Anyone know?

---

### Post by bobnutfield on 2008-07-29
It appears you are running Skype through Wine.  Skype is available natively on Ubuntu.

Bob

---

### Post by Methuselah on 2008-07-29
There is native skype for linux.

---

### Post by maloko1 on 2008-07-29
Thanks! accept now i'm getting that " Wrong achitecture 'i386' " message but i'm sure i saw something about that somewhere else in the forums.

---

### Post by bobnutfield on 2008-07-29
What version of Skype?  If you have a x86-64 kernel then the 32bit Skype should still work.

---

### Post by maloko1 on 2008-07-29
Hm i'm not sure what that is but its skype-debian_2.0.0.72-l_i386.deb
i've everything i can think of.

---

### Post by bobnutfield on 2008-07-29
Just open a terminal and type:

> sudo apt-get install skype

That will install it on your system.

Bob

---

### Post by Methuselah on 2008-07-29
He might have to enable the medibuntu repos first.
See here for how:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just copy and paste into the terminal the instructions relevant to your version under 'adding the repository'

---

