---
title: "HOWTO: Install AssaultCube in Ubuntu Jaunty 9.04"
date: 2009-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by ALIENDUDE5300 on 2009-05-10
Hello, in this tutorial I'll explain how to set up the necessary dependencies in order to run the game "AssaultCube" in Ubuntu Jaunty 9.04. This is the first tutorial I've ever written for the Ubuntu community, so if you notice that I'm missing anything, please say so and I'll try to correct it. Also, I'm assuming that you already have your ATI/NVidia graphics card drivers set-up. I'm running this using the Open Source ATI drivers included in Ubuntu 9.04 with no problems.

Anyways, first we'll have to download assault cube. Either go to [the official website]("http://assault.cubers.net/"), or open up a terminal and run the following command to download the program:
```
wget http://downloads.sourceforge.net/actiongame/AssaultCube_v1.0.2.tar.bz2
```

Now we need to extract this file... in the Terminal, browse to the directory you downloaded the file to and run the following command:
```
tar xjvf AssaultCube_v1.0.2.tar.bz2
```

This will extract all the files in the archive to the AssaultCube_v1.0.2 directory. To change to this directory, type:
```
cd AssaultCube_v1.0.2
```

Before we can run AssaultCube, we need to install the dependencies. In the terminal, type:
```
sudo apt-get install libsdl1.2-all libsdl-image1.2 libsdl-image1.2-dev libopenal-dev
```

Everything should be set-up now. To run AssaultCube, simply type ./assaultcube.sh or double click the icon in the AssaultCube directory.

Enjoy!

---

### Post by G00D_GUY on 2009-06-06
This is all new for me. Will this work if I have Nvidia?

---

### Post by murali231 on 2009-07-08
thnx for the tutorial....i really needed this game!

---

### Post by markman1 on 2009-09-13
ok here is what you do.
 
go to [http://www.playdeb.net/updates/assaultcube](http://www.playdeb.net/updates/assaultcube)
 
and download here is worked for me.
 
also let me know if it workx for you as well.

---

### Post by nooblot on 2009-10-09
> **markman1 said:**
> ok here is what you do.
 
go to [http://www.playdeb.net/updates/assaultcube](http://www.playdeb.net/updates/assaultcube)
 
and download here is worked for me.
 
also let me know if it workx for you as well.

fishy
oh and this is your cherry post

---

### Post by amofhm on 2009-10-27
Everything's good till I type in : 
" sudo apt-get install libsdl1.2-all libsdl-image1.2 libsdl-image1.2-dev libopenal-dev " 
and it says :
" Package libsdl1.2-all is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replaceit:
  libsdl1.2debian-alsa
E: Package libsdl1.2-all has no install"

What must I do please??

---

### Post by Frutol on 2009-10-27
> **amofhm said:**
> Everything's good till I type in : 
" sudo apt-get install libsdl1.2-all libsdl-image1.2 libsdl-image1.2-dev libopenal-dev " 
and it says :
" Package libsdl1.2-all is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replaceit:
  libsdl1.2debian-alsa
E: Package libsdl1.2-all has no install"

What must I do please??

maybe "" sudo apt-get install libsdl1.2debian-alsa libsdl-image1.2 libsdl-image1.2-dev libopenal-dev ""  ???

---

### Post by phreakphish on 2010-06-05
> **markman1 said:**
> ok here is what you do.
 
go to [http://www.playdeb.net/updates/assaultcube](http://www.playdeb.net/updates/assaultcube)
 
and download here is worked for me.
 
also let me know if it workx for you as well.

This link either does not work or is taking way longer than I intend to wait. Anywho. Can anyone explain how to compile/install this from start to finish. I'm a noob still. I've gotten as far as extracting the .tar.bz2

Cheers

---

### Post by Rusty Eagle on 2011-04-10
Finally a good installation guide.:D  I'm new to Linux and Ubuntu and this helped me a lot. thanks! These instuctions also apply to the newer version of assault cube. Just change the filenames in the console.

---

