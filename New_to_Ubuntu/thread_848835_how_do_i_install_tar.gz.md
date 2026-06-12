---
title: "how do i install tar.gz"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-07-03
okay i have had my ubuntu for about 3 months now but i cant install tar.gz files...i know you have to make new directories and everything but i just dont get it...(im trying to install flock just for practice)
plz help

---

### Post by skylinedna on 2008-07-03
Here is a really good guide for anything ubuntu mate  [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)     go hard :)

---

### Post by iaculallad on 2008-07-03
Follow up with this [link]("http://monkeyblog.org/ubuntu/installing/"). It shows how you can install anything in Ubuntu.

---

### Post by Mythology on 2008-07-15
I too am having problems. Those sites aren't making much sense to me. Like "enabling other repositories"... the screen looks different for me. and when I enter those things in the terminal I don't get the same outcome they speak of.

I too am trying to install FLock. Normally I just find things through the add/remove program but Flock isn't there.

---

### Post by oldos2er on 2008-07-15
I'm fairly sure the Flock package contains precompiled binaries, so you would only need to extract the files, then double-click Flock.

---

### Post by fenian on 2008-07-16
This file is a little different than most as it doesnt need to be built or run an installer.To use flock...

Download Flock to your home folder and extract (right click choose extract here).A folder named flock will appear in your home directory,inside this folder is a file named flock,right click this file and choose open a dialog box will open choose run and flock should run.

You can add flock to your Applications menu by doing this...
Right click the Applications menu
choose edit menus
Go to Internet
Click the new item tab
In the name field put flock
in the command field put  /home/username/flock   (replace username with your username)
now you can start flock from Applications>Internet>flock

---

### Post by JeffoOfMetal on 2008-07-16
Go to System>Administration and select Synaptic Package Manager. Search "build essential" and install it.

Then, when you have the tar.gz, or as some may call it, the tarball, right-click it and select "Extract Here."

Go to Applications>Accessories>Terminal. Then, type in:
```
ls
cd Desktop
ls
cd <name of new folder>
./configure
make
sudo make install
make clean
```

Make sure you only input one line at a time.

---

