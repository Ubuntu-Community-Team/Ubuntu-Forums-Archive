---
title: "HOWTO : DBoxFE [A GUI for Dosbox]."
date: 2009-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by ashmew2 on 2009-04-15
Hi,

To install [_DBoxFE_]("http://chmaster.freeforge.net/dboxfe-project.htm") . which is a GUI for [_Dosbox_]("http://dosbox.com/") , We need : 

Dosbox and Development Library of Qt4 and files needed for compiling.

To do that , simply put in the terminal : 

```
sudo apt-get install dosbox libqt4-dev build-essential
```

Now , we need to download the source file for DBoxFE , because its not available in a packaged Binary for each Distro.To do that , simply click here : [http://prdownload.berlios.de/dboxfe/dboxfe-0.1.3.tar.bz2](http://prdownload.berlios.de/dboxfe/dboxfe-0.1.3.tar.bz2)

And select a mirror to download it.

Save the dboxfe-0.1.3.tar.bz2 to your Desktop.

Next , Open up a terminal
[And enter the commands , one line at a time pressing enter after each] :

```
mkdir ~/.dboxfe
cd ~/.dboxfe
tar -xvf ~/Desktop/dboxfe-0.1.3.tar.bz2 
cd dboxfe-0.1.3/
./configure
make -f Makefile
cd dboxfetray/
make -f Makefile
```

It's installed , now to make a launcher for DBoxFe :
```

cd ~/Desktop
ln ~/.dboxfe/dboxfe-0.1.3/bin/dboxfe DBoxFE
```

Now You have an icon on the Desktop , which you can right click to open up DBoxFE.

Just post back if you need some help with this! :D
Cheers.

---

### Post by 5h4dy on 2011-06-01
I keep getting the error make "Makefile" no such file or directory?

---

