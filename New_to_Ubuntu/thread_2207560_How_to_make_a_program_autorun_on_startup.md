---
title: "How to make a program autorun on startup"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by decka on 2014-02-24
hi guys, today i just installed cairo-dock on my lubuntu,  but i want it to run automatically when i boot up my pc, i've read all tutorial for this on google, like find "system>preferences>session", but i can't find it.
so how do i do this?

---

### Post by vasa1 on 2014-02-24
If you're using Lubuntu 13.10, the autostart file is now here:
~/.config/lxsessions/Lubuntu/autostart
This is nothing but a plain text file with one exacutable per line. You may want to provide the entire path.

My autostart looks like this:

> 
pcmanfm --desktop
/home/vasa1/.dropbox-dist/dropbox

Note, there's no need to have "@" to begin the line as was the case in 13.04.

---

### Post by Bucky Ball on 2014-02-24
> **decka said:**
> ... "system>preferences>session", but i can't find it.
so how do i do this?

^^^
This. You just need to find it. It should be 'Sessions & Startup'.

* Ninja-ed by vasa1, who appears to be more familiar with Lubuntu. ;)

---

### Post by vasa1 on 2014-02-24
> **Bucky Ball said:**
> ^^^
This. You just need to find it. It should be 'Sessions & Startup'.

* Ninja-ed by vasa1, who appears to be more familiar with Lubuntu. ;)

There was a big change from 13.04 > 13.10 in how certain basic things were done. Unfortunately, documentation still isn't easy to find. It's an attempt to provide a "united" GUI for a lot of things. In [this link]("http://askubuntu.com/questions/362263/what-is-default-applications-for-lxsession-in-lubuntu-13-10"), you can see "Autostart" in the third tab on the left of the lower image. The path I provided is to the actual file that is modified.

---

### Post by decka on 2014-02-28
so that's why i can't find it, thank you guys for the enlightenment

---

