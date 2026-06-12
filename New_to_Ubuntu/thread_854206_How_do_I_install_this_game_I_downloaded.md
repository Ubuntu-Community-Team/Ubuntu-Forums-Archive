---
title: "How do I install this game I downloaded?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by VargasTheBlind on 2008-07-09
I downloaded a game for Linux, Narcissu ([http://narcissu.insani.org/down.html](http://narcissu.insani.org/down.html)). It's a tarball and I don't know how to install it, do I have to do the whole ./configure, make install thing or is there a simpler way (like dragging and dropping theme .tars in Appearance)? I would love to learn compiling and things like that down the road, but I'm still pretty new to Ubuntu and I don't want to bite off more than I can chew just yet.

Thanks,
Vargas

---

### Post by appi2012 on 2008-07-09
With installing tars, just look inside for a README file or INSTALL file. These tell you what commands to run. You have to run these commands from inside the folder in which all the files are. type in a terminal:
```
cd pathtothefolder(/home/blah/game for example)
```
Normally, once you are in the folder you run:
```
./configure
```
```
make
```
```
sudo make install
```

Its much easier to install programs from Applications -> Add/Remove, but unfortunately, the ubuntu repositories don't have every single piece of software. 

If the game website has directions for adding a repository for your game, then do that and type in a terminal:
```
sudo apt-get install nameofapp
```

or, if the website offers a .deb file, just open it, and click install.

---

### Post by Elfy on 2008-07-09
There is none of that in the download, I was intrigued :)

Extract the file then run the onscripter, you can right click and choose extract here

I extracted to my desktop so
```
cd Desktop
cd narcissu_web_edition
./onscripter
```

It opens in a window

---

### Post by Cypher on 2008-07-09
The tarball contains the game binaries, not code that you would compile. So from the file manager you can choose to "extract" the tarball and see what's in there. You might find a README or INSTALL or some other documentation about starting the game..

From the command line you would do
```

tar -ztvf <file/name>.tar.gz

```
If the file ends in a tar.bz2 ending, then change the "z" in the above command to "j".."tar -jxvf"..

---

### Post by Xerp on 2008-07-09
Its a binary. You just download it, unpack it and then run it :)

---

### Post by VargasTheBlind on 2008-07-09
Thank you all, I'll unpack it and see if it works.

---

### Post by VargasTheBlind on 2008-07-09
I unpacked it, and ./configure didn't work so I just ran the Onscripter, which seems to be the launcher. The game runs, but the window it runs in is unmaximisable, almost completely transparent and the audio is choppy.

---

### Post by Elfy on 2008-07-09
It ran ok for me - although it didn't appear to be a game.

---

### Post by VargasTheBlind on 2008-07-09
Exactly, which is why I got fed up with the thing and just deleted it. Thank you all for your help just the same.

---

