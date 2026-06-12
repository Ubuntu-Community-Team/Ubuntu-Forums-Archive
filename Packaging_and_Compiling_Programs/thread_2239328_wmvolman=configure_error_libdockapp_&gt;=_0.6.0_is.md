---
title: "wmvolman=configure: error: libdockapp &gt;= 0.6.0 is required."
date: 2014-08-13
forum: Packaging and Compiling Programs
---

### Post by Andy_Crowd on 2014-08-13
Hello everybody!

I got a problem with compiling of [*wmvolman*]("https://github.com/raorn/wmvolman") dockapp.
I have installed the [libdockapp-dev]("http://packages.ubuntu.com/sv/lucid/libdockapp-dev") package but still getting the same error.

I used same steps as [here]("http://www.linuxforums.org/forum/applications/199305-wmvolman-2-0-1-install-problems.html") but there were a different errors and was compiled on Arch Linux if I remmember correct. It would be perfekt if someone could also do a *deb* package.

I also problem with compiling one more package.
*[wmudmount-2.2]("http://sourceforge.net/projects/wmudmount/files/wmudmount/")* shows errors like: *Package gnome-keyring-1 was not found in the pkg-config search path* even if it is installed. If I am using the *./configure --without-gnome-keyring* it show a lof of other erors that packages are missing, I have installed many but it cannot find any. What am I doing wrong?

Please test and confirm my errors.

---

### Post by steeldriver on 2014-08-13
What version and architecture of Ubuntu are you building on? what version of libdockapp-dev is actually installed?

---

### Post by Andy_Crowd on 2014-08-13
*Linux wmaker 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux*
Installed from *mini.iso*
I am using WindowMaker for desktop environment.
I made a link to it in the first post: Paket: libdockapp-dev (1:0.5.0-3) [universe]
I installed  *apt-get install libdockapp-dev* 

I found a part of problem now, thanks. I had to manualy download and install needed packges, 
[libdockapp2]("http://packages.ubuntu.com/utopic/amd64/libdockapp2/download") , [libdockapp-dev]("http://packages.ubuntu.com/utopic/libdockapp-dev") 
Look like apt-get cannot install leatest packages. wmvolman is working now. Why no one adds it to ubuntu deb packages?

---

### Post by steeldriver on 2014-08-13
OK glad you got it fixed - please mark the thread [SOLVED]

As to why... I guess it's just one of those compromises that goes into making a 'stable' distribution

---

### Post by Andy_Crowd on 2014-08-13
I created a wmvolman_amd64.deb package for my personal use with help of the [guide]("http://packaging.ubuntu.com/html/packaging-new-software.html"). Thanks for you help!

---

