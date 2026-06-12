---
title: "[SOLVED] .tar.bz install question"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-10
hi
I downloaded the latest (1.4.4) version of battle for wesnoth
and got the cardboard box icon of the .tar.bz2 which I extracted using the archive manager onto the desktop
I now also have a folder called wesnoth 1.4.4 on the desktop
What is the next stage to get the game to run?
I tried reading the install file but was told there was no application suitable for this
I have the older version of the game from synaptic - can I somehow update through that?
Thanks in advance for any assistance

---

### Post by Elfy on 2008-08-10
I assume you got the source package - you need to compile it, [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

There is a .deb available on getdeb, same version which should install with a doubleclick
[http://www.getdeb.net/release/2957](http://www.getdeb.net/release/2957)

It is best to get .deb files if it possible.

---

### Post by Troll_the_Great on 2008-08-10
Try this link too for compiling from source.
Cheers! 
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by bumanie on 2008-08-10
You also need build-essential which is a "C" compiler with the necessary libraries. > sudo apt-get install build-essential

---

### Post by LTFC2020 on 2008-08-10
thanks everyone, however I don't really want to be getting into code
I tried the correct wesnoth file from getdeb - gutsy 32 but got the following error message:
error: dependancy is not satisfiable: wesnoth data
any ideas why this is?
another question/s -
why are there so many differnet downloads and do I need to download all of them?

---

### Post by Nepherte on 2008-08-10
Before you install wesnoth, you need to install all the other files first:   wesnoth-data  (36.5 MB)  ,  wesnoth-server  (472.5 kB)  ,  wesnoth-editor  (880.7 kB)  ,  wesnoth-music  (75.4 MB)  ,  wesnoth-campaigns  (31.4 MB)

---

### Post by Keith Hedger on 2008-08-10
the dependency's you are missing is all the game data so you will have to install this first but if i was u i would just use the version in the repos as all the dependency's will be taken care of for u. why are u trying to do this the hard way?

---

