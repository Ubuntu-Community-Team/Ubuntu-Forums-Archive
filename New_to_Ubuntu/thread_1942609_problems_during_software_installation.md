---
title: "problems during software installation"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by juzaib on 2012-03-17
Hi!

I am completely new on Linux and I am having problems installing Kile ([http://kile.sourceforge.net/help.php#compile](http://kile.sourceforge.net/help.php#compile))

I followed all the instructions, but when I insert

*cmake .. -DCMAKE_INSTALL_PREFIX=$HOME/kile-install -DCMAKE_BUILD_TYPE="Debug"*

I get

[I]CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in                                                                                     
  /home/evandro/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps                       
Call Stack (most recent call first):                                                                                                           
  CMakeLists.txt:5 (find_package)                                                                                                              
                                                                                                                                               
                                                                                                                                               
-- Configuring incomplete, errors occurred![/I]

What could it be?

Thanks!

---

### Post by juzaib on 2012-03-17
No one? =(

---

### Post by zombifier25 on 2012-03-17
You're missing some KDE libraries.
But, why are you compiling the software yourself? It's definitely faster and easier to install it from the repos.

---

### Post by juzaib on 2012-03-17
I don't know why I am doing like this...

Could you teach me how to install it from the repos?

---

### Post by whatthefunk on 2012-03-17
A few ways to do it, from easiest to less easiest:
-Open Muon software center.  Search for Kile (I just checked and its in there) and click install.

-Open Muon Package Manager.  Search for Kile.  Click "Installation" and then "Apply Changes."

-Open a terminal and type:
```
sudo apt-get install kile
```

---

### Post by zombifier25 on 2012-03-17
EDIT: Dang, got beaten :P

The easiest way would be to fire up Ubuntu Software Center, search for the software you want (in this case Kile), click "Install".

Or the faster, but more difficult way (Since you need to know the exact name of the package) would be to enter this into the terminal:
```
sudo apt-get install kile
```or replace kile with any software packages, like firefox, chromium,...
No need for annoying compiles :p

---

### Post by juzaib on 2012-03-17
Thank you guys!

Installed using terminal (just to get used to it!). Running ok! =)

---

