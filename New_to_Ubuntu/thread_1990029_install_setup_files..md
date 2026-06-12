---
title: "install setup files."
date: 2012-05-29
forum: New to Ubuntu
---

### Post by mpallwa on 2012-05-29
How do you install setup file programs. In windows, you simply double click and press next,next and so on. Can this be done on linux kubuntu or programs are solely installed from the tar.gz internet?

---

### Post by kc1di on 2012-05-29
> **mpallwa said:**
> How do you install setup file programs. In windows, you simply double click and press next,next and so on. Can this be done on linux kubuntu or programs are solely installed from the tar.gz internet?

In most linux distrobution you use there package manager to do the installation. 

in Kubuntu I believe it's Mouon or somthing similar.  You can also install them from the command line (Terminal) by using the following syntax:

```
sudo apt-get (filename)
``` Without the ()

---

### Post by mastablasta on 2012-05-29
> **mpallwa said:**
> How do you install setup file programs. In windows, you simply double click and press next,next and so on. Can this be done on linux kubuntu or programs are solely installed from the tar.gz internet?
 
 
they are installed from package manager (in Kubuntu that is Muon which also has a cleaner software center version) which connects to repositories and isntall form there. repositories are secure colleciton of programmes (no viruses there ;)).
 
in command line it is actually
 
sudo apt-get install *programmename*
 
apt-get is a a commandline tool for the package manager. you are always asked for your user password (in command line you won't see anything typed - security feature, so just type it in and press enter). passwords are users approval for install. computer that way knwos that user initiated install not malware.
 
another option is PPA which is adding a personal package archive (basically a personal repository). not as safe as official repositories, but if you trust the source you can add the personal repository.
 
windows has .exe files Ubuntu linux uses .deb files that work in similar way.
 
.sh and .run files are similar to .bat files in windows
 
and finaly tar.gz. files. tar.gz. is actually like a zip file. sometimes they are just extracted and run, while sometimes they have source code in which case you need to compile it. instructions for this and command lines (that you can copy&paste to terminal) can be found wihtin tar.gz. file (usually called install.txt or similar).
 
now if you want to install a windows *setup.exe* file in linux that might be a bit more difficult. you can use Wine where you just run it like in windows. and if it's compatible it will get installed and shortcut to it will be made. you can also try play on linux which is a GUI for wine with some presets for plenty commonly used programmes. to make the install easier. and final option is Crossover which is very good and user friendly implementation of wine, but you would need to pay a small amount for it. however apparently it is worth it if you are uncomfortable with doing special wine setups and command lines.

---

### Post by PeterP24 on 2012-05-29
in addition to what @mastablasta said: if you downloaded the tarball, then you should check the website for that program, or even the tarball for an INSTALL or README file. Usually their are very clear in the steps you have to take in order to install the program - and they warn you if you need other programs or libraries required for the current program to work. It isn't much more complicated as on Windows - you just have to spend 5 minutes in order to search for install instructions and to read them. 
The .deb files are very nice and convenient, but if you love to have the latest version of the program you should go for the tarball from the developer website.

---

