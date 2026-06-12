---
title: "HOWTO: Expocity similar to Apple switch"
date: 2005-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by lizardking on 2005-01-13
I have found this deb package in the net to transform metacity simple task swithcer to a task switcher similar to Exposè di apple.
This si the software [EXPOCITY](http://www.pycage.de/software_expocity.html) .

I have found this debian package if some one would like to try it.
[Debian package for Expocity](http://acm2.ustc.edu.cn/~roger/debian/) 
**I invite the developer of Horthy to intall into it by deafult.** 
I have installed the package by **dpkg**  beacuse apt-get doen't work.
This is the result:
[click here to see](http://iack.altervista.org/expocity.jpg) 

**I have only a problem and if someone knows how to solve I'm glade with him. When I Go  to update package with synaptic I take an error to upgrade the system.The error is beacuse synaptic try to upgrade the library libmetacity0-exp that is the library of Expocity.So if I do this upgrade expocity go away :(. Some one have any solution?**

---

### Post by daniels on 2005-01-13
I had a look at it a while ago and made some packages for it that integrated better with Metacity, but no-one really liked the result.  We decided it wasn't good enough to go into Hoary, because it was just very frustrating.

---

### Post by woifi on 2005-01-13
hi!
[QUOTE=lizardking]
**I have only a problem and if someone knows how to solve I'm glade with him. When I Go  to update package with synaptic I take an error to upgrade the system.The error is beacuse synaptic try to upgrade the library libmetacity0-exp that is the library of Expocity.So if I do this upgrade expocity go away :(. Some one have any solution?**[/QUOTE]

what about ```
apt-get hold libmetacity0-exp
```

hth

woifi

edit:

expocity installation with apt-get should work with ```
deb http://acm2.ustc.edu.cn/~roger/debian/ ./
``` in your sources.list
btw, i see that the metacity version in this archive ist just **2.6.2** -> warty is **2.8.x**
do you have any problems? does anything not work?

---

### Post by lizardking on 2005-01-13
[QUOTE=woifi]

expocity installation with should work with ```
deb http://acm2.ustc.edu.cn/~roger/debian/ ./
``` in your sources.list
btw, i see that the metacity version in this archive ist just **2.6.2** -> warty is **2.8.x**
do you have any problems? does anything not work?[/QUOTE]

I have already tryed to edit source.lst am nothing.There is a bad package.gz in the server I think.

The apt-get hold commando report this:
```
sudo apt-get hold limetacity0-exp
E: Operazione non valida hold
``` 
no i have no problem when metacity runs, **only problem is with I cannot make update of the system leaving libmetacity0-exp**

---

### Post by woifi on 2005-01-14
[QUOTE=lizardking]I have already tryed to edit source.lst am nothing.There is a bad package.gz in the server I think.[/QUOTE]
package.gz seems to be ok, i'll check this...

> 
The apt-get hold commando report this:
```
sudo apt-get hold limetacity0-exp
E: Operazione non valida hold
``` 

oh, i thought there was an apt-get hold command ... sorry for this!
this command should do it for you: ```
echo libmetacity0-exp hold | dpkg --set-selections
```

alternatively you can do this with synaptic or dselect too, i think: "= key" in dselect or crtl+e in synaptic, iirc

hth

woifi

---

### Post by Gymnae on 2005-02-14
[QUOTE=lizardking]I have found this deb package in the net to transform metacity simple task swithcer to a task switcher similar to Exposè di apple.
This si the software [EXPOCITY](http://www.pycage.de/software_expocity.html) .

I have found this debian package if some one would like to try it.
[Debian package for Expocity](http://acm2.ustc.edu.cn/~roger/debian/) 
**I invite the developer of Horthy to intall into it by deafult.** 
I have installed the package by **dpkg**  beacuse apt-get doen't work.
This is the result:
[click here to see](http://iack.altervista.org/expocity.jpg) 

**I have only a problem and if someone knows how to solve I'm glade with him. When I Go  to update package with synaptic I take an error to upgrade the system.The error is beacuse synaptic try to upgrade the library libmetacity0-exp that is the library of Expocity.So if I do this upgrade expocity go away :(. Some one have any solution?**[/QUOTE]
 Wow, your Desktop looks great!
What themes or extra Tools did you use in Order to make Nautilus look like Finder, get the theme and have a Dock?
I wanna make my Ubuntu (did I mention that I'm new to this Community and love Ubuntu?) look like my OS X.

I'll try to install Expocity in Hoary during the next days!

---

### Post by piedamaro on 2005-02-14
[QUOTE=daniels]I had a look at it a while ago and made some packages for it that integrated better with Metacity, but no-one really liked the result.  We decided it wasn't good enough to go into Hoary, because it was just very frustrating.[/QUOTE]
 Totally agree. Unfortunately it's only a hack, ligth years far from exposeé. And as you said it's frustrating cause the windows pop up from nowhere, thus you loose track of the windows, then the whole thing is just useless.

---

### Post by dracnor on 2005-02-14
There is also skippy - [http://thegraveyard.org/skippy.php](http://thegraveyard.org/skippy.php) .  I just compiled the program by hand and it works well.  Just hit F11 after running the program to switch tasks/programs.  

1. download skippy
2. extract it - "tar xjvf skippy-0.5.0.tar.bz2"
3. change directories - "cd skippy-0.5.0"
3b. Optional - you can edit Makefile (nano Makefile) and comment out the Xinerama stuff.
4. build the program - type "make"
5. install it - "sudo make install"
6. "cp skippyrc-default ~/.skippyrc" (edit ~/.skippyrc to your preferences if you want) 
7. run skippy and hit F11

Works great here.  :-)

---

### Post by kamstrup on 2005-02-15
Isn't it painfully slow? For me it is at least...

---

### Post by Happy on 2005-03-31
Just installed Skippy.
It look nice but yes it is kinda painfully slow

but it looks nice =P

---

### Post by mstralka on 2005-05-09
I compiled and installed Expocity from the source.  It's cool, but not as cool as I thought, and it takes over ALT-TAB - How do I uninstall it?

EDIT - in the directory where I built it, do a make uninstall

---

### Post by Tamir on 2005-07-14
[QUOTE=mstralka]I compiled and installed Expocity from the source.  It's cool, but not as cool as I thought, and it takes over ALT-TAB - How do I uninstall it?

EDIT - in the directory where I built it, do a make uninstall[/QUOTE]
 Does somebody want me to do an amd64 package, or there is no need?

---

