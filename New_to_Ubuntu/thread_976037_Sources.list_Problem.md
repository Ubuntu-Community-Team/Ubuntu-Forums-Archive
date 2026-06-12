---
title: "Sources.list Problem"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by PreyToGod on 2008-11-08
I tried to install Avant Window Navigator tonight in Intrepid. Without thinking, I followed the instructions from > [http://ubuntuforums.org/showthread.php?p=2307772](http://ubuntuforums.org/showthread.php?p=2307772) for Hardy and now my package manager doesn't work as well as any apt commands in terminal.

Here is an example of my problem:
> keegan@Oh-Snaptop:~$ sudo apt-get update
E: Type 'echo' is not known on line 58 in source list /etc/apt/sources.list

Help?

---

### Post by m_duck on 2008-11-08
Can you post your /etc/apt/sources.list file? It looks like you just have a few lines in it which contain the word "echo" in it, which shouldn't be there.

Only the parts that look like:
```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
  and
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

```from the tutorial should be present in the sources.list file (as well as the original sources).

EDIT: Welcome to the forums!

---

### Post by taurus on 2008-11-09
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove line 58 from it.  Save it and close gedit window.  Then, run

```
sudo apt-get update
```

---

### Post by PreyToGod on 2008-11-09
Ugh, I'm so new at this. Could you tell me how to view the sources.list file?

Edit:
Never mind. Your fix worked, Taurus. Thanks to both of you for the help.

---

