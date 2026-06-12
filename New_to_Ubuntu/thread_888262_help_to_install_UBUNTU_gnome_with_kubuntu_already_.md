---
title: "help to install UBUNTU gnome with kubuntu already instld"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by rajaabiju on 2008-08-12
i have  live cds of both ubuntu and kubuntu

i have already installed kubuntu (64 bit version)in my laptop using the option install inside windows.,

i want to install ubuntu GNOME also...with live cd as i dont have internet connection.

---

### Post by bpowell2005 on 2008-08-12
> **rajaabiju said:**
> i have  live cds of both ubuntu and kubuntu

i have already installed kubuntu (64 bit version)in my laptop using the option install inside windows.,

i want to install ubuntu GNOME also...with live cd as i dont have internet connection.

You could put the Ubuntu CD in, select it in the aptitude repositories, then try "apt-get install ubuntu-desktop".

---

### Post by rajaabiju on 2008-08-12
i have 2 live cds of both ubuntu and kubuntu

i have already installed kubuntu (64 bit version)in my laptop using the option install inside windows.,

i want to install ubuntu GNOME also...with live cd as i dont have internet connection.[/QUOTE]

---

### Post by rajaabiju on 2008-08-13
i have 2 live cds of both ubuntu and kubuntu
 
 i have already installed kubuntu (64  bit version, i have amd 64 bit turion processor.)in my laptop using the option **install inside windows.,**
 
 i want to install ubuntu GNOME also...from live cd along kubuntu as i dont have internet connection.

---

### Post by loell on 2008-08-13
not sure about this but maybe you can make the ubuntu cd as a repo

in **System**--> **Software sources** 

you can add the ubuntu cd there


then just ```
sudo apt-get install ubuntu-desktop
```

afterwards..

---

### Post by mb_webguy on 2008-08-13
If you stick the Ubuntu LiveCD in your computer and set your sources to look on a CD, you should be able to install ubuntu-desktop from the CD using Synaptic.  Unfortunately, I don't think you can install *just* Gnome like this...

---

### Post by aysiu on 2008-08-13
It can't be done. The live CD does not contain all the packages necessary to *add* Gnome to KDE or vice versa. You need the **Alternate CD** instead of the *Desktop CD* (or live CD)... or an internet connection.

P.S. Please do not cross-post (same topic, multiple threads). I've merged your duplicate threads and deleted the duplicate posts. One thread per support request, please.

---

### Post by KWM987 on 2008-08-13
I may be a little unclear as to what exactly you are trying to accomplish, are you trying to have the gnome desktop available for developing or running applications? or are you trying to have a fully functioning version of Ubuntu to run alongside Kubuntu?

For the former you'll have to try and find internet somewhere it is byfar the easiest and fastest way to get what you need, perhaps a coffee shop or library that has wireless, or perhaps just temporarily move the cable from whatever machine you used to post, or have it share it's internet connection.  This is by far the easiest way to get the gnome, gnome-devel, etc.. packages off of synaptic for having access to gnome.  if it is a gnome program in kde, just download the program and it will install the dependent gnome packages automatically.

For the latter, you should be able to put the Ubuntu CD in and install it to its own partition along side Kubuntu, or also install it along side as a program in windows aswell.

---

