---
title: "Questions regarding Installing Programs in Linux."
date: 2009-01-12
forum: Philippine Team
---

### Post by SHENGTON on 2009-01-12
Hi experts, good day. :)

**I have few questions regarding installing:**
1. Why is that in Linux if we install a program we need to use a command?
2. Is Linux can't make a program which is already compiled and we just run the program to install it just like in Windows?

I'll be waiting for your answers guys.

Take care and God bless. :)

---

### Post by kgas on 2009-01-12
For ubuntu there are many deb files available for eg check this site
[http://www.getdeb.net/](http://www.getdeb.net/) . The next one you should forget is Linux is not windows. [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by loell on 2009-01-12
1. You don't have to install from the command line, there are graphical front ends like synaptic, ubuntu's **Add/remove**(gnome-app install), double clicking a deb  file will even prompt you a message box  if you would like to proceed installing it or not.  

you may have the impression that everything can only be installed from the command line, and its true many tutorials do that, primarily because downloading/installing programs from command line is very efficient.


2. for the sake of simplicity, there are deb files like the previous post mentioned, its the equivalent for program installers in windows. there are variations, but you only have to know debs for now, to know more.. further read on about [package management]("http://en.wikipedia.org/wiki/Package_management_system").

---

### Post by SHENGTON on 2009-01-13
Thanks for your inputs Sir kgas and loell. I got a questions with this:

> primarily because downloading/installing programs from command line is very efficient.
Why Sir? What makes very efficient?

---

### Post by loell on 2009-01-13
> **SHENGTON said:**
> 
Why Sir? What makes very efficient?

just compare the time.. ;) granted you like to try thousands of programs in the repo.

you just type,

**sudo apt-get install *program name*** 

compare that when you install from synaptic or app-install.

though one could argue,  what is 10 seconds faster? :D in the end, it's an individual choice. if you want installing things from GUI then go GUI.

---

### Post by pinoyskull on 2009-01-14
> **SHENGTON said:**
>  
Why Sir? What makes very efficient?
IMHO, it is much faster to do thing in the command line than in GUI ;)

---

### Post by pendletone on 2009-01-14
> **loell said:**
> just compare the time.. ;) granted you like to try thousands of programs in the repo.

you just type,

**sudo apt-get install *program name*** 

compare that when you install from synaptic or app-install.

though one could argue,  what is 10 seconds faster? :D in the end, it's an individual choice. if you want installing things from GUI then go GUI.

this is also especially true if you want to instruct or help someone to do a particular task that requires a multitude of steps if done the GUI way, as opposed to a line or two of code. it's much easier and faster to get your help across that way.

---

### Post by dannybuntu on 2009-01-19
Efficiency is key :)

---

### Post by konqueror7 on 2009-02-06
the good thing about installing application using CLI is that it can be configured to you preference compared to having to install it using GUI tools...

also about why installation in windows is different from linux...linux is a continuously developed operating system (pretty much every quarter/month there a new update), so this components are being developed by thousands of developers around the world coordination over the internet, each of these modules they develop is different, so its hard to keep them upon installation...compared to windows, it updated only through service packs and only few year after the new kernel. also most of those application modules are already installed in the system...

correct me if i'm wrong, but this how i see it...

---

### Post by adredz on 2009-02-06
> **pendletone said:**
> this is also especially true if you want to instruct or help someone to do a particular task that requires a multitude of steps if done the GUI way, as opposed to a line or two of code. it's much easier and faster to get your help across that way.

Tompak! You'd get crazy if you'd go the GUI way helping-wise..

---

### Post by dannybuntu on 2009-02-08
The commands are actually faster. In windows you double click the exe file. In Ubuntu and other Debian based distributions you just have to type

**sudo apt-get install *program name***

Type **your password**

Type **y**

O di ba ang saya? 

Sure ka pa na walang spyware o malware yung iniinstall mo. Sa windows, pag naginstall ka ng "freeware" karaniwan may mga malware at spyware. 

Dito walang ganun. Halos lahat ng kailangan mo meron na. 

Pati Yahoo Messenger malapit ng gumana! Sinubukan kong install yung Windows client ng Yahoo Messenger sa Wine 1.1.13 nag install (yun nga lang hindi maka login) At least malapit na! :)

Marami ng programang tumatakbo sa wine. Konting tiis na lang - keep filing those bug reports para maremedyohan na nila. Saka kung ikaw mayroong mai cocontribute in terms of code e di mas maganda :) 

Grabe in love na in love talaga ako sa ubuntu. Nababaliw na ako. :)

---

### Post by ysNoi on 2009-02-17
[QUOTE=dannybuntu;6702621
Grabe in love na in love talaga ako sa ubuntu. Nababaliw na ako. :)[/QUOTE]

Just keep on loving it bro...! :popcorn::popcorn:

---

### Post by Samhain13 on 2009-02-18
> **SHENGTON said:**
> Hi experts, good day. :)

**I have few questions regarding installing:**
1. Why is that in Linux if we install a program we need to use a command?
2. Is Linux can't make a program which is already compiled and we just run the program to install it just like in Windows?

I'll be waiting for your answers guys.

Take care and God bless. :)

1-2: In Ubuntu, get a .deb file. Double-click on it. Confirm your password. Click "OK". Same process (in the user's perspective) as installing an application using a .exe installer.

1: Not all applications need to be "installed". Some are run just by double-clicking a script that has executable permissions. For example: in Blender 3D 2.48a, you just download the package for Linux, unpack it to a directory, then simply double-click the "blender" script; no need to install, no need to go into CLI.

2: APT is one of those "universal installers". The difference between that and a Windows installer is: in Windows, each "complete application package" like say, Photoshop, comes with its own installer, but you can't use that same installer for installing, say Illustrator or VLC or SomeOtherWhatever; in Linux, you use an installer like APT to install over 9000 big and small application packages, whether they're related or not.

So we might as well turn the question around: can't there be just one pre-compiled program in Windows that installs most (if not all) application packages and dependencies, like in Linux? :D

---

