---
title: "ubuntu, gcc and cmake"
date: 2010-09-18
forum: Programming Talk
---

### Post by Jogidas on 2010-09-18
hi,

I'm absolutely beginner in ubuntu & linux world as I was pure windows guy so far. I recently installed latest ubutnu (i.e. v10) and gcc. I have no idea, where gcc installed by default. Now I was trying to install player/stage which is using cmake files for installation. But I'm keep getting error like this is not found and that's not found. Can anybody suggest some material on where (path) gcc is installed on ubuntu? Do I need to set any environment variables so that gcc can be launched from anywhere? And how about cmake?

Thanks..

---

### Post by Lateralis on 2010-09-18
Hi Jogidas.  Welcome to Ubuntu and the enlightened side! 

Firstly, I'm guessing that what you're trying to do is compile a programme from source code?  If you are, then what programme are you trying to compile?  There is a vast array of software packages and programmes in the Ubuntu software repositories which will cover just about all of your needs.  At the bottom of the applications menu you will see the Ubuntu Software Centre.  You can use that to install and remove programmes.  

If after looking through the software centre there is nothing that will do the job for you, post back saying what programme you're trying to compile, what steps you have taken so far you and precisely what error messages you are get.

---

### Post by The Cog on 2010-09-18
If you want to compile things, you probably want to install package build-essential, using the synaptic package manager, or this command:
> sudo apt-get install build-essential
This will install gcc lots of needed header files and stuff. Beyond that, I can't help you much because I'm not really hot on using gcc.

I'm moving this thread to Programming Talk where it really belongs and won't get buried so quickly either.

---

### Post by MadCow108 on 2010-09-18
if you mean this:
[http://playerstage.sourceforge.net/](http://playerstage.sourceforge.net/)

this software is packaged in ubuntu:
[http://packages.ubuntu.com/lucid/robot-player](http://packages.ubuntu.com/lucid/robot-player)
[http://packages.ubuntu.com/lucid/stage](http://packages.ubuntu.com/lucid/stage)

sudo apt-get install robot-player robot-player-dev stage

if you want to compile yourself it is easiest to get the build dependencies from the packet:
sudo apt-get build-dep robot-player stage

cmake should find all needed programs automatically.

Packets (from the official repositories) mostly follow the standard file system hierarchy:
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)
/usr/bin and /usr/lib are the usual places for binaries/libraries installed from packets

---

### Post by Jogidas on 2010-09-20
> **MadCow108 said:**
> if you mean this:
[http://playerstage.sourceforge.net/](http://playerstage.sourceforge.net/)

this software is packaged in ubuntu:
[http://packages.ubuntu.com/lucid/robot-player](http://packages.ubuntu.com/lucid/robot-player)
[http://packages.ubuntu.com/lucid/stage](http://packages.ubuntu.com/lucid/stage)

sudo apt-get install robot-player robot-player-dev stage

if you want to compile yourself it is easiest to get the build dependencies from the packet:
sudo apt-get build-dep robot-player stage

cmake should find all needed programs automatically.

Packets (from the official repositories) mostly follow the standard file system hierarchy:
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)
/usr/bin and /usr/lib are the usual places for binaries/libraries installed from packets


Thanks mate. You correctly picked up my nerve. Yes, I was after playerstage package. I did successfully installed on my ubuntu as you suggested using the sudo. 
Not sure, where binaries goes as I'm too new for ubuntu. How do I start them?

Thanks again for your great great help..

---

### Post by Jogidas on 2010-09-20
Thanks [Lateralis]("http://ubuntuforums.org/member.php?u=481237") and The Cog for taking time to explain. Executing build essential did helped a bit, but not much.. However reply from MadCow108 is more meaning in my particular case.

---

### Post by ssam on 2010-09-20
> **Jogidas said:**
> 
Not sure, where binaries goes as I'm too new for ubuntu. How do I start them?


the executables/binaries generally go in /usr/bin see [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

you can usually start them just by typing their name in a terminal. this is because /usr/bin is included in the default path [http://en.wikipedia.org/wiki/PATH_%28variable%29](http://en.wikipedia.org/wiki/PATH_%28variable%29) though graphical applications usually are automatically added to the applications menu.

---

### Post by Jogidas on 2010-09-21
Hi MadCow108,

I ran "sudo apt-get install robot-player robot-player-dev stage". It did ran for a while and it was successful. But no player folder is created in /usr/bin or /usr/local/share folder. What could have gone wrong?

---

### Post by dwhitney67 on 2010-09-21
Try using the "locate" utility:
```

locate robot-player

```

---

### Post by MadCow108 on 2010-09-21
no folder gets created in /usr/bin, just the executables get placed in /usr/bin

here's a list of files the package installs:
[http://packages.ubuntu.com/lucid/amd64/robot-player/filelist](http://packages.ubuntu.com/lucid/amd64/robot-player/filelist)

---

### Post by Jogidas on 2010-09-22
sorry to annoy you further.. As I said earlier, I'm really beginner...

I still can't run the executable. I tried executing every robot-player  file in usr/bin, but I could not able to start the player.. What should I enter on command line to launch the stage..

---

### Post by shawnhcorey on 2010-09-22
> **The Cog said:**
> If you want to compile things, you probably want to install package build-essential, using the synaptic package manager...

You should also install the documentation that goes with this:
```
sudo apt-get install manpages-dev
```

---

