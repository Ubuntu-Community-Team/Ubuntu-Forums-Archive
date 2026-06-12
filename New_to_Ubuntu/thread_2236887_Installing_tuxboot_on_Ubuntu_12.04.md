---
title: "Installing tuxboot on Ubuntu 12.04"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by chris_v2 on 2014-07-29
Hi, I'm new to linux and I'm trying to install tuxboot to linux. I downloaded the tarball file at [http://sourceforge.net/projects/tuxboot/files/](http://sourceforge.net/projects/tuxboot/files/) and I have followed the directions in the readme file, but whenever I try to install the files I get an error message. Here's what I've done so far/ gotten:

In the readme file the instructions are: 
1. Extract the tarball and cd to it

2. Run either the "INSTALL" script, or the following commands:

sed -i '/^RESOURCES/d' tuxboot.pro
lupdate-qt4 tuxboot.pro
lrelease-qt4 tuxboot.pro
qmake-qt4 "DEFINES += NOSTATIC" "RESOURCES -= tuxboot.qrc"
make

when I run these commands, I get this output from the terminal:
/usr/bin/uic-qt4 tuxboot.ui -o ui_tuxboot.h
make: /usr/bin/uic-qt4: Command not found
make: *** [ui_tuxboot.h] Error 127

I get the same result both by running the install file and by running the other commands. 
I don't know what to make of these error messages and I'm very new linux in general so any help would be greatly appreciated!

---

### Post by ubudog on 2014-07-29
Looks like you're missing the uic-qt4 program, so try this:
```
sudo apt-get install libxtst-dev build-essential libqt4-dev qt4-qmake
```

---

### Post by Bucky Ball on 2014-07-29
That is VERY old and not maintained.

[http://sourceforge.net/projects/tux2live/files/Tux2live/Stable/](http://sourceforge.net/projects/tux2live/files/Tux2live/Stable/)

That's from 2011 so don't like you're chances. From their website, the list of supported, and long dead, Ubuntus:

11.04(Natty Narwhal),10.10(Maverck Meerkat),10.04(Lucid Lynx),9.10(Karmic Koala),9.04(Jaunty Jackalope),8.10(Intrepid Ibex),8.04(Hardy Heron),7.10(Gutsy Gibbon),7.04(Feisty Fawn),6.10(Edgy Eft), 6.06(Dapper Drake)

Nothing's happened with it since 2011, but good luck with it. ;)

(Pity, looks interesting. :-k)

---

### Post by chris_v2 on 2014-07-29
Thanks, that was the problem and now it's working fine!

---

### Post by Bucky Ball on 2014-07-29
> **chris_v2 said:**
> Thanks, that was the problem and now it's working fine!

Great! Hopefully there are no changes that make it stop and it will work until 2017. I might give it a look. ;)

Please mark thread as solved by following the second link in my signature to help others. Good luck.

---

