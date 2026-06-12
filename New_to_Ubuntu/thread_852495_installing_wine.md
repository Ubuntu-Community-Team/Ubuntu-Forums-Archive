---
title: "installing wine"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by carrarin on 2008-07-07
i seem to be having problems with instlling wine. 
Ths is a clean install of Ubuntu 8.04 Hardy, and I dont't have internet hooked up to the computer.

i tried ./tools/installwine

someone told me i have to get buil dependancies, i looked in the wine website and found out how to do this, but i don't have the internet, so i have no idea how to do this on my linux machine

---

### Post by carrarin on 2008-07-07
do all i have to do is type

sudo apt-get install build-essentials 
sudo apt-get build-dep wine

---

### Post by jamesrfla on 2008-07-07
You have to download wine off the internet.

---

### Post by carrarin on 2008-07-07
did that onto my flash and im at the library so if someone could tell me soon whether or not i can do this with out the internet that would be create.

---

### Post by RequinB4 on 2008-07-07
Ignore everything that you heard... that's assuming you want to compile the entire program, which from your experience you probably don't want to do.

If you have i386 -- [http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb)

If you have amd --
[http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_amd64.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_amd64.deb)

If you have lpia --
[http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_lpia.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_lpia.deb)

Transfer to your computer via your flash drive, double click and install.

---

### Post by Xerp on 2008-07-07
There is no need to compile anything. Simply add the wine repositories to Synaptic and install - takes just a few seconds!

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by carrarin on 2008-07-08
i downloaded **[http://wine.budgetdedicated.com/arch...04-1_amd64.deb](http://wine.budgetdedicated.com/arch...04-1_amd64.deb)**

so, all i have to do is dclick. Then to install wine. do i go into the terminal go to the directory that wine is, and type 
./tools/installwine

---

### Post by deNoobius on 2008-07-08
> **Xerp said:**
> There is no need to compile anything. Simply add the wine repositories to Synaptic and install - takes just a few seconds!

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

The OP doesn't have Internet, though--don't you need Internet access to add new repositories?

---

### Post by carrarin on 2008-07-08
yeah i cant add depositories from my flash, i tried :(

---

### Post by deNoobius on 2008-07-08
OK, here are some instructions I found for installing software manually.  Maybe this will help.

[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

---

### Post by carrarin on 2008-07-08
i had tried this once before( in fact more than once )
every time i try 
sudo apt-get install [prgogram name] 
i get an error saying something like 

checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

do i need to dload make-install from synaptic, does that come in a .deb package.

---

### Post by deNoobius on 2008-07-08
It definitely looks like you need some additional packages.  Can you get this computer on which you're trying to install Wine to an Internet connection?  Synaptic would resolve all those issues for you.

---

### Post by aktiwers on 2008-07-08
What do you need wine for? Its always better to find a native alternative.

Wine-Doors and Playonlinux are something that might make your life easier if you really need to install Windows apps on Ubuntu

---

### Post by carrarin on 2008-07-08
what do i need wine for...?
try video games that aren't native to linux

on an unrelated note, what packages would i need, and are they in .deb format

---

### Post by aktiwers on 2008-07-08
Grab the Ubuntu package:
[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by deNoobius on 2008-07-08
> **carrarin said:**
> what do i need wine for...?
try video games that aren't native to linux

on an unrelated note, what packages would i need, and are they in .deb format

If you're using Ubuntu, you need to find packages that work with Ubuntu.  Many .deb packages will, but not all.

Well, the message you get indicates that gcc is needed, which is a C compiler.  Build-essential, if you don't already have it, will be necessary also.

However, you might install those and still find that Wine needs further packages.

---

### Post by carrarin on 2008-07-08
yeah, dont have the internet so i have no idea how to do that. 
it looks like they want us to do that over the terminal

---

### Post by deNoobius on 2008-07-08
Honestly, it might be easier to ask a friend or neighbor if you can borrow their internet connection and just use Synaptic than to try to compile Wine.  Wine is in the Ubuntu repositories and it's just a snap.

---

### Post by carrarin on 2008-07-08
:lolflag: i can just see myself throwing the tower in a wheelbarrel and marching it acoss town. :lol:

or stapping it across my back like a hobo.

---

### Post by deNoobius on 2008-07-08
Well, all I can suggest then is while you're at a  computer with a connection, download the Ubuntu Wine package from the URL that Aktiwers gave you, also get build-essential.  Go back to your computer, install build-essential, then if that goes OK, install the Wine package.  If you get messages saying that other packages are needed, write them down and get them when you go back to a computer that's connected.  Install them and try again, etc.

---

### Post by deNoobius on 2008-07-08
Also, build-essential depends on other packages, which are listed here:

[http://packages.ubuntu.com/hardy/build-essential](http://packages.ubuntu.com/hardy/build-essential)

---

### Post by carrarin on 2008-07-08
what if we don't have an amd64 and what if we dont have an intell. it seems like its the only two options they give

---

### Post by aktiwers on 2008-07-08
You dont need built-essential for installing a deb.
If your CPU is 32bit, or if you at least installed the 32bit, then go with the Intel 32bit one.

---

### Post by stchman on 2008-07-08
> **carrarin said:**
> i seem to be having problems with instlling wine. 
Ths is a clean install of Ubuntu 8.04 Hardy, and I dont't have internet hooked up to the computer.

i tried ./tools/installwine

someone told me i have to get buil dependancies, i looked in the wine website and found out how to do this, but i don't have the internet, so i have no idea how to do this on my linux machine

WINE is in the Hardy Universe repos.

```
sudo apt-get install wine
```

That is it.

---

### Post by deNoobius on 2008-07-08
> **stchman said:**
> WINE is in the Hardy Universe repos.

```
sudo apt-get install wine
```

That is it.

You have to read the whole thread.  The OP is trying to install Wine on a computer that doesn't have Internet access.

---

### Post by stchman on 2008-07-08
My bad.

You will have to somehow go to a PC that has internet access and download the WINE .deb from packages.ubuntu.com and all of WINE's dependencies.

[http://packages.ubuntu.com/hardy/wine](http://packages.ubuntu.com/hardy/wine)

You will need to see if you have all the dependencies already installed.

---

### Post by carrarin on 2008-07-08
it seems like in order to dload that you need to have unix, would ineed to use a live cd to dload the files.

---

### Post by stchman on 2008-07-08
> **carrarin said:**
> it seems like in order to dload that you need to have unix, would ineed to use a live cd to dload the files.

No go to the bottom of the page and there are links for 32 and 64 bit downloads.

---

