---
title: "apt-get huh?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by carrarin on 2008-08-26
How does apt-get work?

---

### Post by halitech on 2008-08-26
apt-get is the method that is used to tell the system to install (and download from the repo if needed) software. It can also work in reverse to remove a program

ie. sudo apt-get install build-essential

tells the system to download and install the files associated with build-essential

sudo apt-get remove amsn

will tell the system to remove amsn from the computer

---

### Post by jerome1232 on 2008-08-26
Also if you ever want to know more about a program or command try looking at it's man page, can be kinda cryptic at times but does provide insight

```
man apt-get
```

---

### Post by jgrabham on 2008-08-26
simple, launch a terminal (applications > accessories > terminal)

then type

```
sudo apt get install 'application name' 
``` to install something
```
sudo apt-get remove 'application name'
``` to uninstall something
```
sudo apt-get upgrade
``` to upgrade everything

Thats a very simple version of how to use it, there are more complicated things you don't need to worry about right now.

You can also go Applications > add/remove and it's very simple, you type in what you're looking for, check or uncheck it, and click apply

hope this helps

---

### Post by carrarin on 2008-08-26
if have packs on a flash that i want to install 
do i just do the 
sudo apt-get pack.deb 

and the comp will find the pack on my flash and dload

---

### Post by -Zeus- on 2008-08-26
if you have downloaded a .deb, all you need to do to install it is double-click on it then press "install"

---

### Post by Michael.Godawski on 2008-08-26
It is not wrong to browse the help.ubuntu.com first :)
We are all willing to help but sometimes you will find great answers to frequently asked questions there:
for apt-get have a look here
[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto)

---

