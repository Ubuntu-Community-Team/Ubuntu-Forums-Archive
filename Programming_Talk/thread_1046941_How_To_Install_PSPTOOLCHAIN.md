---
title: "How To: Install PSPTOOLCHAIN"
date: 2009-01-21
forum: Programming Talk
---

### Post by InSaN3 GoDLiK3 on 2009-01-21
This is a installation Tutorial about how to install psptoolchain 
you will need to install: 

build-essential, autoconf, automake, bison, flex, libncurses5-dev, libreadline-dev, libusb-dev, texinfo, libmpfr-dev,
 libgmp3-dev   

if you dont know how to install open termianl and type 
sudo apt-install then type one of those names

First off -- go to your home/username folder <(username)> = your ubuntu login name...so anyways go to your home/username folder and you should see folders like Desktop, Documents, Examples, etc  now press ctrl + H (this shows your hidden folders) now scroll down and find a txt folder called .bashrc and open that up and paste these at the bottom of the text file

export PSPDEV="/usr/local/pspdev"
export PSPSDK="$PSPDEV/psp/sdk"
export PATH="$PATH:$PSPDEV/bin:$PSPSDK/bin"

Then save that and exit text editor now back to your username folder press ctrl + H to hide your hidden folders now open Synaptic Package Manager System - Administration - Synaptic Package Manager now search for libgmp3-dev and install that now open your terminal 
Applications - Accessories - Terminal and type this or paste 


```
svn checkout svn://svn.ps2dev.org/psp/trunk/psptoolchain
```

Now this folder should be in your home/username folder called psptoolchain
now type this in terminal

```
cd /home/YOUR USER NAME GOES HERE/psptoolchain
```

Now in terminal again type this 

```
sudo ./toolchain-sudo.sh
```

now if you get and error to install something then go to your Synaptic Package Manager and search for it.....and now the find begins psptoolchain will install and it will take an hour or so. So just it back and eat some popcorn:popcorn:  

when your done hopefully no error then congrats you have psptoolchain ;)


**************************************************************************
                SOME INFO ABOUT PSPTOOLCHAIN

This program will automatically build and install a compiler and other
  tools used in the creation of homebrew software for the Sony Playstation
  Portable handheld videogame system.

**************************************************************************

---

